# The Memory & Reasoning Architecture of Claude Code

*March 31, 2026 | System Architecture & State Management*

One of the hardest problems in agentic software engineering is context persistence. How do you ensure an autonomous coding agent remembers technical constraints and user preferences across thousands of sessions without constantly polluting (and overflowing) its token context window? 

The leaked `.map` source code from Anthropic's Claude Code reveals a masterclass in autonomous memory allocation and cognitive reasoning loops. It separates transient "thinking" from durable "memory", backed by parallel background validation agents.

Here is exactly how Claude Code's memory and reasoning architecture actually works.

---

## 1. The Four-Tier Memory Taxonomy

If you dive into `memdir/memoryTypes.ts`, you’ll see that Claude Code strictly limits what it remembers to exactly four rigorously defined types. The prompt explicitly instructs the LLM *not* to save architecture, file paths, or git history—because these can be dynamically derived via `git log`/`grep` at runtime.

Memory is highly curated into four classes, further separated by **Private** vs **Team** scopes:

```mermaid
graph TD
    classDef memoryNode fill:#e1f5fe,stroke:#01579b,stroke-width:2px,color:#000000;
    classDef scopeNode fill:#fff3e0,stroke:#e65100,stroke-width:1px,color:#000000;
    classDef discardNode fill:#ffebee,stroke:#c62828,stroke-width:1px,color:#000000;

    Input[Agent Identifies Context Element] --> Filter{Derivable from Codebase?}
    
    Filter -->|Yes: Git History, File Paths| Discard[Discard Memory]
    Filter -->|No: Requires Persistence| Sort{Determine Memory Type}

    Sort --> M1([User])
    Sort --> M2([Feedback])
    Sort --> M3([Project])
    Sort --> M4([Reference])

    M1 -.-> S1{Always Private Scope}
    M2 -.-> S2{Bias Private Scope}
    M3 -.-> S3{Bias Team Scope}
    M4 -.-> S4{Usually Team Scope}

    S1 & S2 --> Private[~/.claude/MEMORY.md]
    S3 & S4 --> Team[./.claude/MEMORY.md]

    class Input,Sort,Filter memoryNode;
    class M1,M2,M3,M4 memoryNode;
    class S1,S2,S3,S4 scopeNode;
    class Private,Team scopeNode;
    class Discard discardNode;
```

1. **`user` (Always Private):** Tracks domain knowledge levels. (*e.g., "User is a data scientist, frame frontend concepts using backend analogies."*)
2. **`feedback` (Bias Private):** Tracks behavioral corrections and confirmations. The prompt specifically instructs Claude to record *confirmations of success* so that it doesn't "grow overly cautious" from only remembering negative corrections.
3. **`project` (Bias Team):** Tracks organizational contexts. (*e.g., "Merge freeze begins on 2026-03-05 for mobile release cut."*) The prompt strictly forces Claude to **convert relative dates ("next Thursday") to absolute dates** to prevent temporal drift.
4. **`reference` (Always Team):** Pointers to external systems. (*e.g., "Pipeline bugs are tracked in Linear under project INGEST."*)

### Formatting and Constraints
Memories are stored in `.md` files with Markdown frontmatter (name, description, type).
To prevent prompt-context explosion during normal sessions, the `MEMORY.md` index file is strictly regulated:
* Each entry must be exactly one line.
* Max length is ~150 characters.
* Hard-truncated at **200 lines** to save tokens.

---

## 2. Background Extraction Agents & Turn Budgets

Claude doesn't force the primary chat agent to manually handle filesystem memory mutations on the hot path (which would slow down the user's chat speed). 

Instead, checking `services/extractMemories/prompts.ts` reveals a dedicated **Memory Extraction Subagent**.

Every few turns, Claude Code forks the conversation and spawns a background agent with a severely restricted toolset (only `FileRead`, `FileEdit`, and read-only `Bash` commands like `ls`/`stat`). 
Because agents generate expensive reasoning steps, this subagent is forced onto a strict **Turn Budget**:

```mermaid
sequenceDiagram
    participant User
    participant ChatAgent as Primary Agent
    participant BgAgent as Subagent (Extraction)
    participant FS as File System
    
    User->>ChatAgent: Iterates through conversation tasks
    Note over ChatAgent: N turns passed since last memory write
    ChatAgent-->>BgAgent: Fork Transcript (Start Background Job)
    
    Note over BgAgent: Turn 1: Parallel Reads Only (Strict Budget)
    BgAgent->>FS: Request File A
    BgAgent->>FS: Request File B
    BgAgent->>FS: Request MEMORY.md
    
    Note over BgAgent: Turn 2: Parallel Writes Only (Strict Budget)
    BgAgent->>FS: Edit File A
    BgAgent->>FS: Write File C
    BgAgent->>FS: Update MEMORY.md
    
    BgAgent--xChatAgent: Terminate silently
```

