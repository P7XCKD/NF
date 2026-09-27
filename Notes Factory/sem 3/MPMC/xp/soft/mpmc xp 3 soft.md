
<p>
    <span style="float:left;">
        <h3> MPMC Experiment 3
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

To implement loop operations using Assembly Language Programming.

### OBJECTIVE

- To read a list of integers from memory.
- To determine whether each integer is even or odd.

### THEORY

Assembly Language Programming allows direct control of processor registers and memory. Loop operations are used to repeat a set of instructions for processing data.

In this experiment, an 8-bit number is analyzed bit-by-bit using the `RCR` instruction. The number of `1`s and `0`s present in the binary representation is counted using loop operations.

### ALGORITHM

1. Define the data segment and store the input number.
2. Initialize counters for the number of `1`s and `0`s.
3. Load the 8-bit number into the `AL` register.
4. Initialize the loop counter with 8.
5. Use the `RCR` instruction to check one bit at a time.
6. If the carry flag is set, increment the counter for `1`.
7. Otherwise, increment the counter for `0`.
8. Decrement the loop counter.
9. Repeat the process until all 8 bits are checked.
10. Store the final counts of `1`s and `0`s.

### PROGRAM

```asm
.MODEL SMALL
.STACK 100H

.DATA
    num   DB 0A5H
    ones  DB 0
    zeros DB 0

.CODE

MAIN PROC

    MOV AX, @DATA
    MOV DS, AX

    MOV AL, num
    MOV CL, 8

    MOV BL, 0
    MOV BH, 0

    CLC

LOOP1:
    RCR AL, 1

    JC ONE

    INC BH
    JMP NEXT

ONE:
    INC BL

NEXT:
    DEC CL
    JNZ LOOP1

    MOV ones, BL
    MOV zeros, BH

    MOV AH, 4CH
    INT 21H

MAIN ENDP
END MAIN
````



### OUTPUT

For the input number `A5H`:

```text
A5H = 10100101B

Number of 1s = 4
Number of 0s = 4
```

### OUTCOME

Loop operations were successfully implemented using 8086 Assembly Language. The given 8-bit number was processed bit-by-bit and the number of `1`s and `0`s was counted.

### CONCLUSION

Thus, the experiment successfully demonstrated the use of loop and conditional instructions in Assembly Language to analyze an 8-bit number.