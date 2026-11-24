# COA Module 6 – Extra Answers

Missing answers from the existing solution file: Q4, Q5, Q7, Q10, Q11, Q12 and Q13. Q1's block diagram is present, but add the register table at the end of this file for fuller coverage.

---

## Q4. Embedded C: Transfer "A" serially at 9600 baud continuously (8 data bits, 1 stop bit)

Assumption: classic 8051 with an 11.0592 MHz crystal; serial format 8-N-1.

```c
#include <reg51.h>

void main(void)
{
    TMOD = 0x20;       // Timer 1, Mode 2 (8-bit auto-reload)
    TH1 = 0xFD;        // 9600 baud at 11.0592 MHz
    SCON = 0x50;       // Serial Mode 1: 8-bit UART, receiver enabled
    TR1 = 1;           // Start Timer 1

    while (1)
    {
        SBUF = 'A';    // Send character A
        while (TI == 0);
        TI = 0;        // Clear transmit flag
    }
}
```

**Explanation:** TMOD selects Timer 1 Mode 2. TH1 sets the baud-rate reload value. SCON selects 8-bit UART Mode 1. TR1 starts the timer. Writing `A` to SBUF starts transmission. TI becomes 1 when transmission finishes; the program clears it and sends the next character.

## Q5. 8051 C: Display temperature levels 0–9 on a 7-segment display

The example below cycles through digits 0–9 as simulated readings. It assumes a common-cathode display connected to P2, with bit 0 = segment a through bit 6 = segment g.
***
```
Group them based on the common ending:

### **Group 1 – Ends with F**

```
3F, 4F, 7F, 6F
```

Digits: **0, 3, 8, 9**

### **Group 2 – Ends with D**

```
6D, 7D
```

Digits: **5, 6**

### **Group 3 – Ends with 6**

```
06, 66
```

Digits: **1, 4**

### **Group 4 – Remaining values**

```
5B, 07
```

Digits: **2, 7**

**Memory trick:** First remember the four groups, then associate each value with its digit. This is easier than memorizing all ten values in sequence.
```
***
```c
#include <reg51.h>

void delay()
{
    int i, j;
    for(i = 0; i < 200; i++)
        for(j = 0; j < 250; j++);
}

void main()
{
    while(1)
    {
        P2 = 0x3F;  // 0
        delay();

        P2 = 0x06;  // 1
        delay();

        P2 = 0x5B;  // 2
        delay();

        P2 = 0x4F;  // 3
        delay();

        P2 = 0x66;  // 4
        delay();

        P2 = 0x6D;  // 5
        delay();

        P2 = 0x7D;  // 6
        delay();

        P2 = 0x07;  // 7
        delay();

        P2 = 0x7F;  // 8
        delay();

        P2 = 0x6F;  // 9
        delay();
    }
}

```
**Explanation:** The array stores the segment pattern for each digit. The loop sends each pattern to Port 2, and the delay keeps the digit visible before updating it. Use current-limiting resistors. For a common-anode display, use inverted patterns. In a real monitoring system, replace the counter with the actual sensor reading.

## Q7. Explain TMOD and TCON Special Function Registers

Both are 8-bit SFRs used with Timer 0 and Timer 1.

### TMOD – Timer Mode Register

```text
Bit:  7    6    5    4    3    2    1    0
     +----+----+----+----+----+----+----+----+
     |GATE|C/T | M1 | M0 |GATE|C/T | M1 | M0 |
     +----+----+----+----+----+----+----+----+
          Timer 1                  Timer 0
```

| Bits | Function |
|---|---|
| GATE | If 1, timer operation also depends on the external interrupt pin; if 0, TR controls it. |
| C/T | 0 = timer; 1 = counter. |
| M1, M0 | Select the operating mode. |

| M1 M0 | Mode | Operation |
|---|---|---|
| 00 | 0 | 13-bit timer/counter |
| 01 | 1 | 16-bit timer/counter |
| 10 | 2 | 8-bit auto-reload |
| 11 | 3 | Split Timer 0 mode |

### TCON – Timer Control Register

```text
Bit:  7    6    5    4    3    2    1    0
     +----+----+----+----+-----+-----+-----+-----+
     | TF1| TR1| TF0| TR0| IE1 | IT1 | IE0 | IT0 |
     +----+----+----+----+-----+-----+-----+-----+
```

| Bit | Function |
|---|---|
| TF1 | Timer 1 overflow flag. |
| TR1 | Starts Timer 1 when set; stops it when cleared. |
| TF0 | Timer 0 overflow flag. |
| TR0 | Starts Timer 0 when set; stops it when cleared. |
| IE1 | External Interrupt 1 flag. |
| IT1 | Selects edge- or level-triggering for Interrupt 1. |
| IE0 | External Interrupt 0 flag. |
| IT0 | Selects edge- or level-triggering for Interrupt 0. |

**Difference:** TMOD configures the timer/counter mode; TCON controls timer operation and holds timer/interrupt flags.

## Q10. Draw and explain SCON (Serial Control) Register

SCON is an 8-bit SFR that selects the serial mode, enables reception and stores serial status flags.

```text
Bit:  7    6    5    4    3    2    1    0
     +----+----+----+----+----+----+----+----+
     | SM0| SM1| SM2| REN| TB8| RB8| TI | RI |
     +----+----+----+----+----+----+----+----+
```

