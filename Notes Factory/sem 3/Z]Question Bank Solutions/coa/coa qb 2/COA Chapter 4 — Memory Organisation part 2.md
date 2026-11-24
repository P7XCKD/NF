# COA Chapter 4 — Memory Organisation
## Extra Answers — Topics Not Fully Covered
### Exam-Oriented | Simple Answers

These answers supplement the existing Chapter 4 solution. Direct Mapping, Memory Hierarchy, and Cache HIT/MISS are already covered in the original notes.

---

## Question 2: Explain the classification of Primary Memory in a computer system. Cover its subcategories, characteristics, advantages and disadvantages.

### Answer

**Primary memory** is the memory directly accessible by the CPU. It stores the data and instructions required for processing.

Primary memory can be classified into **RAM and ROM**.

### 1. RAM (Random Access Memory)

RAM is volatile memory. It stores data and programs temporarily while the computer is running. Its contents are lost when power is switched off.

**Types of RAM:**

| Type | Characteristics | Advantages | Disadvantages |
|---|---|---|---|
| SRAM (Static RAM) | Uses flip-flops and does not require refreshing. | Very fast. | Expensive and lower storage density. |
| DRAM (Dynamic RAM) | Uses capacitors and requires periodic refreshing. | Cheaper and higher storage density. | Slower and needs refreshing. |

### 2. ROM (Read Only Memory)

ROM is non-volatile memory. It retains its contents even when power is switched off. It is used to store permanent instructions such as firmware.

**Types of ROM:**

| Type | Characteristics | Advantages | Disadvantages |
|---|---|---|---|
| PROM | Can be programmed only once. | Useful for permanent data. | Cannot be erased or reprogrammed. |
| EPROM | Can be erased using ultraviolet light and programmed again. | Reusable. | Requires UV light and usually must be removed for erasing. |
| EEPROM | Can be electrically erased and reprogrammed. | Can be updated without UV light. | Write operations are slower and have limited write cycles. |

**Conclusion:** Primary memory includes RAM for temporary storage and ROM for non-volatile storage of instructions.

---

## Question 3: Explain Direct Memory Mapping in Cache Memory. Draw and explain a 3-level Cache Memory diagram and describe its working.

### Answer

**Direct Mapping:** In direct mapping, each block of main memory can be stored in only one fixed cache line.

**Formula:**

`Cache Line = Main Memory Block Number mod Number of Cache Lines`

For the full direct-mapping explanation, formula and example, refer to Question 1 in the original Chapter 4 notes.

### Three-Level Cache Memory

A three-level cache contains L1, L2 and L3 cache memories between the CPU and main memory.

### Diagram

```text
             +-------------+
             |     CPU     |
             +-------------+
                    |
             +-------------+
             |  L1 Cache   |
             | Smallest &  |
             | Fastest     |
             +-------------+
                    |
             +-------------+
             |  L2 Cache   |
             | Larger and  |
             | Slower      |
             +-------------+
                    |
             +-------------+
             |  L3 Cache   |
             | Largest and |
             | Slowest     |
             +-------------+
                    |
             +-------------+
             | Main Memory |
             |    (RAM)    |
             +-------------+
```

### Working

1. The CPU first searches for the required data in the L1 cache.
2. If the data is not found, it checks the L2 cache.
3. If it is still not found, it checks the L3 cache.
4. If the data is absent from all cache levels, it is fetched from main memory.
5. The fetched data may be placed in the cache levels for future use.

### Characteristics

- **L1:** Smallest and fastest cache, usually closest to or inside each CPU core.
- **L2:** Larger than L1 but slower.
- **L3:** Usually larger than L2 but slower; often shared by CPU cores.
- Main memory has much larger capacity but is slower than cache.

**Conclusion:** Three-level cache improves performance by checking small, fast caches before accessing slower main memory.

---

## Question 4: Explain ROM Memory and its types: PROM, EPROM and EEPROM.

### Answer

**ROM (Read Only Memory)** is a non-volatile memory that stores data and instructions permanently. It retains its contents even when the power is switched off.

### Types of ROM

1. **PROM (Programmable Read Only Memory):**
   - It can be programmed only once.
   - Once programmed, its contents cannot be erased or changed.

2. **EPROM (Erasable Programmable Read Only Memory):**
   - It can be erased using ultraviolet (UV) light.
   - After erasing, it can be programmed again.

3. **EEPROM (Electrically Erasable Programmable Read Only Memory):**
   - It can be erased and reprogrammed electrically.
   - It does not require ultraviolet light.

### Difference between ROM types

| PROM | EPROM | EEPROM |
|---|---|---|
| Programmed once. | Erased using UV light. | Erased electrically. |
| Cannot be erased. | Can be reprogrammed after erasing. | Can be reprogrammed electrically. |
| Least flexible. | More flexible than PROM. | More flexible and convenient. |

**Conclusion:** PROM is programmed once, EPROM is erased using UV light, and EEPROM is erased electrically.

---

## Question 7: Explain Memory Segmentation in 8086.

### Answer

**Memory segmentation** is a technique used in the 8086 microprocessor to divide its 1 MB memory into logical segments. Each segment can have a maximum size of 64 KB.

### Four segments of 8086

1. **Code Segment (CS):** Stores program instructions.
2. **Data Segment (DS):** Stores data used by the program.
3. **Stack Segment (SS):** Stores stack data, return addresses and temporary information.
4. **Extra Segment (ES):** Provides additional data storage, often used in string operations.

### Address Calculation

The 8086 generates a 20-bit physical address using a 16-bit segment address and a 16-bit offset.

`Physical Address = Segment Address × 10H + Offset`

### Example

If:
- Segment address = `2000H`
- Offset = `1500H`

