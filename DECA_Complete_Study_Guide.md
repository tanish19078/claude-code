# DECA Complete Study Guide — Units 2 & 3 (MCQ Ready)

---

# UNIT 2: DIGITAL ELECTRONICS

---

## 1. Signals & Digital Basics

| Term | Definition |
|------|-----------|
| **Signal** | Function representing variation of a physical quantity |
| **Analog Signal** | Amplitude can have **infinite** values at any point in time |
| **Digital Signal** | Amplitude has **finite and discrete** values |
| **Binary Signal** | Special case of digital signal with **two** discrete values |
| **Positive Logic** | Higher voltage = logic 1, Lower voltage = logic 0 (e.g., +5V=1, 0V=0) |
| **Negative Logic** | Lower voltage = logic 1, Higher voltage = logic 0 (e.g., 0V=1, +5V=0) |

### Digital Waveform Key Terms
- **Leading edge**: occurs first (t=0)
- **Trailing edge**: occurs last
- **Positive-going pulse**: LOW → HIGH → LOW (leading=rising, trailing=falling)
- **Negative-going pulse**: HIGH → LOW → HIGH (leading=falling, trailing=rising)
- **Periodic**: repeats at fixed interval (period T)
- **Frequency**: f = 1/T (measured in Hertz)
- **Duty Cycle** = (t_w / T) × 100% where t_w = pulse width

### Advantages of Digital Electronics
1. Processed & transmitted more efficiently and reliably
2. Simple and accurate (only HIGH/LOW)
3. Better storage (e.g., digital music)
4. Less affected by noise
5. Easier display to read
6. High degree of security
7. Small size due to ICs, very cheap

### Disadvantages
- Conversion to/from analog loses information
- Consumes more energy, produces more heat
- More expensive in small quantities

---

## 2. Number Systems

| System | Base/Radix | Digits |
|--------|-----------|--------|
| **Decimal** | 10 | 0-9 |
| **Binary** | 2 | 0, 1 |
| **Octal** | 8 | 0-7 |
| **Hexadecimal** | 16 | 0-9, A-F |

### Conversion Methods

| From → To | Method |
|-----------|--------|
| Decimal → Binary | Divide by 2, track remainders (read bottom to top) |
| Decimal → Octal | Divide by 8, track remainders |
| Decimal → Hex | Divide by 16, track remainders |
| Binary → Decimal | Multiply each bit by 2^n (n = position from right starting 0), add results |
| Binary → Octal | Group bits in **3** from right, convert each group |
| Binary → Hex | Group bits in **4** from right, convert each group |
| Octal → Binary | Each octal digit → 3-bit binary |
| Octal → Decimal | Multiply each digit by 8^n, add results |
| Octal → Hex | Convert to binary first, then group by 4 |
| Hex → Decimal | Multiply each digit by 16^n, add results |
| Hex → Binary | Each hex digit → 4-bit binary |
| Hex → Octal | Convert to binary first, then group by 3 |

### Data Units
| Unit | Size |
|------|------|
| 1 Bit | 0 or 1 |
| 1 Nibble | 4 bits |
| 1 Byte | 8 bits |
| 1 Half-word | 16 bits |
| 1 Word | 32 bits |
| 1 Double Word | 64 bits |

---

## 3. Binary Arithmetic

### Addition Rules
| A | B | Sum | Carry |
|---|---|-----|-------|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | **1** |

### Subtraction Rules
| A | B | Diff | Borrow |
|---|---|------|--------|
| 0 | 0 | 0 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | **1** |

### Multiplication Rules
- 1×1=1, 1×0=0, 0×1=0, 0×0=0

### Division Rules
- 1÷1=1, 0÷1=0, 1÷0=undefined, 0÷0=undefined

---

## 4. Complements

| Type | Method |
|------|--------|
| **1's Complement** | Replace every 0 with 1 and every 1 with 0 |
| **2's Complement** | 1's complement + 1 |

- **MSB = 0** → Positive number
- **MSB = 1** → Negative number
- 1's complement of 1's complement = **original number**

**Example**: 10110 → 1's comp: 01001 → 2's comp: 01001+1 = 01010

---

## 5. Logic Gates

