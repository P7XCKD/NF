# COA Module 1 — Extra Answers
## Questions Not Fully Covered in Existing Notes
### Exam-Oriented | Simple 4-Mark Answers

These answers supplement the existing COA Module 1 notes. Questions 1–5 are already covered there.

---

## Question 6: Explain any two assembler directives of 8086 (DB, DW, DD or EQU).

**Assembler directives** are instructions given to the assembler to define data, reserve memory or assign constants. They are not executed by the processor as machine instructions.

| Directive | Meaning | Purpose | Example |
|---|---|---|---|
| `DB` | Define Byte | Defines/reserves 1 byte (8 bits). | `NUM DB 25H` |
| `DW` | Define Word | Defines/reserves 1 word (16 bits). | `VALUE DW 1234H` |
| `DD` | Define Doubleword | Defines/reserves 4 bytes (32 bits). | `DATA DD 12345678H` |
| `EQU` | Equate | Gives a constant name to a value; does not reserve storage. | `COUNT EQU 10` |

### Explanation of any two

1. **DB:** Used to define an 8-bit value.
   ```asm
   NUM DB 25H
   ```
   It defines a byte named NUM with the value 25H.

2. **DW:** Used to define a 16-bit value.
   ```asm
   VALUE DW 1234H
   ```
   It defines a word named VALUE with the value 1234H.

**Other directives:** DD defines a 32-bit value. EQU assigns a constant value to a symbolic name.

**Conclusion:** DB, DW and DD define data of different sizes, whereas EQU defines a symbolic constant.

---

## Question 7: Explain the interrupt pins of 8086.

The 8086 has two main interrupt request input pins: **INTR and NMI**. It also has an interrupt acknowledge signal, **INTA̅**, in minimum mode.

1. **INTR (Interrupt Request):**
   - It is a maskable interrupt input.
   - The CPU responds when the Interrupt Flag (IF) is set.
   - It is generally used for normal external device interrupt requests.
   - The CPU acknowledges the request using INTA̅ in minimum mode.

2. **NMI (Non-Maskable Interrupt):**
   - It is a non-maskable interrupt input.
   - It is not disabled by clearing the Interrupt Flag.
   - It is used for important events requiring urgent attention, such as a power-failure warning.

3. **INTA̅ (Interrupt Acknowledge):**
   - It is an active-low output in minimum mode.
   - It indicates that the processor has accepted an INTR request.
   - It allows external interrupt hardware to provide interrupt type/vector information.

**Conclusion:** INTR is maskable, NMI is non-maskable, and INTA̅ acknowledges an accepted INTR request.

---

## Question 8: What is the purpose of ALE, BHE̅, DEN̅ and DT/R̅ pins of 8086?

1. **ALE (Address Latch Enable):**
   - Indicates that a valid address is available on the multiplexed address/data lines.
   - Enables an external latch to store the address before those lines are used for data.

2. **BHE̅ (Bus High Enable):**
   - Active-low signal that enables the upper data byte (D8–D15).
   - Works with A0 to select the lower byte, upper byte or both byte banks.

3. **DEN̅ (Data Enable):**
   - Active-low output.
   - Enables the external data bus transceiver during data transfer.

4. **DT/R̅ (Data Transmit/Receive):**
   - Controls the direction of data through the external transceiver.
   - Selects whether data is transmitted from the processor or received by it.

**Conclusion:** ALE latches the address, BHE̅ selects the upper byte, DEN̅ enables the data transceiver, and DT/R̅ controls data direction.

---

## Question 9: List Minimum and Maximum mode pins of 8086 and explain any two in detail.

The 8086 operates in two modes selected by the **MN/MX̅** pin.

- **Minimum mode:** MN/MX̅ = 1. Used in a single-processor system. The 8086 generates the main bus control signals itself.
- **Maximum mode:** MN/MX̅ = 0. Used in systems requiring external bus-control support, such as multiprocessor/coprocessor arrangements.

### Minimum-mode control pins
- `M/IO̅`
- `WR̅`
- `INTA̅`
- `ALE`
- `DT/R̅`
- `DEN̅`
- `HOLD`
- `HLDA`

### Maximum-mode control/status pins
- `S0`, `S1`, `S2`
- `RQ/GT0̅`, `RQ/GT1̅`
- `LOCK̅`
- `QS0`, `QS1`

### Explain any two

1. **HOLD:**
   - Input used by an external bus master to request control of the system buses.
   - The processor responds after completing the current bus cycle.

2. **HLDA (Hold Acknowledge):**
   - Output from the processor.
   - Indicates that the processor has acknowledged HOLD and released the buses.

**Other maximum-mode signals:** S0–S2 identify the bus cycle; RQ/GT0̅ and RQ/GT1̅ are request/grant lines; LOCK̅ prevents another bus master from taking control during a locked operation; QS0 and QS1 indicate instruction-queue status.

**Conclusion:** Minimum mode generates bus-control signals directly from the 8086, while maximum mode uses external bus-control logic.

---

## Question 10: Explain common control pins of 8086.

Common control pins are signals used for controlling or coordinating processor operations.

1. **RD̅ (Read):** Active-low output indicating a read operation from memory or an I/O device.
2. **READY:** Input indicating whether memory or an I/O device is ready. If it is not ready, the processor inserts wait states.
3. **RESET:** Input used to reset the processor and restart execution from its reset entry point.
4. **CLK (Clock):** Provides timing signals to synchronize processor operations.
5. **TEST:** Checked by the `WAIT` instruction. The processor waits while TEST indicates that it should not continue.
6. **INTR:** Maskable interrupt request input.
7. **NMI:** Non-maskable interrupt request input.

**Conclusion:** These pins provide read control, timing, reset, wait-state and interrupt functions needed for proper processor operation.

---

## Coverage Check

| Question | Topic | Status |
|---|---|---|
| 1 | 8086 Architecture | Already covered in original notes |
| 2 | Architecture vs Organisation | Already covered in original notes |
| 3 | Performance metrics | Already covered in original notes |
| 4 | CPU time numerical | Already covered in original notes |
| 5 | 8086 Flag Register | Already covered in original notes |
| 6 | Assembler Directives | Added here |
| 7 | Interrupt Pins | Added here |
| 8 | ALE, BHE̅, DEN̅ and DT/R̅ | Added here |
| 9 | Minimum and Maximum Mode Pins | Added here |
| 10 | Common Control Pins | Added here |

**Exam note:** Pin names with an overbar (for example, RD̅ and DEN̅) are active-low signals. Copy the exact pin names and signal grouping used in your lecturer's diagram if it differs.
