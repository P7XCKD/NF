# COA Module 2 — Extra Answers
## Questions Not Fully Covered in Existing Notes
### Exam-Oriented | Simple Answers

These answers supplement the uploaded Module 2 notes. Q1, Q2, Q4 and Q5 are already covered in the original notes.

---

## Question 3: Explain the concept of Pipelining in 8086. State its advantages.

### Answer

**Pipelining** is a technique in which different stages of multiple instructions are performed simultaneously to improve the speed of instruction processing.

### Pipelining in 8086

The 8086 uses two main units:

1. **Bus Interface Unit (BIU):**
   - Fetches instructions from memory.
   - Stores prefetched instructions in a 6-byte instruction queue.
   - Handles address generation and bus operations.

2. **Execution Unit (EU):**
   - Takes instructions from the instruction queue.
   - Decodes and executes the instructions.
   - Performs arithmetic and logical operations.

### Working

1. The BIU fetches instructions from memory and stores them in the 6-byte queue.
2. The EU takes instructions from the queue and executes them.
3. While the EU executes an instruction, the BIU can fetch the next instructions.
4. Both units work simultaneously, reducing CPU waiting time.

### Advantages

- Increases instruction-processing speed.
- Improves CPU performance and throughput.
- BIU and EU work simultaneously.
- Reduces the time the EU waits for instruction fetching.

**Conclusion:** The 8086 uses a 6-byte instruction queue to overlap instruction fetching and execution, improving overall performance.

---

## Question 6: Classify and explain computers according to the type of Parallelism (Flynn's Taxonomy). Mention advantages, disadvantages and uses.

### Answer

**Flynn's Taxonomy** classifies computer systems according to the number of instruction streams and data streams processed at a time.

There are four types:

### 1. SISD — Single Instruction, Single Data

- One processor executes one instruction stream on one data stream.
- Instructions are generally executed sequentially.
- **Advantages:** Simple design and easy programming.
- **Disadvantages:** Limited parallel processing and lower throughput.
- **Uses:** Traditional single-processor systems and simple sequential tasks.

### 2. SIMD — Single Instruction, Multiple Data

- One instruction is applied to multiple data items simultaneously.
- Multiple processing units perform the same operation on different data.
- **Advantages:** Fast processing of large datasets and efficient repeated calculations.
- **Disadvantages:** Not suitable when different data items require different instructions.
- **Uses:** Image processing, graphics, vector processing and scientific calculations.

### 3. MISD — Multiple Instruction, Single Data

- Multiple processing units perform different instructions on the same data stream.
- It is uncommon in general-purpose computers.
- **Advantages:** Can support redundant or independent processing of the same input for reliability.
- **Disadvantages:** Complex design and limited practical applications.
- **Uses:** Specialised fault-tolerant or redundant processing systems; often treated mainly as a theoretical classification.

### 4. MIMD — Multiple Instruction, Multiple Data

- Multiple processors execute different instructions on different data streams.
- Processors can work independently.
- **Advantages:** High performance, supports different tasks simultaneously and is flexible.
- **Disadvantages:** Complex design, communication and synchronisation overhead.
- **Uses:** Multiprocessor systems, servers, computer clusters and parallel computing.

### Summary Table

| Type | Instruction streams | Data streams | Main use |
|---|---:|---:|---|
| SISD | Single | Single | Sequential processing |
| SIMD | Single | Multiple | Graphics and image processing |
| MISD | Multiple | Single | Specialised fault-tolerant systems |
| MIMD | Multiple | Multiple | Servers and parallel computing |

**Conclusion:** Flynn's Taxonomy has four categories: SISD, SIMD, MISD and MIMD. They differ in the number of instruction and data streams processed.

---

## Question 7: Explain the Instruction Cycle in detail with a neatly labelled state diagram and describe each phase: Fetch, Decode, Execute, Memory Access and Write-Back.

### Answer

**Instruction Cycle** is the sequence of steps performed by the CPU to fetch, decode and execute an instruction.

### Phases of the Instruction Cycle

1. **Fetch:**
   - The CPU uses the Program Counter (PC) to locate the next instruction in memory.
   - The instruction is loaded into the Instruction Register (IR).
   - The PC is updated to point to the next instruction.

2. **Decode:**
   - The Control Unit decodes the instruction stored in the IR.
   - It identifies the operation and the required operands.

3. **Execute:**
   - The CPU performs the required operation.
   - The ALU may perform arithmetic or logical operations, or the CPU may perform a branch or data transfer.

4. **Memory Access:**
   - If required, the CPU reads data from memory or writes data to memory.
   - This phase is used by instructions that access memory.

5. **Write-Back:**
   - The final result is written into the destination register.
   - For example, the result of an addition may be stored in a CPU register.

### Diagram

```text
       +------------------+
       |      FETCH       |
       | Get instruction  |
       | from memory      |
       +--------+---------+
                |
                v
       +------------------+
       |      DECODE      |
       | Identify the     |
       | operation        |
       +--------+---------+
                |
                v
       +------------------+
       |     EXECUTE      |
       | Perform the      |
       | operation        |
       +--------+---------+
                |
                v
       +------------------+
       |  MEMORY ACCESS   |
       | Read/write data  |
       | if required      |
       +--------+---------+
                |
                v
       +------------------+
       |    WRITE-BACK    |
       | Store the result |
       +--------+---------+
                |
                v
        Next instruction
```

**Conclusion:** The instruction cycle has five commonly described phases: Fetch, Decode, Execute, Memory Access and Write-Back.

**Note:** Not every instruction needs a memory-access phase. For example, an operation using only CPU registers may skip data-memory access.

---

## Question 8: Explain Physical Address Calculation in 8086 with an example.

### Answer

The 8086 microprocessor has a **20-bit address bus**, so it can access up to **1 MB of memory**.

It uses a 16-bit segment address and a 16-bit offset to calculate the 20-bit physical address.

### Formula

\[
\text{Physical Address} = (\text{Segment Address} \times 10H) + \text{Offset}
\]

Multiplying the segment address by `10H` means shifting it left by 4 bits (one hexadecimal digit).

### Example

Given:
- Segment Address = `2000H`
- Offset = `1500H`

**Step 1: Multiply the segment address by 10H**

`2000H × 10H = 20000H`

**Step 2: Add the offset**

`20000H + 1500H = 21500H`

**Physical Address = 21500H**

### Another quick example

Given segment = `1000H` and offset = `0020H`:

`Physical Address = 1000H × 10H + 0020H`

`= 10000H + 0020H`

`= 10020H`

**Conclusion:** The 8086 combines a segment address and an offset to generate a 20-bit physical address.

---

## Coverage Check

| Question | Topic | Status |
|---|---|---|
| 1 | Basic Instruction Cycle with Interrupt Processing | Already covered in original notes |
| 2 | Six-Stage Instruction Pipeline | Already covered in original notes |
| 3 | Pipelining in 8086 and advantages | Expanded here |
| 4 | Softwired vs Hardwired Control Units | Already covered in original notes |
| 5 | Illustrate Six-Stage Pipelining | Already covered in original notes |
| 6 | Flynn's Taxonomy with advantages, disadvantages and uses | Expanded here |
| 7 | Five phases of Instruction Cycle | Expanded here |
| 8 | Physical Address Calculation in 8086 | Added here |
