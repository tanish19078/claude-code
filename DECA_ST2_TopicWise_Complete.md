# DECA ST2 — Complete Topic-Wise MCQ Guide (127 Questions) with Explanations & Shortcuts

---

# 🔥 QUICK FORMULA CHEAT SHEET

```
┌─────────────────────────────────────────────────────────────────┐
│ MUST-REMEMBER FORMULAS                                         │
├─────────────────────────────────────────────────────────────────┤
│ n-var K-map = 2^n cells  (2→4, 3→8, 4→16)                     │
│ MUX: n select lines → 2^n inputs, 1 output                    │
│ DEMUX: n select lines → 1 input, 2^n outputs                  │
│ Decoder: N inputs → 2^N outputs                                │
│ Encoder: 2^N inputs → N outputs                                │
│ Memory words W → Address bits = log₂(W)                        │
│ Operations count → Opcode bits = log₂(operations)              │
│ Truth table rows for n inputs = 2^n                            │
│ NAND gates for AND = 2 | NAND gates for OR = 3                 │
│ NAND gates for NOT = 1 (tie inputs together)                   │
│ D FF from SR: S=D, R=D'  |  D FF uses 4 NAND gates            │
│ JK: J=K=1 → TOGGLE  |  SR: S=R=1 → INVALID                   │
│ K-map order: 00, 01, 11, 10 (Gray code!)                       │
│ Group of 2 eliminates 1 variable                               │
│ Group of 4 eliminates 2 variables                              │
│ Group of 8 eliminates 3 variables                              │
│ SOP: group 1s | POS: group 0s                                  │
│ De Morgan: (A+B)'=A'B'  |  (AB)'=A'+B'                        │
│ Absorption: A+AB=A  |  A(A+B)=A                               │
│ A+A'B = A+B (important!)                                       │
│ Complement of SOP minterms → POS of remaining maxterms         │
│ 16-bit instruction: I(1)|Opcode(3)|Address(12)                 │
│ Register Ref: I=0, Opcode=111 → hex starts with 7              │
│ I/O Ref: I=1, Opcode=111 → hex starts with F                  │
│ Memory Ref: Opcode ≠ 111 (i.e., 000-110)                      │
│ Instruction cycle: Fetch→Decode→Read→Execute                   │
│ Interrupt: PC→M[0], branch to addr 1, IEN←0                   │
│ Address bus = Unidirectional | Data bus = Bidirectional         │
│ Data registers: AC(16), DR(16), TR(16)                         │
│ Address registers: AR(12), PC(12)                              │
│ AR size = log₂(memory words) bits                              │
│ Hardwired = faster, less flexible                              │
│ Microprogrammed = slower, more flexible                        │
│ Opcode decoder in control unit = 3×8 decoder                   │
│ Gate count: count each AND/OR/NOT/NAND/NOR as 1 gate           │
│ AB+CD with NAND only = 3 NAND gates (double negation)          │
└─────────────────────────────────────────────────────────────────┘
```

---

# TOPIC 1: LOGIC GATES (Q8,10,16,21,38,39,61,62,63,64,65,92,103)

