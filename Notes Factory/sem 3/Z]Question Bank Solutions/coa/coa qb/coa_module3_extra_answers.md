# COA Module 3 — Extra Answers
## Missing Question Bank Solutions | Exam-Oriented

These answers cover the seven topics identified as missing from the Module 3 notes.

---

## Q2. Draw and explain the flowchart for Restoring Division Algorithm

### Meaning
The **Restoring Division Algorithm** divides binary numbers by repeatedly subtracting the divisor from the partial remainder. If the result is negative, the previous remainder is restored.

### Registers
- `A`: Partial remainder; initially `0`.
- `Q`: Dividend; it stores the quotient during the process.
- `M`: Divisor.
- `n`: Number of bits in the dividend.

### Flowchart

```text
             START
               |
       Initialise A = 0
       Load Q = Dividend
       Load M = Divisor
          Count = n
               |
       Shift left [A,Q]
               |
          A = A - M
               |
        Is A negative?
          /       \
        YES       NO
         |         |
     Restore A    Keep A
      Q0 = 0      Q0 = 1
          \       /
         Count = Count - 1
               |
        Is Count = 0?
          /       \
        NO         YES
        |           |
   Repeat shift   Quotient = Q
   and subtract   Remainder = A
                    |
                   STOP
```

### Working
1. Initialise `A = 0`, load the dividend into `Q`, load the divisor into `M`, and set count to the number of dividend bits.
2. Shift the combined register `[A,Q]` one bit to the left.
3. Subtract the divisor: `A = A - M`.
4. If `A` is negative, restore it by adding `M` back and set the least significant bit of `Q` to `0`.
5. If `A` is non-negative, keep it and set the least significant bit of `Q` to `1`.
6. Decrease the count and repeat until it becomes zero.
7. The final quotient is in `Q` and the remainder is in `A`.

**Remember:** Negative result → restore and write `0`; non-negative result → keep and write `1`.

---

## Q4. Multiply (-2) and (-5) using Booth's Algorithm

### Given
- Multiplicand: `M = -2`
- Multiplier: `Q = -5`
- Use 4-bit 2's-complement representation.

### Step 1: Convert to binary

| Number | 4-bit representation |
|---|---|
| `+2` | `0010` |
| `-2` | `1110` |
| `+5` | `0101` |
| `-5` | `1011` |

Therefore, `M = 1110`, `Q = 1011`, and `-M = 0010`. Initially, `A = 0000`, `Q-1 = 0`, and count = 4.

### Step 2: Working table

| Step | Q0 Q-1 | Operation | A before shift | Q | Q-1 |
|---|---|---|---|---|---|
| Initial | — | Initialise | `0000` | `1011` | `0` |
| 1 | `10` | A = A − M | `0010` | `1011` | `0` |
| Shift 1 | — | Arithmetic right shift | `0001` | `0101` | `1` |
| 2 | `11` | No operation | `0001` | `0101` | `1` |
| Shift 2 | — | Arithmetic right shift | `0000` | `1010` | `1` |
| 3 | `01` | A = A + M | `1110` | `1010` | `1` |
| Shift 3 | — | Arithmetic right shift | `1111` | `0101` | `0` |
| 4 | `10` | A = A − M | `0001` | `0101` | `0` |
| Shift 4 | — | Arithmetic right shift | `0000` | `1010` | `1` |

### Final answer
`AQ = 00001010₂ = 10₁₀`

Therefore, **(-2) × (-5) = +10**.

---

## Q5. Multiply (-12) and (4) using Booth's Algorithm

### Given
- Multiplicand: `M = -12`
- Multiplier: `Q = +4`
- Use 5-bit 2's-complement representation.

### Step 1: Convert to binary

| Number | 5-bit representation |
|---|---|
| `+12` | `01100` |
| `-12` | `10100` |
| `+4` | `00100` |

Therefore, `M = 10100`, `Q = 00100`, and `-M = 01100`. Initially, `A = 00000`, `Q-1 = 0`, and count = 5.

### Step 2: Working table

| Step | Q0 Q-1 | Operation | A before shift | Q | Q-1 |
|---|---|---|---|---|---|
| Initial | — | Initialise | `00000` | `00100` | `0` |
| 1 | `00` | No operation | `00000` | `00100` | `0` |
| Shift 1 | — | Arithmetic right shift | `00000` | `00010` | `0` |
| 2 | `00` | No operation | `00000` | `00010` | `0` |
| Shift 2 | — | Arithmetic right shift | `00000` | `00001` | `0` |
| 3 | `10` | A = A − M | `01100` | `00001` | `0` |
| Shift 3 | — | Arithmetic right shift | `00110` | `00000` | `1` |
| 4 | `01` | A = A + M | `11010` | `00000` | `1` |
| Shift 4 | — | Arithmetic right shift | `11101` | `00000` | `0` |
| 5 | `00` | No operation | `11101` | `00000` | `0` |
| Shift 5 | — | Arithmetic right shift | `11110` | `10000` | `0` |

### Final answer
`AQ = 1111010000₂`.

This is a 10-bit 2's-complement negative number:
- Invert: `0000101111`
- Add 1: `0000110000`
- Magnitude: `48₁₀`

Therefore, **(-12) × 4 = -48**.

---

## Q6. Explain Memory Hierarchy Design and its characteristics in detail

### Definition
**Memory hierarchy** is the arrangement of computer memory into different levels based on speed, cost and storage capacity. The fastest memory is closest to the CPU, while larger and slower memory is farther away.

