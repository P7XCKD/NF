
# Experiment No. 2

### Aim

Implementation of arithmetic and logical operations using assembly language programme.

### Lab Objective

a) Program to perform arithmetic operations on 16-bit data.

b) To convert two digit packed BCD to unpacked BCD.

### Theory

#### Arithmetic Operations in 8086:

The 8086 microprocessor can perform arithmetic operations on 8-bit and 16-bit data using instructions like ADD, ADC, SUB, SBB, INC, DEC, MUL and DIV.

Arithmetic operations are carried out using registers, memory and immediate values.

#### Hexadecimal Addition

Hexadecimal addition is performed by loading two 16-bit hexadecimal values into registers and using the `ADD` instruction. The carry generated from the addition is checked using the Carry Flag.

Example:

```text
  4567H
+ 3219H
-------
  7780H
````

#### Packed BCD to Unpacked BCD

Packed BCD stores two decimal digits in one byte.

For packed BCD `79H`:

-   Lower digit = `09H`
    
-   Higher digit = `07H`
    

The lower digit is obtained using `AND` with `0FH`.

The higher digit is obtained using `AND` with `0F0H` and rotating the result by 4 bits using `ROL`.

The ASCII value of the digits can be obtained by adding `30H`.

### Algorithm / Steps

#### Program 1: 16-bit Hexadecimal Addition

1.  Initialize the data segment.
    
2.  Load the first 16-bit hexadecimal number into AX.
    
3.  Load the second 16-bit hexadecimal number into BX.
    
4.  Add the contents of BX to AX.
    
5.  Check the Carry Flag.
    
6.  If carry is generated, increment the carry register.
    
7.  Store the result and carry.
    
8.  Terminate the program.
    

#### Program 2: Packed BCD to Unpacked BCD

1.  Initialize the data segment.
    
2.  Load the packed BCD value into AL.
    
3.  Mask the lower nibble using `AND 0FH`.
    
4.  Store the lower digit.
    
5.  Add `30H` to obtain its ASCII value.
    
6.  Load the packed BCD value again into AL.
    
7.  Mask the higher nibble using `AND 0F0H`.
    
8.  Rotate the value by 4 bits using `ROL`.
    
9.  Store the higher digit.
    
10.  Add `30H` to obtain its ASCII value.
     
11.  Terminate the program.
     

### Conclusion

Thus, the 8086 assembly language programs successfully performed arithmetic operation on 16-bit data and converted two-digit packed BCD into unpacked BCD.

### Lab Outcome

1.  Execute assembly language programs on microprocessor using arithmetic and logical instructions of 8086 microprocessors.