| Bit | Function |
|---|---|
| SM0, SM1 | Select the serial communication mode. |
| SM2 | Multiprocessor communication control. |
| REN | 1 enables serial reception; 0 disables it. |
| TB8 | Ninth bit transmitted in Modes 2 and 3. |
| RB8 | Ninth bit received in Modes 2 and 3; in Mode 1 it can hold the received stop-bit value. |
| TI | Set when serial transmission is complete. |
| RI | Set when a serial byte is received. |

| SM0 | SM1 | Mode | Description |
|---:|---:|---|---|
| 0 | 0 | 0 | Shift-register mode |
| 0 | 1 | 1 | 8-bit UART, variable baud rate |
| 1 | 0 | 2 | 9-bit UART, fixed baud rate |
| 1 | 1 | 3 | 9-bit UART, variable baud rate |

Example: `SCON = 0x50` selects Mode 1 and enables reception.

## Q11. Explain Stack and Stack Pointer (SP)

A stack is an area of internal RAM used to temporarily store data, return addresses and register values. It follows LIFO (Last In, First Out).

The Stack Pointer (SP) is an 8-bit SFR that stores the address of the top of the stack.

- **PUSH:** SP is incremented first, then the data is stored at the new address.
- **POP:** Data is read from the address pointed to by SP, then SP is decremented.
- The stack is used for subroutine calls, returns and interrupt handling.
- After reset, the default SP value is `07H`; the first pushed byte is stored at `08H`.

Example:

```asm
MOV  SP, #2FH
MOV  A, #55H
PUSH ACC
POP  B
```

SP becomes `30H` and `55H` is stored there. `POP B` copies `55H` into B and restores SP to `2FH`.

**Conclusion:** The stack stores temporary information; SP tracks its current top.

## Q12. Explain structure and operation of Port 0 and Port 1

Both are 8-bit bidirectional I/O ports on the classic 8051.

### Port 0
1. Works as an 8-bit general-purpose I/O port.
2. Also carries the multiplexed low-order address/data bus (`AD0–AD7`) during external memory access.
3. It is open-drain in general I/O mode.
4. External pull-up resistors are required for logic-high output in general I/O mode.

### Port 1
1. Works as an 8-bit bidirectional general-purpose I/O port.
2. Has internal pull-up resistors.
3. Can connect LEDs, switches and other digital devices.
4. Does not perform Port 0's multiplexed external-memory address/data function on the classic 8051.

| Port 0 | Port 1 |
|---|---|
| 8-bit bidirectional I/O. | 8-bit bidirectional I/O. |
| Open-drain in I/O mode. | Has internal pull-ups. |
| External pull-ups needed for general I/O logic-high output. | External pull-ups are not normally required. |
| Also carries multiplexed low address/data bus during external memory access. | General-purpose I/O on the classic 8051. |

## Q13. Explain any five 8051 Addressing Modes with examples

Addressing modes specify how an instruction accesses its operand.

### 1. Immediate addressing
The data is included directly in the instruction. `#` indicates immediate data.

```asm
MOV A, #25H
```
Loads `25H` into A.

### 2. Register addressing
The operand is in a CPU register.

```asm
MOV A, R2
```
Copies the contents of R2 into A.

### 3. Direct addressing
The instruction specifies the internal RAM or SFR address.

```asm
MOV A, 30H
```
Copies the contents of internal RAM address `30H` into A.

### 4. Register indirect addressing
A register holds the address of the operand. R0 or R1 is used for internal RAM indirect addressing.

```asm
MOV R0, #30H
MOV A, @R0
```
R0 holds address `30H`; the data at that address is copied into A.

### 5. Indexed addressing
The effective code-memory address is formed using A plus DPTR or PC. It is useful for lookup tables.

```asm
MOV DPTR, #TABLE
MOV A, #02H
MOVC A, @A+DPTR

TABLE: DB 10H, 20H, 30H, 40H
```
DPTR points to the table and A contains offset `02H`; the third table byte (`30H`) is read into A.

| Mode | Operand location | Example |
|---|---|---|
| Immediate | Data in instruction | `MOV A, #25H` |
| Register | CPU register | `MOV A, R2` |
| Direct | Specified RAM/SFR address | `MOV A, 30H` |
| Register indirect | Address held in R0/R1 | `MOV A, @R0` |
| Indexed | Code-memory table using A + DPTR/PC | `MOVC A, @A+DPTR` |

---

## Extra coverage for Q1: 8051 registers to add to the block diagram answer

Your existing solution already explains the main architecture blocks, but its register details are brief. Add this table if the question says "with all registers".

| Register | Size | Function |
|---|---:|---|
| A (Accumulator) | 8-bit | Stores operands and arithmetic/logic results. |
| B | 8-bit | Used in multiplication and division; also general-purpose. |
| PSW | 8-bit | Stores status flags and register-bank selection bits. |
| SP | 8-bit | Points to the top of the stack. |
| DPTR (DPH + DPL) | 16-bit | Data pointer for external data memory and code-memory table access. |
| PC | 16-bit | Holds the address of the next instruction. |
| R0–R7 | 8-bit each | General-purpose registers in the selected register bank; four banks are available. |
| TMOD | 8-bit | Selects Timer 0 and Timer 1 modes. |
| TCON | 8-bit | Controls timers and external interrupt flags. |
| SCON | 8-bit | Controls serial communication. |
| SBUF | 8-bit | Serial data buffer for transmission and reception. |
| IE | 8-bit | Enables or disables interrupts. |
| IP | 8-bit | Sets interrupt priority levels. |
| P0–P3 | 8-bit each | I/O port registers. |

**Exam tip:** Label CPU/ALU, ROM, RAM, four I/O ports, timers, serial port, interrupt control and oscillator/clock in the block diagram. Explain the registers separately in a table.