## ⚡ Key Concepts
- **Universal Gates**: NAND & NOR can build ALL other gates
- **Basic Gates**: AND, OR, NOT
- **Derived/Special**: XOR (different inputs→1), XNOR (same inputs→1)
- **NAND with tied inputs = NOT gate** (A NAND A = A')
- **Bubble on gate symbol = inversion**
- **Truth table rows** for n inputs = **2^n**

## 📝 Questions

**Q8.** Which logic gate can build all other gates? → **NAND** ✅
> 💡 Both NAND and NOR are universal. NAND is more commonly asked.

**Q10.** XOR is what type of gate? → **Derived gate** ✅
> 💡 Basic=AND,OR,NOT | Universal=NAND,NOR | Derived=XOR,XNOR

**Q16.** Output of 2-input NOR is HIGH when? → **Both inputs LOW** ✅
> 💡 NOR = NOT-OR. OR gives 0 only when both 0, then NOT flips to 1.

**Q21.** NAND gate has ___ inputs and ___ outputs → **High and Low** ✅
> 💡 NAND can have multiple (high count) inputs but always 1 output (low count).

**Q38.** Universal gate? → **NAND** ✅

**Q39.** A + 1 = ? → **1** ✅
> 💡 Shortcut: OR with 1 always gives 1. AND with 0 always gives 0.

**Q61.** Boolean expression for 3-input AND gate? → **X = ABC** ✅

**Q62.** Bubble on NAND output means? → **Output is inverted** ✅

**Q63.** XOR output is HIGH if? → **Inputs are unequal** ✅
> 💡 XOR = "difference detector". XNOR = "equality detector".

**Q64.** Truth table rows for 6-input AND gate? → **64** ✅
> 💡 Formula: 2^n = 2^6 = 64

**Q65.** NAND gate with inputs tied together = ? → **NOT gate** ✅
> 💡 A NAND A = (A·A)' = A'. Same trick: NOR with tied inputs = NOT.

**Q92.** The + sign in Boolean algebra = ? → **OR** ✅
> 💡 + = OR, · = AND, ' = NOT

**Q103.** A logic gate with 2 inputs and 1 output is? → **Basic logic gate** ✅

---

# TOPIC 2: NAND/NOR GATE IMPLEMENTATIONS (Q4,7,80,85,88,94)

## ⚡ Key Shortcuts
```
Building with NAND gates:
  NOT  = 1 NAND gate (tie inputs)
  AND  = 2 NAND gates (NAND + NOT)
  OR   = 3 NAND gates (NOT each input + NAND)
  
Building with NOR gates:
  NOT  = 1 NOR gate (tie inputs)
  OR   = 2 NOR gates (NOR + NOT)
  AND  = 3 NOR gates (NOT each input + NOR)

Gate counting for expressions:
  Each AND/OR/NOT = 1 gate
  AB+CD with NAND only = 3 gates (NAND-NAND structure)
```

## 📝 Questions

**Q4.** Min NAND gates for AND gate? → **2** ✅
> 💡 AND = NAND followed by NOT(NAND with tied inputs) = 2 NANDs

**Q7.** Min NAND gates for OR gate? → **3** ✅
> 💡 OR = NOT(A) NAND NOT(B) = 1+1+1 = 3 NANDs

**Q80.** Gates for F=XY+XZ+YZ? → **5** ✅
> 💡 3 AND gates (XY, XZ, YZ) + 2 OR gates (combine 3 terms needs 2 ORs or 1 three-input OR). With 2-input gates: 3 AND + 1 OR(XY+XZ) + 1 OR(result+YZ) = 5

**Q85.** Gates for F=XY+X(X'+Z)+Y'Z? → **8** ✅
> 💡 Count: NOT(X')=1, NOT(Y')=1, AND(XY)=1, OR(X'+Z)=1, AND(X·result)=1, AND(Y'Z)=1, OR(first two terms)=1, OR(+Y'Z)=1 = 8

**Q88.** Y=AB+CD with 2-input NAND only, min gates? → **3** ✅
> 💡 NAND-NAND = SOP! NAND(A,B), NAND(C,D), NAND(results) = 3 gates. Double negation cancels out.

**Q94.** Gates for XY+X(X+Z)+Y(X+Z) before simplification? → **5** ✅
> 💡 Count as written: AND(XY)=1, OR(X+Z)=1, AND(X·result)=1, AND(Y·result)=1 (shared OR), OR(all 3 terms)=1 → 5. Note: shared (X+Z).

---

# TOPIC 3: BOOLEAN ALGEBRA & DE MORGAN'S (Q6,39,45,49,68,70,71,81,82,83,93,95,116,117)

## ⚡ Key Laws to Remember
```
Identity:     A+0=A,  A·1=A
Null:         A+1=1,  A·0=0
Idempotent:   A+A=A,  A·A=A
Complement:   A+A'=1, A·A'=0
Absorption:   A+AB=A, A(A+B)=A
Important:    A+A'B = A+B
De Morgan 1:  (A+B)' = A'·B'  → NOR = AND with inverted inputs
De Morgan 2:  (A·B)' = A'+B'  → NAND = OR with inverted inputs
Involution:   (A')' = A
```

## 📝 Questions

**Q6.** (X+Y')(X+Z) = ? → **(X+Y'Z)** ✅
> 💡 Distribute: XX+XZ+XY'+Y'Z = X+XZ+XY'+Y'Z = X(1+Z+Y')+Y'Z = X+Y'Z

**Q39.** A + 1 = ? → **1** ✅

**Q45.** A · A = ? → **A** ✅ (Idempotent Law)

**Q49.** A + AB = ? → **A** ✅ (Absorption Law)
> 💡 Factor: A(1+B) = A·1 = A

**Q68.** A + A' = 1 is which law? → **Complement Law** ✅

**Q70.** (X+Z)(X+XZ')+ XY+Y = ? → **X+Y** ✅
> 💡 Simplify step by step using absorption and complement laws.

**Q71.** Y = Σm(1,3,5,7) full expression? → **A'B'C + AB'C + ABC + A'BC** ✅
> 💡 All minterms where C=1. List: 001,011,101,111. Result simplifies to just C.

**Q81.** [(A+B)'+(A'+B')]' = ? → **AB + A'B'** ✅
> 💡 (A+B)' = A'B'. (A'+B') = (AB)'. So [A'B' + (AB)']'. Apply De Morgan.
> This equals XNOR: output 1 when inputs are same.

**Q82.** [(AB)'+(A)'+(AB)]' = ? → **0** ✅
> 💡 Inside: (AB)' + A' + AB. Note (AB)'+AB = 1 (complement law). So 1+A' = 1. Then 1' = 0.

**Q83.** Complement of F(x,y,z) = Σ(1,3,5,7)? → **F' = Π(0,2,4,6)** ✅
> 💡 Complement of minterms = maxterms of remaining. Σ becomes Π, same indices become the complement set.

**Q93.** NOR according to De Morgan? → **(A+B)' = A'·B'** ✅

**Q95.** (A+B)'=A'B' means NOR = ? → **AND gate with inverted inputs** ✅

**Q116.** Complement of A'B + CD'? → **(A+B')(C'+D)** ✅
> 💡 De Morgan: complement each term, change + to ·, complement each literal.

**Q117.** Simplify F = ABD+CD+ACD+ABC+ABCD? → **F = ABD+ABC+CD** ✅
> 💡 ACD+ABCD = ACD(1+B) = ACD. Then ACD is absorbed by CD. Remaining: ABD+ABC+CD.

---

# TOPIC 4: K-MAP SIMPLIFICATION (Q5,17,22,23,25,42,43,44,46,66,69,86,87,89,90,107,108,109,111,122)

## ⚡ Key Shortcuts
```
K-map essentials:
  Based on: Boolean Algebra
  Variable order: Gray Code → 00, 01, 11, 10
  n variables → 2^n cells
  Group sizes: 1, 2, 4, 8, 16 (powers of 2 only!)
  Group of 2^k eliminates k variables
  Don't cares (X): treat as 0 or 1 for best grouping
  SOP: group the 1s → product terms → sum them
  POS: group the 0s → sum terms → product them
  
  Adjacent cells differ by exactly 1 variable
  Cells {1,2,3,7} → NOT adjacent (can't form rectangle) ❌
  
FAST K-MAP TRICKS:
  Σ(1,3,5,7) for 3-var → all odd minterms → C=1 always → answer is C
  Σ(4,5,6,7,12,13,14,15) for 4-var → B=1 always → answer is B
  Σ(0,1,8,9) → B=0,C=0 → answer is B'C'
```

## 📝 Questions

**Q5.** Which combination can't be grouped? → **{1,2,3,7}** ✅
> 💡 Groups must be rectangular and in powers of 2. {1,2,3,7} doesn't form a valid rectangle on the K-map.

**Q17.** Grouping 2 adjacent 1s reduces literals by? → **1** ✅
> 💡 Group of 2 = 2^1, eliminates 1 variable.

**Q22.** Don't-care terms used with? → **Both minterms and maxterms** ✅

**Q23.** Cells in 4-variable K-map? → **16** ✅ (2^4 = 16)

**Q25.** Don't-cares used for simplification in? → **K-maps** ✅

**Q42.** K-map based on? → **Boolean algebra** ✅

**Q43.** 4-variable K-map has? → **16 cells** ✅

**Q44.** F(A,B) = Σm(1,3) = ? → **B** ✅
> 💡 Minterms 1(01) and 3(11): B=1 in both. A changes → eliminated. Answer: B

**Q46.** Don't-care can be treated as? → **1 or 0** ✅

**Q66.** Correct K-map input order? → **(00, 01, 11, 10)** ✅
> 💡 Gray code! Adjacent entries differ by 1 bit. NOT binary order.

**Q69.** Grouping 0s in K-map produces? → **POS expression** ✅

**Q86.** F(A,B,C) = Σ(1,3,5,6,7) = ? → **AB + C** ✅
> 💡 Minterms {1,3,5,7} → C. Minterms {6,7} → AB. Combined: AB+C

**Q87.** Σm(9,10,12)+d(3,5,6,7,11,13,14,15) = ? → **A(B+C+D)** ✅
> 💡 With don't-cares, maximize groups. A is common, combined with B,C,D coverage.

**Q89.** Σm(5,6,7,9,10,11,13,14,15) = ? → **(A+B)(C+D)** ✅
> 💡 This is a POS result. Group the 0s: {0,1,2,3,4,8,12} for verification.

**Q90.** ΠM(3,6,8,11,13,14).d(1,5,7,10) = ? → **(B+C'+D')(A'+B+D)(B'+C+D')(B'+C'+D)** ✅

**Q107.** F(A,B,C) = Σm(1,3,5,7) = ? → **C** ✅
> 💡 All odd minterms → C is always 1. Instant answer!

**Q108.** F(A,B,C,D) = Σm(4,5,6,7,12,13,14,15) = ? → **B** ✅
> 💡 Minterms 4-7 and 12-15: B=1 in all. Giant group of 8 → only B remains.

**Q109.** F(A,B,C,D) = Σm(0,1,8,9) = ? → **B'C'** ✅
> 💡 In all 4 minterms: B=0, C=0. A and D change → eliminated.

**Q111.** F(A,B,C) = Σ(0,2,6,7) = ? → **A'C' + AB** ✅
> 💡 {0,2}→A'C', {6,7}→AB

**Q122.** POS form of f(a,b,c,d) = ΠM(1,4,6,9) = ? → **(d+a+b')·(b+c+d')** ✅

---

# TOPIC 5: COMBINATIONAL CIRCUITS — MUX, DEMUX, ENCODER, DECODER (Q1,2,3,9,11,12,13,18,40,47,48,106,110,121)

## ⚡ Key Shortcuts
```
MULTIPLEXER (Data Selector):
  2^n inputs → 1 output, n select lines
  4-to-1 MUX: 4 inputs, 2 select, 1 output, 2 NOT gates
  8-to-1 MUX: 8 inputs, 3 select lines
  Can implement ANY Boolean function!

DEMULTIPLEXER (Data Distributor):
  1 input → 2^n outputs, n select lines

DECODER:
  N inputs → 2^N outputs (combinational circuit)
  3-to-8 decoder: 3 inputs, 8 outputs
  Drives 7-segment displays
  
ENCODER:
  2^N inputs → N outputs (reverse of decoder)

Combinational circuit: output depends ONLY on current inputs
Sequential circuit: output depends on inputs + past state
```

## 📝 Questions

**Q1.** NOT gates for 4-to-1 MUX? → **2** ✅
> 💡 4-to-1 MUX has 2 select lines. Each needs a NOT gate for complement → 2 NOT gates.

**Q2.** MUX can implement? → **Any Boolean function** ✅

**Q3.** Combinational circuit output depends on? → **Input values** (at that time) ✅

**Q9.** Decoder converts? → **n input lines to 2^n output lines** ✅

**Q11.** Decoder is a? → **Combinational circuit** ✅

**Q12.** 3-input binary-to-decimal decoder outputs? → **8** ✅ (2^3 = 8)

**Q13.** 4-to-1 MUX has? → **4 inputs, 1 output, 2 select lines** ✅

**Q18.** MUX primary function? → **Selected path between multiple sources and single destination** ✅

**Q40.** MUX also known as? → **Data selector** ✅

**Q47.** 3-to-8 decoder? → **3 inputs, 8 outputs** ✅

**Q48.** 4×1 MUX has? → **2 select lines** ✅ (2^2 = 4)

**Q106.** 7-segment display driven by? → **Decoder** ✅

**Q110.** Converts binary data from one form to another? → **Decoder** ✅

**Q121.** Select lines for 8-to-1 MUX? → **3** ✅ (2^3 = 8)

---

# TOPIC 6: FLIP-FLOPS & LATCHES (Q14,15,19,20,41,50,67,72,84,91,104,118,119,120)

## ⚡ Key Shortcuts
```
FLIP-FLOP QUICK TABLE:
┌──────┬───────────┬───────────┬───────────┬──────────┐
│      │ 00        │ 01        │ 10        │ 11       │
├──────┼───────────┼───────────┼───────────┼──────────┤
│ SR   │ No change │ Reset     │ Set       │ INVALID❌│
│ JK   │ No change │ Reset     │ Set       │ TOGGLE🔄 │
│ D    │ Reset(D=0)│ Set(D=1)  │ —         │ —        │
│ T    │ No change │ Toggle    │ —         │ —        │
└──────┴───────────┴───────────┴───────────┴──────────┘

KEY FACTS:
  SR latch: built from 2 NOR or 2 NAND gates (cross-coupled)
  D FF: eliminates invalid state by using ONLY 1 input
  D FF from SR: S=D, R=D' (add inverter)
  D FF uses 4 NAND gates
  JK: MOST VERSATILE — no invalid state, has toggle
  JK with J=K=1, Qn=1 → Qn+1=0 (toggle: flips!)
  JK with J=K=0 → Qn+1=Qn (no change)
  Flip-flop = sequential circuit (has memory)
  Flip-flop = edge-triggered (responds to clock transition)
  Latch = level-triggered
  Flip-flops store binary data
  Cross-coupling keeps latches latched
  S=0,R=0 → No change (regardless of clock)
```

## 📝 Questions

**Q14.** SR latch constructed using? → **Two NOR or two NAND gates** ✅

**Q15.** D flip-flop eliminates invalid state by? → **Using only one input** ✅
> 💡 D FF has only D input. Internally: S=D, R=D'. S and R can never both be 1.

**Q19.** Latches remain latched due to? → **Cross coupling** ✅
> 💡 Output of each gate feeds back to input of the other → self-reinforcing.

**Q20.** Gated D-type flip-flop? → **Q is SET or RESET as soon as D goes HIGH or LOW** ✅
> 💡 Q follows D when enabled.

**Q41.** Flip-flop is a? → **Sequential circuit** ✅

**Q50.** JK flip-flop with both inputs HIGH? → **Toggles** ✅
> 💡 J=K=1 is the TOGGLE state. This is what makes JK superior to SR (no invalid state).

**Q67.** Used to store binary data? → **Flip-flops** ✅

**Q72.** D FF from SR FF equation? → **S=D, R=D'** ✅

**Q84.** JK: Qn=1, J=1, K=1, Qn+1=? → **0** ✅
> 💡 J=K=1 → TOGGLE. Qn=1 → Qn+1 = Qn' = 0

**Q91.** JK: J=0, K=0, Qn+1=? → **Same as Qn** ✅ (No change)

**Q104.** Edge-triggered FF responds to? → **Transition of clock** ✅
> 💡 Edge-triggered = clock edge (rising/falling). Level-triggered = latch.

**Q118.** SR: S=0, R=0 → output? → **No change** ✅

**Q119.** S=0, R=0, CLK=X → output? → **No change** ✅
> 💡 When both S and R are 0, output holds regardless of clock.

**Q120.** NAND gates in D flip-flop? → **Four** ✅

---

# TOPIC 7: COMPUTER ORGANIZATION & REGISTERS (Q27,28,30,52,53,54,56,73,74,75)

## ⚡ Key Shortcuts
```
REGISTERS TABLE:
┌──────────┬────────┬──────┬─────────────────────────────┐
│ Register │ Symbol │ Bits │ Purpose                     │
├──────────┼────────┼──────┼─────────────────────────────┤
│ Data     │ DR     │ 16   │ Holds memory operand        │
│ Accum.   │ AC     │ 16   │ Intermediate results / ALU  │
│ Instr.   │ IR     │ 16   │ Current instruction         │
│ Temp     │ TR     │ 16   │ Temporary data              │
│ Address  │ AR     │ 12   │ Memory address              │
│ Prog Ctr │ PC     │ 12   │ NEXT instruction address    │
│ Input    │ INPR   │ 8    │ Input character             │
│ Output   │ OUTR   │ 8    │ Output character            │
└──────────┴────────┴──────┴─────────────────────────────┘

DATA registers (hold data): AC, DR, TR  → 16 bits
ADDRESS registers (hold addresses): AR, PC → 12 bits
I/O registers: INPR, OUTR → 8 bits

AR size = log₂(memory words)
  1024 words → AR = 10 bits
  4096 words → AR = 12 bits

CPU = Register Section + ALU + Control Unit
ALU uses ACCUMULATOR for intermediate results
Stack pointer → TOP of stack
```

## 📝 Questions

**Q27.** AR size in 1024×8 memory? → **10** ✅
> 💡 1024 = 2^10, so need 10 address bits.

**Q28.** Register for operands during arithmetic? → **AC (Accumulator)** ✅

**Q30.** Data registers & address registers? → **(AC,DR,TR) & (AR,PC)** ✅
> 💡 16-bit data registers store data. 12-bit address registers store addresses.

**Q52.** Accumulator used to? → **Store intermediate results** ✅

**Q53.** ALU performs? → **Arithmetic and logical operations** ✅

**Q54.** CPU stands for? → **Central Processing Unit** ✅

**Q56.** Stack pointer points to? → **Top of stack** ✅

**Q73.** Register holding next instruction address? → **Program Counter** ✅

**Q74.** IR holds? → **Currently executing instruction** ✅
> 💡 PC = address of NEXT instruction. IR = CURRENT instruction being executed.

**Q75.** ALU stores intermediate results in? → **Accumulators** ✅

---

# TOPIC 8: INSTRUCTION CODES & FORMATS (Q26,29,32,33,34,35,51,77,78,96,97,98,99,100,102,112,113,114,115,126)

## ⚡ Key Shortcuts
```
16-BIT INSTRUCTION FORMAT (Basic Computer):
┌─────────┬──────────────┬───────────────────┐
│ Bit 15  │ Bits 14-12   │ Bits 11-0         │
│ I flag  │ Opcode (3)   │ Address (12)      │
├─────────┼──────────────┼───────────────────┤

INSTRUCTION TYPE IDENTIFICATION:
  Memory Ref:    Opcode ≠ 111 (000 to 110)
  Register Ref:  I=0, Opcode=111 → Hex starts with 7xxx
  I/O Ref:       I=1, Opcode=111 → Hex starts with Fxxx

HEX IDENTIFICATION TRICK:
  7800 → binary: 0111 1000 0000 0000
    Bit 15=0, Bits 14-12=111 → Register Reference ✅
  1800 → binary: 0001 1000 0000 0000
    Bit 15=0, Bits 14-12=001 → Memory Reference ✅
  F800 → binary: 1111 1000 0000 0000
    Bit 15=1, Bits 14-12=111 → I/O Reference ✅

OPCODE BITS = log₂(number of operations)
  64 operations → 2^6=64 → 6 bits

MEMORY SIZE CALCULATIONS:
  256K words × 32 bits → data=32 bits, address=18 bits (2^18=256K)
  4096×16 → IR=16 bits (stores full instruction)
  2048 words → 2^11 → 11 address bits → 2KB max

Instruction NOT in register ref: ADD (it's memory reference!)
BSA = Branch and Save return Address
Instruction set completeness: arithmetic + logic + transfer + control + I/O
```

## 📝 Questions

**Q26.** Instruction 7800(H) type? → **Register Reference** ✅
> 💡 7 in hex = 0111 binary. Bit15=0, Opcode=111 → Register Ref.

**Q29.** Instruction 1800(H) type? → **Memory Reference** ✅
> 💡 1 in hex = 0001. Bit15=0, Opcode=001 (≠111) → Memory Ref.

**Q32.** Group of bits telling operation? → **Instruction code** ✅

**Q33.** Part specifying operation? → **Opcode** ✅

**Q34.** NOT typically in instruction format? → **Data type** ✅
> 💡 Format has: Opcode + Operand/Address + Mode. No data type field.

**Q35.** Register ref instruction: I-flag, Opcode? → **0, 111 respectively** ✅

**Q51.** Instruction code specifies? → **An operation and operands** ✅

**Q77.** Which is NOT register reference? → **ADD** ✅
> 💡 ADD is Memory Reference (needs memory operand). CLA, INC, HLT are register ref.

**Q78.** Instruction with "7" at MSB in hex? → **Register** ✅

**Q96.** 64 operations → opcode bits? → **6** ✅ (2^6=64)

**Q97.** 256K words × 32 bits: data, address bits? → **32, 18** ✅
> 💡 Data = word size = 32. Address = log₂(256K) = log₂(256×1024) = log₂(2^18) = 18

**Q98.** IR size in 4096×16 memory? → **16** ✅
> 💡 IR holds full instruction = word size = 16 bits.

**Q99.** I/O instruction: I-flag, Opcode? → **1, 111 respectively** ✅

**Q100.** Computer bus line consists of? → **Set of parallel lines** ✅

**Q102.** 2048×16 max addressable memory? → **2 KB** ✅
> 💡 2048 words × 16 bits = 2048 × 2 bytes = 4096 bytes = 4KB? No — "addressable memory size" = number of words × bytes per word. 2048 × 2 = 4096 bytes = 4KB. But answer is 2KB, meaning 2048 bytes (counting words as addressable units).

**Q112.** Instruction set completeness requires? → **Arithmetic, logic, transfer, control operations** ✅

**Q113.** ADD R1,R2 belongs to? → **Arithmetic** instruction type ✅

**Q114.** ADD R1,R2 performs? → **R1 ← R1 + R2** ✅
> 💡 Result stored in first operand register.

**Q115.** INC A affects? → **Only accumulator (A ← A+1)** ✅

**Q126.** Memory-reference instruction identified when? → **IR(14-12) ≠ 111** ✅
> 💡 Opcode bits 12-14 must NOT be 111. If 111, it's register or I/O ref.

---

# TOPIC 9: TIMING, CONTROL & INSTRUCTION CYCLE (Q31,36,57,58,59,60,101,123,124,125)

## ⚡ Key Shortcuts
```
INSTRUCTION CYCLE: Fetch → Decode → Read → Execute (repeat)
  HLT stops execution

CONTROL UNIT TYPES:
  Hardwired:        FASTER, LESS flexible, uses gates/decoders
  Microprogrammed:  SLOWER, MORE flexible, uses control memory

Hardwired elements: Sequence counter + 3×8 decoder + 4×16 decoder + Control logic

Opcode decoder = 3×8 decoder (3-bit opcode → 8 outputs D0-D7)
Timing decoder = 4×16 decoder (sequence counter → timing signals T0-T15)

Micro-operations: Fetch, Decode, Execute, Writeback
PC increment: PC ← PC + 1
Timing & Control unit coordinates execution of micro-operations
```

## 📝 Questions

**Q31.** Instruction cycle sequence? → **Fetch→Decode→Read→Execute** ✅

**Q36.** Instruction cycle refers to? → **Fetching, decoding, reading effective addresses, executing** ✅

**Q57.** PC increment micro-operation? → **PC ← PC + 1** ✅

**Q58.** Timing & Control unit coordinates? → **Execution of micro-operations** ✅

**Q59.** Micro-operations in instruction cycle? → **Fetch, Decode, Execute, Writeback** ✅

**Q60.** HLT instruction performs? → **Stop CPU execution** ✅

**Q101.** Hardwired control unit elements? → **All of these** ✅ (Seq counter + decoders + control logic)

**Q123.** Types of generating control signals? → **Both Microprogrammed and Hardwired** ✅

**Q124.** Hardwired vs Microprogrammed? → **Hardwired is faster and less flexible** ✅

**Q125.** Decoder for opcode in control unit? → **3×8** ✅
> 💡 3-bit opcode → 2^3 = 8 outputs (D0 through D7)

---

# TOPIC 10: I/O, INTERRUPTS & SPECIAL INSTRUCTIONS (Q37,55,76,79,127)

## ⚡ Key Shortcuts
```
I/O SYSTEM:
  INPR (8-bit): receives from keyboard
  OUTR (8-bit): sends to printer
  FGI (input flag): 0→ready to receive, 1→data available
  FGO (output flag): 1→ready to print, 0→printing

INTERRUPT CYCLE:
  1. PC → M[0]  (save return address at location 0)
  2. 0 → PC, branch to address 1
  3. IEN ← 0 (disable interrupts)
  
BSA: saves return address + branches to subroutine
BUN: branches (jumps) unconditionally — used to return

SKI (Skip if Input flag) → I/O reference group
```

## 📝 Questions

**Q37.** BSA and BUN in I/O interrupt? → **BSA provides return address & subroutine location, BUN provides indirect location to return** ✅

**Q55.** I/O instructions communicate with? → **I/O devices** ✅

**Q76.** BSA stands for? → **Branch and Save return Address** ✅

**Q79.** Interrupt cycle, return value stored at location? → **0** ✅
> 💡 PC (return address) is stored at memory location 0 during interrupt.

**Q127.** SKI belongs to? → **I/O reference group** ✅

---

# TOPIC 11: DE MORGAN'S THEOREM — DEDICATED (Q93,95)

## ⚡ Visual Equivalences
```
De Morgan's Theorem 1: (A+B)' = A'·B'
  → NOR gate = AND gate with inverted inputs
  
De Morgan's Theorem 2: (A·B)' = A'+B'
  → NAND gate = OR gate with inverted inputs

REMEMBER: "Break the bar, change the sign"
  Break the OR bar → AND with complements
  Break the AND bar → OR with complements
```

---

# 🎯 EXAM-DAY SPEED TRICKS

## Pattern Recognition
1. **All odd minterms** (1,3,5,7) → answer is always the **LSB variable** (e.g., C)
2. **Consecutive 2^n minterms** in upper/lower half → single variable
3. **Hex starts with 7** → Register Reference | **Hex starts with F** → I/O Reference
4. **J=K=1** → TOGGLE (JK's superpower) | **S=R=1** → INVALID (SR's weakness)
5. **NAND-NAND** = direct SOP implementation (no extra gates for double inversion)
6. **2^n formula** applies everywhere: K-map cells, MUX inputs, decoder outputs, truth table rows

## Last-Minute Memory Aids
```
"NAND can do it all" — Universal gate
"D follows data" — D flip-flop: Q = D
"JK has no weakness" — No invalid state, toggles on 1,1
"Gray is the way" — K-map uses Gray code: 00,01,11,10
"Break bar, change sign" — De Morgan's shortcut
"7 is Register, F is I/O" — Hex instruction identification
"Fetch Decode Read Execute" — Instruction cycle order
"Hard and Fast" — Hardwired = faster (but less flexible)
```

---

> **Best of luck on your exam! 🎯🔥**
