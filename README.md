#  Claude Code: The Sourcemap Leak Analysis

**Anthropic's Multi-Agent Orchestration Engine Disassembled**

On March 31, 2026, Anthropic published an update to their highly anticipated `claude-code` CLI. Due to an accidental `.map` inclusion during the Bun build process, the unminified, heavily commented TypeScript source code for the entire product was leaked via the npm registry.

Rather than just a simple CLI wrapper for an LLM text-generator, the source code revealed a highly experimental, multi-layered **Swarm Orchestrator** featuring background processing, memory garbage collection, corporate espionage safeguards (Undercover Mode), and even a Tamagotchi system.

This repository serves as an exhaustive, definitive teardown of the leaked architecture. 

---

##  The Deep Dives

Analyzed thousands of lines of the original TypeScript to produce three extensive, flowchart-rich technical teardowns. 

### 1. [The Architecture Deep Dive](./claude-code-architecture.md)
*Focuses on System Design, Prompt Caching, and Concurrency.*
* **Dead Code Elimination:** How Bun's `feature()` conditionally removes internal tooling (`Undercover Mode`) from public binaries.
* **The Swarm Coordinator:** How Claude utilizes exact-prefix prompt caching to fork local Worker agents to parallelize file reads in a shared `tengu_scratch` lock.
* **Asynchronous execution barriers:** How the Event Loop separates 60+ tools into Concurrent Reads and Serial Mutations over the Libuv thread pool.
* **The Permissions Race:** How the CLI eliminates I/O blocking by asynchronously racing `stdin` against a sub-15ms local YOLO Safety Classifier.

### 2. [The Memory & Reasoning Engine](./claude_code_memory.md)
*Focuses on Cognitive Load, State Persistence, and Garbage Collection.*
* **The 4-Tier Memory Taxonomy:** How memories are rigorously constrained into `User`, `Feedback`, `Project`, and `Reference` scopes.
* **The Extraction Subagent:** A breakdown of the background agent subjected to strict Turn Budgets to index memory passively.
* **The autoDream Loop:** The 3-gate triggered "sleep function" that scrubs memory for contradictions and converts relative dates.
* **ULTRAPLAN:** How localized swarms can yield to a 30-minute Cloud Container Runtime (CCR) for app-wide architectural migrations.

### 3. [The Claude Code Mastery Guide](./claude_code_mastery.md)
*Focuses on practical implementation to 10x your development workflow.*
* **Context Collapsing:** Why using `/compact` is vastly superior to clearing threads.
* **The CLAUDE.md Cascade:** How the system re-compiles the context boundary dynamically on *every single turn*.
* **YOLO Configuration:** Why you should turn Auto-Approve on for linting and formatting.

---

### Disclaimer
*This repository contains educational software architecture analysis. No proprietary keys, user data, or internal model weights are hosted here. Code snippets analyzed are referenced for educational teardown purposes derived from public package registries.*
