<p>
    <span style="float:left;">
        <h3> MPMC Experiment 3
    </span>


### AIM

To implement loop operations using Assembly Language Programming.

### OBJECTIVE

- To read a list of integers from memory.
- To determine whether each integer is even or odd.

### THEORY

Assembly language allows direct control of processor registers and memory. Loop operations are used to repeat a set of instructions for processing multiple values.

In this experiment, an 8-bit number is analyzed bit-by-bit using the `RCR` instruction. The number of `1`s and `0`s in its binary representation are counted using loop operations.

### ALGORITHM

1. Define the memory model and data segment.
2. Store the input number and initialize counters for `1`s and `0`s.
3. Load the 8-bit number into the `AL` register.
4. Initialize the loop counter with 8.
5. Use the `RCR` instruction to examine one bit at a time.
6. Check the bit and increment the corresponding counter.
7. Decrement the loop counter.
8. Repeat the process until all 8 bits are checked.
9. Store the final counts of `1`s and `0`s.

### OUTCOME

Loop operations were successfully implemented using 8086 Assembly Language. The given 8-bit number was processed bit-by-bit and the number of `1`s and `0`s was counted.

### CONCLUSION

Thus, the experiment successfully demonstrated the use of loop operations and conditional instructions in Assembly Language to analyze all 8 bits of a given number.