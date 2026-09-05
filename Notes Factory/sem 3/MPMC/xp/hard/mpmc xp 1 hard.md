# Experiment No. 1

### Aim

Simulation of selected instructions to understand the addressing modes and instruction set of 8086 microprocessors.

### Lab Objective

The lab will cover hands-on experience with Assembly language Programming of 8086b Microprocessor and C language programming of 8051 Microcontroller.

### Theory: ADDRESSING MODES OF 8086

The different ways in which a source operand is denoted in an instruction is known as addressing modes.

**Types of Addressing Modes:**

**1. Register Mode:** Both operands are registers.  
Example: `MOV AX, BX`

**2. Immediate Mode:** The source operand is an 8-bit or 16-bit data.  
Example: `MOV AX, 2000`

**3. Displacement or Direct Mode:** The effective address is directly given as displacement.  
Example: `MOV AX, [0500]`

**4. Register Indirect Mode:** The effective address is stored in SI, DI, or BX.  
Example: `MOV AX, [SI]`

**5. Based Indexed Mode:** Effective address is the sum of a base register and index register.  
Example: `MOV AX, [BX+DI]`

**6. Indexed Mode:** Effective address is the sum of an index register and displacement.  
Example: `MOV AX, [SI+2000]`

**7. Based Mode:** Effective address is the sum of a base register and displacement.  
Example: `MOV AL, [BP+0100]`

**8. Based Indexed Displacement Mode:** Effective address is the sum of a base register, index register, and displacement.  
Example: `MOV AL, [SI+BP+2000]`

**9. String Mode:** Used with string instructions. SI and DI are automatically incremented or decremented according to the Direction Flag.  
Example: `MOVSB`, `MOVSW`

**10. Input/Output Mode:** Used for input/output operations.  
Example: `IN`, `OUT`

**11. Relative Mode:** Effective address is calculated relative to the Instruction Pointer (IP).  
Example: `JNZ 8-bit address`

### Algorithm / Steps

1.  Create and save the `.asm` source file using a text editor.
    
2.  Assemble the program using TASM to check for errors.
    
3.  Link the `.obj` file using TLINK to generate the `.exe` file.
    
4.  Execute the generated `.exe` file.
    
5.  Use Turbo Debugger to execute instructions step-by-step and observe registers and memory.
    

### Programs Performed

**1. Immediate Addressing Mode**  
**Aim:** Load an immediate value into a register.

**2. Direct Addressing Mode**  
**Aim:** Access data using its memory address.

**3. Register Addressing Mode**  
**Aim:** Transfer data between registers.

**4. Register Indirect Addressing Mode**  
**Aim:** Access memory using SI register.

**5. Indexed Addressing Mode**  
**Aim:** Access array elements using an index.

### Conclusion

Thus we studied assembly language programming format and tools. As well DOS function INT21h. And simulated a few instructions.

### Lab Outcome:

1.  Execute assembly language programs on microprocessor using arithmetic and logical instructions of 8086 microprocessors
    
