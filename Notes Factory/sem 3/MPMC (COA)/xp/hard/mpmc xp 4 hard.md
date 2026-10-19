<p>
    <span style="float:left;">
        <h3> MPMC Experiment 4
    </span>

### AIM

Implementation of loop operations using Assembly Language Programming.

### OBJECTIVE

- To check whether a given string is a palindrome or not using 8086 Assembly Language.
- To generate the first `n` Fibonacci numbers using Assembly Language Programming.

### THEORY

Assembly language allows direct control of processor registers and memory. Loop operations are used to repeat a set of instructions for processing data.

In this experiment, string characters are compared from both ends of the string to determine whether the given string is a palindrome or not. The `SI` and `DI` registers are used to access the characters from the beginning and end of the string.

The Fibonacci series starts with `0` and `1`. Each subsequent number is obtained by adding the previous two numbers. Loop operations are used to generate the required number of Fibonacci terms.

### ALGORITHM

#### Palindrome

1. Define the string and required messages.
2. Initialize the data segment.
3. Set `SI` to the beginning of the string.
4. Find the end of the string.
5. Set `DI` to the beginning of the string.
6. Compare characters from both ends.
7. If the characters are different, display that the string is not a palindrome.
8. Move `SI` towards the beginning and `DI` towards the end.
9. Repeat the comparison until the middle of the string is reached.
10. If all characters match, display that the string is a palindrome.

#### Fibonacci Series

1. Read the number of terms `n`.
2. Initialize the first number as `0` and the second number as `1`.
3. Display the current Fibonacci number.
4. Add the previous two numbers to generate the next number.
5. Move the second number to the first position.
6. Store the newly generated number as the second number.
7. Repeat the process until `n` terms are generated.

### OUTCOME

Loop operations were successfully implemented using 8086 Assembly Language. The given string was checked for palindrome and the required number of Fibonacci terms was generated.

### CONCLUSION

Thus, the experiment successfully demonstrated the use of loop operations, registers, string comparison and arithmetic operations in Assembly Language.