Then:

`Physical Address = 2000H × 10H + 1500H`

`= 20000H + 1500H`

`= 21500H`

**Conclusion:** Memory segmentation divides memory into logical sections and allows the 8086 to access its 1 MB address space.

---

## Question 9: A byte-addressable main memory of 1 MB has a 16 KB cache with a 64-byte block size. Find the address format for Direct, Fully Associative and 4-way Set-Associative Mapping.

### Given

- Main memory = 1 MB = `2^20` bytes
- Cache = 16 KB = `2^14` bytes
- Block size = 64 bytes = `2^6` bytes
- Main memory address = 20 bits

### Step 1: Find number of cache lines

`Number of Cache Lines = Cache Size / Block Size`

`= 16 KB / 64 B`

`= 16384 / 64 = 256 = 2^8 lines`

### A. Direct Mapping

- Block offset = `log2(64) = 6 bits`
- Index = `log2(256) = 8 bits`
- Tag = `20 - 8 - 6 = 6 bits`

**Address format:**

| Tag | Index | Block Offset |
|---:|---:|---:|
| 6 bits | 8 bits | 6 bits |

### B. Fully Associative Mapping

- Block offset = 6 bits
- No index is required.
- Tag = `20 - 6 = 14 bits`

**Address format:**

| Tag | Block Offset |
|---:|---:|
| 14 bits | 6 bits |

### C. 4-Way Set-Associative Mapping

`Number of Sets = Number of Cache Lines / Number of Ways`

`= 256 / 4 = 64 = 2^6 sets`

- Block offset = 6 bits
- Set index = 6 bits
- Tag = `20 - 6 - 6 = 8 bits`

**Address format:**

| Mapping | Tag | Index / Set | Block Offset |
|---|---:|---:|---:|
| Direct | 6 bits | 8 bits | 6 bits |
| Fully Associative | 14 bits | Not required | 6 bits |
| 4-Way Set-Associative | 8 bits | 6 bits | 6 bits |

---

## Question 10: A byte-addressable main memory of 64 MB uses a 128 KB cache with a block size of 32 bytes. Find the address format for Direct, Fully Associative and 8-way Set-Associative Mapping.

### Given

- Main memory = 64 MB = `2^26` bytes
- Cache = 128 KB = `2^17` bytes
- Block size = 32 bytes = `2^5` bytes
- Main memory address = 26 bits

### Step 1: Find number of cache lines

`Number of Cache Lines = Cache Size / Block Size`

`= 128 KB / 32 B`

`= 131072 / 32 = 4096 = 2^12 lines`

### A. Direct Mapping

- Block offset = `log2(32) = 5 bits`
- Index = `log2(4096) = 12 bits`
- Tag = `26 - 12 - 5 = 9 bits`

**Address format:**

| Tag | Index | Block Offset |
|---:|---:|---:|
| 9 bits | 12 bits | 5 bits |

### B. Fully Associative Mapping

- Block offset = 5 bits
- No index is required.
- Tag = `26 - 5 = 21 bits`

**Address format:**

| Tag | Block Offset |
|---:|---:|
| 21 bits | 5 bits |

### C. 8-Way Set-Associative Mapping

`Number of Sets = Number of Cache Lines / Number of Ways`

`= 4096 / 8 = 512 = 2^9 sets`

- Block offset = 5 bits
- Set index = 9 bits
- Tag = `26 - 9 - 5 = 12 bits`

**Final Answer:**

| Mapping | Tag | Index / Set | Block Offset |
|---|---:|---:|---:|
| Direct | 9 bits | 12 bits | 5 bits |
| Fully Associative | 21 bits | Not required | 5 bits |
| 8-Way Set-Associative | 12 bits | 9 bits | 5 bits |

---

## Question 11: Compare Direct Mapping, Fully Associative Mapping and Set-Associative Mapping.

### Answer

| Direct Mapping | Fully Associative Mapping | Set-Associative Mapping |
|---|---|---|
| 1. Each main-memory block maps to one fixed cache line. | 1. A main-memory block can be placed in any cache line. | 1. A main-memory block maps to one set and can occupy any line in that set. |
| 2. Simple to implement. | 2. More complex to implement. | 2. Moderately complex to implement. |
| 3. Fast and inexpensive. | 3. Requires more complex searching hardware. | 3. Provides a balance between speed and flexibility. |
| 4. More conflict misses can occur. | 4. Fewer conflict misses generally occur. | 4. Fewer conflict misses than direct mapping generally occur. |
| 5. No replacement choice is needed; the mapped line is replaced. | 5. A replacement policy is needed when the cache is full. | 5. A replacement policy is needed within the selected set when it is full. |

**Conclusion:** Direct mapping is simple, fully associative mapping is flexible, and set-associative mapping combines features of both.

---

## Coverage Check

| Question | Topic | Status |
|---|---|---|
| 1 | Direct Memory Mapping | Already covered in original notes |
| 2 | Classification of Primary Memory | Added here |
| 3 | Direct Mapping + 3-Level Cache | Direct Mapping already covered; 3-Level Cache added here |
| 4 | ROM, PROM, EPROM and EEPROM | Added here |
| 5 | Memory Hierarchy | Already covered in original notes |
| 6 | Cache Need, HIT and MISS | Already covered in original notes |
| 7 | 8086 Memory Segmentation | Added here |
| 8 | Need for DMA and working | Covered in your Chapter 5 DMA notes |
| 9 | Address format numerical: 1 MB / 16 KB / 64 B / 4-way | Added here |
| 10 | Address format numerical: 64 MB / 128 KB / 32 B / 8-way | Added here |
| 11 | Compare three cache mapping techniques | Added here |