### Diagram

```text
             CPU
              |
          Registers
              |
           Cache
          (L1, L2, L3)
              |
         Main Memory
             RAM
              |
      Secondary Storage
          SSD / HDD
              |
       Backup Storage
```

### Characteristics
1. **Speed:** Registers are the fastest, followed by cache, RAM and secondary storage.
2. **Capacity:** Storage capacity generally increases as we move down the hierarchy.
3. **Cost per bit:** Faster memory is more expensive per bit; slower memory is cheaper.
4. **Access time:** Registers have the lowest access time, while SSDs and HDDs take longer.
5. **Distance from CPU:** Faster memory is closer to the CPU; slower memory is farther away.
6. **Purpose:** The hierarchy balances high speed, large capacity and affordable cost.

### Levels

| Level | Memory | Main characteristic |
|---|---|---|
| 1 | Registers | Fastest; very small storage inside CPU |
| 2 | Cache | Stores frequently used data and instructions |
| 3 | Main memory (RAM) | Holds currently running programs and data |
| 4 | Secondary memory (SSD/HDD) | Large, non-volatile storage |
| 5 | Backup storage | Used for long-term storage and backup |

### Working
1. The CPU first looks for the required data in registers or cache.
2. If the data is not in cache, it is fetched from RAM.
3. If it is not in RAM, it must be loaded from secondary storage.
4. Frequently used data may be copied into faster memory to make future access quicker.

**Conclusion:** Memory hierarchy balances speed, storage capacity and cost.

---

## Q8. Represent (-125)₁₆ in Single and Double Precision IEEE 754 formats

### Step 1: Convert hexadecimal to decimal
`(125)₁₆ = 1 × 16² + 2 × 16¹ + 5 × 16⁰`

`= 256 + 32 + 5 = 293`

Therefore, `(-125)₁₆ = -293₁₀`.

### Step 2: Convert 293 to binary
`293₁₀ = 100100101₂`

Therefore, `-293₁₀ = -100100101₂`.

### Step 3: Normalize
`100100101₂ = 1.00100101₂ × 2⁸`

- Sign bit = `1` because the number is negative.
- Actual exponent = `8`.
- Fraction bits = `00100101`, followed by zeroes.

### A. Single precision (32-bit)
- Sign bit = `1`
- Biased exponent = `8 + 127 = 135`
- `135₁₀ = 10000111₂`
- Mantissa = `00100101000000000000000` (23 bits)

**Final representation:**
```text
1 10000111 00100101000000000000000
```

### B. Double precision (64-bit)
- Sign bit = `1`
- Biased exponent = `8 + 1023 = 1031`
- `1031₁₀ = 10000000111₂`
- Mantissa = `00100101` followed by 44 zeroes (52 bits)

**Final representation:**
```text
1 10000000111 0010010100000000000000000000000000000000000000000000
```

**Remember:** Single precision uses bias 127 and 23 fraction bits; double precision uses bias 1023 and 52 fraction bits.

---

## Q10. Minimize the Boolean function using a 4-variable K-map

Given:

`F(A,B,C,D) = Σm(1,3,4,6,8,9,11,13) + Σd(0,2,14)`

### Step 1: Enter the minterms
Use Gray-code order `00, 01, 11, 10` for both rows and columns.

| AB \ CD | 00 | 01 | 11 | 10 |
|---|---:|---:|---:|---:|
| 00 | X | 1 | 1 | X |
| 01 | 1 | 0 | 0 | 1 |
| 11 | 0 | 1 | 0 | X |
| 10 | 1 | 1 | 1 | 0 |

`X` represents a don't-care condition.

### Step 2: Make groups
One valid grouping is:
- Group `(0,1,2,3)` gives `A'B'`.
- Group `(0,2,4,6)` gives `A'D'`.
- Group `(8,9)` gives `AB'C'`.
- Group `(9,11)` gives `AB'D`.
- Group `(9,13)` gives `AC'D`.

### Simplified expression
`F = A'B' + A'D' + AB'C' + AB'D + AC'D`

---

## Q11. Minimize the Boolean function using a 4-variable K-map

Given:

`F(A,B,C,D) = Σm(0,2,8,10,14) + Σd(5,15)`

### Step 1: Enter the minterms
Use Gray-code order `00, 01, 11, 10` for both rows and columns.

| AB \ CD | 00 | 01 | 11 | 10 |
|---|---:|---:|---:|---:|
| 00 | 1 | 0 | 0 | 1 |
| 01 | 0 | X | 0 | 0 |
| 11 | 0 | 0 | X | 1 |
| 10 | 1 | 0 | 0 | 1 |

`X` represents a don't-care condition.

### Step 2: Make groups
- Group `(0,2,8,10)` gives `B'D'`.
- Group `(10,14)` gives `ACD'`.

### Simplified expression
`F = B'D' + ACD'`

---

## Last-Minute Revision

| Topic | Remember |
|---|---|
| Restoring division | Shift, subtract, restore if negative |
| Booth's algorithm | `01` add, `10` subtract, `00/11` no operation |
| Memory hierarchy | Registers → Cache → RAM → SSD/HDD |
| IEEE 754 single | 1 sign + 8 exponent + 23 fraction; bias 127 |
| IEEE 754 double | 1 sign + 11 exponent + 52 fraction; bias 1023 |
| K-map | Group adjacent 1s in sizes of 1, 2, 4, 8 or 16; use don't-cares when helpful |