---

## 3. The `autoDream` Consolidation Loop (Memory GC)

Memory rots over time as codebases evolve. Anthropic mitigates "stale memory hallucination" using a Garbage Collection subagent called **autoDream**.

Triggered transparently under a Three-Gate Lock (24-hour expiration, 5 active sessions tracked, DB exclusivity), the algorithm executes a four-phase memory scrub. 

```mermaid
graph TD
    classDef step fill:#dcedc8,stroke:#33691e,color:#000000;
    classDef trigger fill:#ffe0b2,stroke:#e65100,color:#000000;

    Start((Time passed <br/> >= 24h)) --> Check1{5 Sessions Passed?}
    Check1 -->|Yes| Lock{Acquire DB Exclusivity Lock}
    
    Lock -->|Lock Aquired| Phase1[Phase 1: Orient <br/> Scan MEMORY.md]
    Phase1 --> Phase2[Phase 2: Signal Hunt <br/> Parse Append-Only Logs]
    Phase2 --> Phase3[Phase 3: Consolidate <br/> Fix contradictions & relative dates]
    Phase3 --> Phase4[Phase 4: Prune <br/> Force sub-25KB payloads]
    
    Phase4 --> End(((Sleep Cycle Complete)))

    class Phase1,Phase2,Phase3,Phase4 step;
    class Start,Check1,Lock trigger;
```

To further safeguard against hallucinations, the prompt compiler injects a **`MEMORY_DRIFT_CAVEAT`**:
> *"Memory records can become stale over time... Before answering the user... verify that the memory is still correct and up-to-date by reading the current state of the files."*

---

## 4. Multi-Agent Reasoning & ULTRAPLAN

Claude Code's cognitive load isn't restricted to a single monolithic API call. It implements varying levels of computational effort depending on the task's complexity.

### Coordinator Mode Swarms
For complex refactoring, reasoning is explicitly decentralized. A **Coordinator** acts as the high-level system architect. It evaluates the prompt, draws up a spec layout, and parallelizes the actual coding tasks out to localized **Worker Agents**. 

These isolated workers execute tasks and write their outputs to a shared SQLite/Filesystem lock directory (`tengu_scratch`). The Coordinator then reads the scratchpad outputs to cross-verify that the implementation matches the original spec.

```mermaid
graph TD
    classDef parent fill:#ce93d8,stroke:#4a148c,color:#000000;
    classDef node fill:#e1f5fe,stroke:#01579b,color:#000000;
    classDef external fill:#ffccbc,stroke:#bf360c,color:#000000;

    TaskInput[Complex User Prompt] --> Analyzer{Difficulty Analyzer}

    Analyzer -->|Medium: Refactor| Coord[Local Coordinator Node]
    Analyzer -->|Extreme: App Migration| Ultra[ULTRAPLAN Protocol]

    %% Local Swarm
    Coord -->|Parallel Fork| W1[Worker Subagent 1]
    Coord -->|Parallel Fork| W2[Worker Subagent 2]
    Coord -->|Parallel Fork| W3[Worker Subagent n]
    
    W1 & W2 & W3 <--> Scratchpad[(tengu_scratch <br/> Shared Filesystem)]
    Scratchpad -.-> Coord

    %% Ultraplan Remote
    Ultra --> RemoteCCR[Anthropic Cloud Container Runtime <br/> Unreleased Opus 4.6 Model]
    RemoteCCR --> |30 mins max execution time| VisualUI[Web UI Approval Dashboard]
    VisualUI --> |Sentinel Tag: __ULTRAPLAN_TELEPORT_LOCAL__| Diffs[Blast Diffs to Local Dev Environment]

    class Analyzer node;
    class Coord parent;
    class W1,W2,W3 node;
    class Ultra,RemoteCCR,VisualUI external;
```

### ULTRAPLAN (The Heavy Compute Override)
For reasoning tasks that demand immense depth (e.g., full app migrations), the local Swarm is insufficient. 
Claude Code detects high-complexity tasks and bridges out to **ULTRAPLAN**. It fires a serialized task state payload to Anthropic's remote Cloud Container Runtimes (CCR). 

The CCR spins for up to 30 minutes, reasoning through deep multi-step trees, while the user watches a telemetry dashboard in their local browser. Upon user approval, the compiled architecture payload is "teleported" back into the CLI via a sentinel XML tag, converting 30 minutes of cloud-based reasoning directly into local filesystem diffs.

---

## Summary

Anthropic's approach to Agentic Memory is defined by paranoid prompt constraints and decoupled background validation. By limiting the primary loop's context window to a strictly pruned, 200-line index flag—and offloading the actual IO mutations to `autoDream` cycles and parallel Extraction Subagents—Claude Code manages to remember the user's intent indefinitely without ever suffocating its own context window.
