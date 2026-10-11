<p>
    <span style="float:left;">
        <h3> MPMC Experiment 7
    </span>

### AIM

Program to implement loop operations using C language and Assembly Language in 8051 Microcontroller.

### OBJECTIVE

-   To write and execute an 8051 C program in Keil µVision to copy 10 bytes of data from a source array to a destination array.
    
-   To write and execute an 8051 C program to count the number of 1s and 0s in an 8-bit binary number and transmit the results through UART.
    

### THEORY

Loops in C language are used to perform repetitive operations efficiently. Arrays represent memory blocks, where each element stores a value at a particular index. A loop can copy data from a source array to a destination array by transferring each element one by one.

Bitwise operations are used to check individual bits of a binary number. The bitwise AND operator (`&`) checks whether a bit is 1 or 0, while the right-shift operator (`>>`) moves the next bit into the least significant bit position. UART is used to transmit the calculated results through serial communication. Timer 1 generates the baud-rate timing required for UART communication.

### ALGORITHM

#### Copy 10 Bytes of Data

1.  Initialize the source array with 10 data bytes.
    
2.  Declare a destination array of 10 bytes.
    
3.  Initialize the loop counter to 0.
    
4.  Copy each source array element to the corresponding destination array element.
    
5.  Increment the loop counter and repeat until 10 bytes are copied.
    
6.  Verify that the destination array contains the same values as the source array.
    
7.  Halt the program using an infinite loop.
    

#### Count 1s and 0s in an 8-Bit Number

1.  Initialize the 8-bit number and set the counters for 1s and 0s to zero.
    
2.  Initialize UART and configure Timer 1 for baud-rate generation.
    
3.  Check the least significant bit using the bitwise AND operator.
    
4.  Increment the counter for 1s if the bit is 1; otherwise, increment the counter for 0s.
    
5.  Right-shift the number by one bit.
    
6.  Repeat the process for all eight bits.
    
7.  Transmit the counts of 1s and 0s through UART.
    
8.  Halt the program using an infinite loop.
    

### OUTCOME

Loop operations were implemented using C language programming on the 8051 Microcontroller. Data was copied between arrays, and the number of 1s and 0s in an 8-bit binary number was calculated and transmitted through UART.

### CONCLUSION

Thus, the experiment successfully demonstrated the use of loops, arrays, bitwise operations and UART serial communication in the 8051 Microcontroller using C language programming.