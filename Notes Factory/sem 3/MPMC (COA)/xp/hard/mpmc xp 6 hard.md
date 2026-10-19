<p>
    <span style="float:left;">
        <h3> MPMC Experiment 6
    </span>
          
### AIM

Implementation of Arithmetic and logical operations of 8051 microcontroller using C language programming.

### OBJECTIVE

-   To perform addition of two 16-bit numbers using Assembly Language programming on the 8051 Microcontroller.
    
-   To perform addition of two 16-bit numbers using C language programming on the 8051 Microcontroller.
    
-   To perform subtraction of two 16-bit numbers using C language programming on the 8051 Microcontroller.
    

### THEORY

The 8051 Microcontroller supports arithmetic instructions for addition, subtraction, multiplication and division. Arithmetic operations may affect flags such as Carry (CY), Auxiliary Carry (AC) and Overflow (OV), depending on the instruction and result.

C language provides arithmetic operators such as `+` for addition, `-` for subtraction, `*` for multiplication, `/` for division and `%` for modulo division.

In this experiment, two 16-bit numbers are added using Assembly Language and C language programming. Subtraction of two 16-bit numbers is also performed using C language. The results are observed in the register or memory window of Keil µVision 5.

### ALGORITHM

#### Addition Using Assembly Language

1.  Load the first 16-bit number into the DPL and DPH registers.
    
2.  Load the second number into registers A and B.
    
3.  Add the high bytes and store the result in DPH.
    
4.  Add the low bytes, considering the carry, and store the result in DPL.
    
5.  End the program.
    

#### Addition Using C Language

1.  Declare three unsigned integer variables `a`, `b` and `c`.
    
2.  Assign `0x1786` to `a` and `0x2038` to `b`.
    
3.  Add `a` and `b` and store the result in `c`.
    
4.  Halt the program using an infinite loop.
    

#### Subtraction Using C Language

1.  Declare three unsigned integer variables `i`, `j` and `k`.
    
2.  Assign `0x4567` to `j` and `0x1234` to `k`.
    
3.  Subtract `k` from `j` and store the result in `i`.
    
4.  Halt the program using an infinite loop.
    

### OUTCOME

Arithmetic operations were implemented on the 8051 Microcontroller using Assembly Language and C language programming. Addition and subtraction of two 16-bit numbers were performed, and the results were verified using Keil µVision 5.

### CONCLUSION

Thus, the experiment successfully demonstrated arithmetic operations on the 8051 Microcontroller using Assembly Language and C language programming. The programs were executed using Keil µVision 5, and the results were verified.