### Three Categories
1. **Basic Gates**: AND, OR, NOT
2. **Universal Gates**: NAND, NOR
3. **Special Purpose Gates**: XOR, XNOR

### Basic Gates

| Gate | Symbol Op | Output HIGH when | Expression |
|------|-----------|-------------------|------------|
| **AND** | A·B | ALL inputs are HIGH | Y = A·B |
| **OR** | A+B | ANY input is HIGH | Y = A+B |
| **NOT** | A' | Input is LOW (inverts) | Y = A' |

### Universal Gates (can implement ALL basic gates)

| Gate | Output HIGH when | Expression |
|------|-------------------|------------|
| **NAND** | ANY input is LOW (not all HIGH) | Y = (A·B)' |
| **NOR** | ALL inputs are LOW | Y = (A+B)' |

### Special Purpose Gates

| Gate | Output HIGH when | Expression |
|------|-------------------|------------|
| **XOR** | Odd number of inputs are HIGH / inputs are **different** | Y = A'B + AB' |
| **XNOR** | Inputs are **same** | Y = AB + A'B' |

### Practical Applications
- **AND Gate**: Burglar alarm (alarm switch ON + person enters = alarm rings)
- **OR Gate**: Doorbell (front door OR back door pressed = bell rings)
- **NOT Gate**: Heating (temp < 20°C → NOT gate turns ON heating)

---

## 6. Boolean Algebra — Laws & Theorems

### Properties of 0 and 1
| Law | Expression |
|-----|-----------|
| 0 + A | = A |
| 0 · A | = 0 |
| 1 + A | = 1 |
| 1 · A | = A |

### Core Laws
| Law | OR Form | AND Form |
|-----|---------|----------|
| **Commutative** | A+B = B+A | A·B = B·A |
| **Associative** | (A+B)+C = A+(B+C) | (A·B)·C = A·(B·C) |
| **Distributive** | A+(B·C) = (A+B)·(A+C) | A·(B+C) = A·B+A·C |
| **Idempotent** | A+A = A | A·A = A |
| **Absorption** | A+A·B = A | A·(A+B) = A |
| **Complement** | A+A' = 1 | A·A' = 0 |
| **Involution** | (A')' = A | — |

- **A + A'B = A + B** (important distributive variant)

### De Morgan's Theorems
| Theorem | Statement |
|---------|-----------|
| **First** | (A+B)' = A'·B' — complement of sum = product of complements |
| **Second** | (A·B)' = A'+B' — complement of product = sum of complements |

---

## 7. K-Map (Karnaugh Map)

- Graphical method to get **simplest SOP or POS** form
- Minimizes number of gates needed

| Variables | K-Map Size | Cells |
|-----------|-----------|-------|
| 2 | 2×2 | 4 |
| 3 | 2×4 | 8 |
| 4 | 4×4 | 16 |

### SOP vs POS
- **SOP** (Sum of Products) = Minterms: Y = A·B + C·D'
- **POS** (Product of Sums) = Maxterms: Y = (A+B)·(C+D')

### K-Map Steps
1. Select K-map size based on number of variables
2. Identify minterms (SOP) or maxterms (POS)
3. **SOP**: Put 1's for minterms, 0's elsewhere
4. **POS**: Put 0's for maxterms, 1's elsewhere
5. Make rectangular groups of size 2, 4, 8... (powers of 2)
6. **SOP**: Find product terms from groups, SUM them
7. **POS**: Find sum terms from groups, PRODUCT them

### Don't Care Conditions
- Combinations where output is **not specified**
- Marked as **'X'** in K-map
- Can be treated as 0 or 1 to get better simplification

### Example (3-var SOP)
Z(A,B,C) = Σ(1,3,6,7) → Simplified: **A'C + AB**

### Example (4-var SOP)
F(P,Q,R,S) = Σ(0,2,5,7,8,10,13,15) → Simplified: **QS + Q'S'**

### Example (3-var POS)
F(A,B,C) = π(0,3,6,7) → Simplified: **(A'+B')(B'+C')(A+B+C)**

---

## 8. Multiplexer (MUX)

- **Many inputs → One output** (Data Selector)
- Uses **selection lines** to choose which input goes to output
- n selection lines → 2^n inputs

| MUX Type | Select Lines | Inputs |
|----------|-------------|--------|
| 2-to-1 | 1 | 2 |
| 4-to-1 | 2 | 4 |
| 8-to-1 | 3 | 8 |
| 16-to-1 | 4 | 16 |

### 4-to-1 MUX Truth Table
| B | A | Y (Output) |
|---|---|------------|
| 0 | 0 | D0 |
| 0 | 1 | D1 |
| 1 | 0 | D2 |
| 1 | 1 | D3 |

---

## 9. Demultiplexer (DEMUX)

- **One input → Many outputs** (reverse of MUX)
- Uses selection lines to route input to one specific output

| DEMUX Type | Select Lines | Outputs |
|------------|-------------|---------|
| 1-to-2 | 1 | 2 |
| 1-to-4 | 2 | 4 |
| 1-to-8 | 3 | 8 |
| 1-to-16 | 4 | 16 |

### 1-to-4 DEMUX Truth Table
| B | A | D0 | D1 | D2 | D3 |
|---|---|----|----|----|----|
| 0 | 0 | X | 0 | 0 | 0 |
| 0 | 1 | 0 | X | 0 | 0 |
| 1 | 0 | 0 | 0 | X | 0 |
| 1 | 1 | 0 | 0 | 0 | X |

---

## 10. Encoders

- Converts **2^N input lines → N output lines**
- Opposite of decoder
- Only one input line active at a time

### Octal to Binary Encoder (8-to-3)
- 8 inputs (D0-D7), 3 outputs (X, Y, Z)
- Boolean functions:
  - **X = D4 + D5 + D6 + D7**
  - **Y = D2 + D3 + D6 + D7**
  - **Z = D1 + D3 + D5 + D7**

### Decimal to BCD Encoder (10-to-4)
- 10 inputs (Y0-Y9), 4 outputs (A3, A2, A1, A0)
- Boolean functions:
  - **A3 = Y9 + Y8**
  - **A2 = Y7 + Y6 + Y5 + Y4**
  - **A1 = Y7 + Y6 + Y3 + Y2**
  - **A0 = Y9 + Y7 + Y5 + Y3 + Y1**

---

## 11. Decoders

- Converts **N input lines → 2^N output lines**
- Opposite of encoder

### 3-to-8 Line Decoder
- 3 inputs (X, Y, Z), 8 outputs (D0-D7)
- Each output = specific minterm:
  - D0 = X'Y'Z', D1 = X'Y'Z, D2 = X'YZ', D3 = X'YZ
  - D4 = XY'Z', D5 = XY'Z, D6 = XYZ', D7 = XYZ

### BCD to 7-Segment Decoder
- 4 BCD inputs (A,B,C,D) → 7 outputs (a,b,c,d,e,f,g)
- BCD only valid for 0-9 (inputs 10-15 are invalid/don't care)
- **Common Cathode**: All cathodes to ground, HIGH signal activates LED
- **Common Anode**: All anodes to +Vcc, LOW signal activates LED

---

## 12. Latches & Flip-Flops

### Key Concepts
- **Sequential circuit** = Combinational logic + Memory elements
- **Synchronous**: outputs change at specific time
- **Asynchronous**: outputs change at any time
- **Latch**: pulse-triggered (level-sensitive)
- **Flip-flop**: edge-triggered (clock-edge sensitive)

### Multivibrator Types
| Type | Stable States |
|------|--------------|
| Bistable | 2 stable states (latches & flip-flops) |
| Monostable | 1 stable state |
| Astable | No stable state |

### S-R Latch (Active-HIGH / NOR gate latch)

| S | R | Q | Q' | State |
|---|---|---|----|----|
| 0 | 0 | Q(prev) | Q'(prev) | No change |
| 0 | 1 | 0 | 1 | RESET |
| 1 | 0 | 1 | 0 | SET |
| 1 | 1 | 0 | 0 | **INVALID** |

### Gated D Latch
- Eliminates invalid state (R = S')
- When EN=1: **Q follows D**
- When EN=0: Q holds previous value
- Q(t+1) = D (when EN=1)

### Edge-Triggered Flip-Flops
- Change state ONLY at clock edge (positive or negative)

### S-R Flip-Flop
- Same as S-R latch but edge-triggered
- 3 parts: NAND latch + pulse-steering circuit + edge detector
- S=1,R=0 → SET; S=0,R=1 → RESET; S=0,R=0 → No change; S=1,R=1 → **INVALID**

### D Flip-Flop
- Single input D (data)
- D=1 → SET (Q=1); D=0 → RESET (Q=0)
- **Q follows D at clock edge**
- Made from S-R flip-flop by adding inverter (R = D')

### J-K Flip-Flop (Most versatile — NO invalid state)

| J | K | Q(t+1) | State |
|---|---|--------|-------|
| 0 | 0 | Q(t) | No change |
| 0 | 1 | 0 | RESET |
| 1 | 0 | 1 | SET |
| 1 | 1 | Q'(t) | **TOGGLE** |

### T Flip-Flop (Toggle)

| T | Q(t+1) | State |
|---|--------|-------|
| 0 | Q(t) | No change |
| 1 | Q'(t) | Toggle |

---
---

# UNIT 3: COMPUTER ORGANIZATION & ARCHITECTURE

---

## 1. Basic Computer Organization

### Three Main Components
1. **CPU** (Central Processing Unit)
2. **Memory Subsystem**
3. **I/O Subsystem**

### System Bus — Three Types

| Bus | Purpose | Direction |
|-----|---------|-----------|
| **Address Bus** | Carries memory addresses | **Unidirectional** (CPU → Memory) |
| **Data Bus** | Transfers data between components | **Bidirectional** |
| **Control Bus** | Carries control signals (READ, WRITE, I/O) | Mixed |

### CPU Organization — Three Internal Sections
1. **Register Section**: Set of registers + communication mechanism
2. **ALU** (Arithmetic Logic Unit): Performs arithmetic & logic operations
3. **Control Unit**: Controls the CPU, generates control signals

### Key Registers
- **Program Counter (PC)**: Holds address of next instruction to be fetched
- **Instruction Register (IR)**: Stores instruction code read from memory

### How CPU Fetches Data
1. CPU outputs memory address on address bus
2. Memory outputs data on data bus
3. If READ line is low → CPU reads from memory
4. If WRITE line is low → CPU writes to memory
5. Both lines HIGH → No communication

---

## 2. Instruction Codes

- **Computer instruction**: Binary code specifying a sequence of micro-operations
- **Instruction code**: Group of bits that instruct computer to perform specific operation

### Two Parts of Instruction Code
| Part | Purpose |
|------|---------|
| **Operation part (Opcode)** | Defines operations: add, subtract, multiply, shift, complement |
| **Address part** | Contains register/memory address of operand or result location |

- n bits in opcode → **2^n** possible operations

---

## 3. Stored Program Organization

- **One processor register**: Accumulator (AC)
- Memory with **4096 words** → needs **12 bits** for address (2^12 = 4096)
- **16-bit instruction format**: 4 bits opcode + 12 bits address
- 4 bits opcode → **16 possible operations**

### Execution Steps
1. Control reads 16-bit instruction from program portion of memory
2. Uses 12-bit address to read 16-bit operand from data portion
3. Executes operation specified by opcode
4. Operation performed with memory operand and content of AC

---

## 4. Addressing Modes

| Mode | Description |
|------|-------------|
| **Immediate** | Address part contains the operand itself (e.g., ADD 5) |
| **Direct** | Address part contains the address of the operand |
| **Indirect** | Address part contains a pointer to where the operand's address is found |

- **Bit I** distinguishes: I=0 → Direct, I=1 → Indirect
- **Effective Address**: The actual address of the operand in memory

---

## 5. Computer Registers

| Register | Symbol | Bits | Function |
|----------|--------|------|----------|
| Data Register | DR | 16 | Holds memory operand |
| Accumulator | AC | 16 | Processor register |
| Instruction Register | IR | 16 | Holds instruction code |
| Temporary Register | TR | 16 | Holds temporary data |
| Address Register | AR | 12 | Holds memory address |
| Program Counter | PC | 12 | Holds address of next instruction |
| Input Register | INPR | 8 | Holds input character |
| Output Register | OUTR | 8 | Holds output character |

---

## 6. Computer Instructions — Three Formats (all 16-bit)

### 1. Memory Reference Instructions (MRI)
- Bits 0-11: Address
- Bits 12-14: Opcode (000 to 110)
- Bit 15: Addressing mode (I=0 direct, I=1 indirect)

### 2. Register Reference Instructions
- Opcode = **111**, Bit 15 = **0**
- Operates on AC register; no memory operand needed
- 12 bits specify the operation
- Examples: **CLA (7800)** - Clear AC, **CLE (7400)** - Clear E

### 3. I/O Instructions
- Opcode = **111**, Bit 15 = **1**
- Bits 0-11 specify type of I/O operation
- Examples: **INP (F800)** - Input to AC, **OUT (F400)** - Output from AC

---

## 7. Memory Reference Instructions — Detail

| Instruction | Opcode | Hex | Function |
|-------------|--------|-----|----------|
| **AND** | 000 | 0/8 | AND memory word with AC, result → AC |
| **ADD** | 001 | 1/9 | Add memory word to AC, carry → E |
| **LDA** | 010 | 2/A | Load memory word → AC |
| **STA** | 011 | 3/B | Store AC → memory |
| **BUN** | 100 | 4/C | Branch unconditionally (effective addr → PC) |
| **BSA** | 101 | 5/D | Branch & save return address |
| **ISZ** | 110 | 6/E | Increment memory word, skip next if zero |

### Time Cycles
- AND, ADD, LDA, BSA: **6 cycles**
- STA, BUN: **5 cycles**

### Detailed Descriptions
- **AND**: ANDs each bit pair of AC and memory word; result stored in AC
- **ADD**: Adds memory word to AC; sum → AC, carry out → E flip-flop
- **LDA**: Transfers memory word to AC
- **STA**: Stores AC content into memory location
- **BUN**: Transfers effective address to PC (enables jumping out of sequence)
- **BSA**: Saves address of next instruction to memory, then branches to subroutine (effective addr + 1 → PC)
- **ISZ**: Increments memory word; if result = 0, PC increments (skips next instruction)

---

## 8. Instruction Set Completeness

A complete instruction set must include:
1. **Arithmetic, logical, and shift** instructions
2. **Data movement** instructions (memory ↔ registers)
3. **Program control** instructions (branching)
4. **Input and output** instructions

---

## 9. Timing and Control

- All register timing controlled by **master clock generator**
- Control signals generated by **control unit**

### Two Types of Control Organization

| Type | Implementation | Modification |
|------|---------------|-------------|
| **Hardwired** | Gates, flip-flops, decoders, digital circuits | Difficult to modify |
| **Microprogrammed** | Control information in control memory | Easy — update microprogram |

- Example timing: D3T4: SC ← 0 (at time T4, if decoder output D3 is active, sequence counter clears to 0)

---

## 10. Instruction Cycle

### Four Phases
1. **Fetch** instruction from memory
2. **Decode** the instruction
3. **Read effective address** from memory (if indirect addressing)
4. **Execute** the instruction

After step 4 → back to step 1 (continues until **HALT** instruction)

### Fetch & Decode Phase
- PC loaded with address of first instruction
- Sequence Counter (SC) cleared to 0
- After each clock pulse, SC incremented by 1
- Steps:
  1. Place content of PC onto bus (S2S1S0 = 010)
  2. Transfer bus content to AR
  3. Read instruction from memory at AR address
  4. Store in IR, increment PC

---

## 11. Determining Instruction Type (at T3)

During **T3**, control unit checks:

| Condition | Instruction Type |
|-----------|-----------------|
| D7'=1 (opcode ≠ 111) | **Memory Reference Instruction** |
| D7=1, I=0 (bit 15=0) | **Register Reference Instruction** |
| D7=1, I=1 (bit 15=1) | **I/O Instruction** |

---

## 12. Input-Output & Interrupts

### I/O Configuration
- Terminal with **keyboard** (input) and **printer** (output)
- Serial information: 8 bits alphanumeric code
- **INPR** (Input Register): receives serial data from keyboard
- **OUTR** (Output Register): sends serial data to printer
- Both registers communicate serially with interface, in parallel with AC

### I/O Flags
| Flag | Initial | Set When | Cleared When |
|------|---------|----------|-------------|
| **FGI** (Input Flag) | 0 | Key struck, data shifted into INPR | Computer accepts data |
| **FGO** (Output Flag) | 1 | Printer finishes | AC data transferred to OUTR |

### Program Interrupt
- External device informs computer when ready (instead of polling)
- Computer can do other tasks in the meantime
- **IEN** (Interrupt Enable Flip-flop):
  - **IOF** instruction: IEN ← 0 (interrupts disabled)
  - **ION** instruction: IEN ← 1 (interrupts enabled)
- When IEN=0: flags cannot interrupt
- When IEN=1: computer can be interrupted

### Interrupt Cycle
1. Store return address (PC → Memory[0])
2. Branch to interrupt service routine (0 → PC, load address 1)
3. IEN ← 0 (disable further interrupts)
4. Execute service routine
5. Return to original program

---

## 13. Important MCQs from Slides

1. **Who developed the basic architecture of computer?** → **(c) John Von Neumann**
2. **Which allows simultaneous write and read?** → **(c) RAM**
3. **Which is NOT a peripheral device?** → **(a) CPU**
4. **Computer address bus is:** → **(c) Unidirectional**
5. **Components connected to each other via:** → **(b) Computer architecture**
6. **CPU to memory bus:** → **(c) System bus**
7. **Memory unit communicating directly with CPU:** → **(b) Main memory**
8. **Computer stores data in:** → **(c) Binary form**
9. **MRI indicates:** → **(b) Memory Reference Instruction**
10. **Group of bits telling computer to perform operation:** → **(a) Instruction code**

### Number System MCQs from Slides
- (0.345)₁₀ → octal = **(0.26050)₈** [Option 2]
- (1011.011)₂ → decimal = **(11.375)₁₀** [Option 1]
- 22.5625 binary = **10110.1001** [Option 2]
- (B9F.AE)₁₆ → octal = **5637.534** [Option 3]
- 1001.0010₂ → decimal = **9.125** [Option 2]
- (1E.43)₁₆ → octal = **(36.206)₈** [Option 2]
- Same in octal, hex, and decimal = **7** [Option 3]
- (0.23)₁₀ → octal = **(0.165)₈** [Option 2]
- 2's complement of 11001011 = **00110101** [Option 3]

---

## Quick Recall Cheat Sheet

### Gate Output Summary (2-input)
```
AND:  0·0=0  0·1=0  1·0=0  1·1=1
OR:   0+0=0  0+1=1  1+0=1  1+1=1
NAND: 0·0=1  0·1=1  1·0=1  1·1=0
NOR:  0+0=1  0+1=0  1+0=0  1+1=0
XOR:  0⊕0=0  0⊕1=1  1⊕0=1  1⊕1=0
XNOR: 0⊕0=1  0⊕1=0  1⊕0=0  1⊕1=1
```

### Flip-Flop Quick Comparison
```
SR:  S=0,R=0→NC  S=0,R=1→Reset  S=1,R=0→Set  S=1,R=1→INVALID
D:   D=0→Reset   D=1→Set        (Q follows D)
JK:  J=0,K=0→NC  J=0,K=1→Reset  J=1,K=0→Set  J=1,K=1→TOGGLE
T:   T=0→NC      T=1→Toggle
```

### Key Formulas
```
Address bits = log₂(memory words)
Opcode bits = total bits - address bits - other fields
2-var K-map = 4 cells, 3-var = 8 cells, 4-var = 16 cells
Encoder: 2^N inputs → N outputs
Decoder: N inputs → 2^N outputs
MUX: 2^n inputs, n select lines, 1 output
DEMUX: 1 input, n select lines, 2^n outputs
```

### Instruction Format (16-bit Basic Computer)
```
Memory Ref:   [I(1 bit)][Opcode(3 bits)][Address(12 bits)]  opcode: 000-110
Register Ref: [0][111][Operation(12 bits)]
I/O:          [1][111][Operation(12 bits)]
```

---

> **Good luck on your exam tomorrow! 🎯**
