# Experiment No. 1

### Aim

To simulate selected instructions and understand the addressing modes and instruction set of the 8086 microprocessor.

### Lab Objective

To gain hands-on experience with 8086 Assembly Language Programming and 8051 C programming.

### Theory: Addressing Modes of 8086

Addressing modes are the different ways used by the 8086 microprocessor to specify the source operand of an instruction.

**1. Register Mode:** Both operands are registers.  
Example: `MOV AX, BX`

**2. Immediate Mode:** The source operand is a constant 8-bit or 16-bit value.  
Example: `MOV AX, 1234H`

**3. Direct Mode:** The memory address is directly specified in the instruction.  
Example: `MOV AX, [0500H]`

**4. Register Indirect Mode:** The memory address is stored in BX, SI, or DI.  
Example: `MOV AX, [SI]`

**5. Based Indexed Mode:** Effective address is the sum of a base and index register.  
Example: `MOV AX, [BX+SI]`

**6. Indexed Mode:** Effective address is the sum of an index register and displacement.  
Example: `MOV AX, [SI+2000H]`

**7. Based Mode:** Effective address is the sum of a base register and displacement.  
Example: `MOV AL, [BP+0100H]`

**8. Based Indexed Displacement Mode:** Effective address is the sum of a base register, index register, and displacement.  
Example: `MOV AL, [SI+BP+2000H]`

**9. String Mode:** Used with string instructions; SI and DI are automatically updated.  
Example: `MOVSB`, `MOVSW`

**10. Input/Output Mode:** Used for communication with I/O devices.  
Example: `IN`, `OUT`

**11. Relative Mode:** The effective address is calculated relative to the Instruction Pointer (IP).  
Example: `JNZ 8-bit address`

### Algorithm / Steps

1.  Create and save the `.asm` source file.
    
2.  Assemble it using TASM.
    
3.  Link the `.obj` file using TLINK.
    
4.  Execute the generated `.exe` file.
    
5.  Use Turbo Debugger to observe registers and execute instructions step-by-step.
    

### Programs Performed

**1. Immediate Addressing Mode**  
**Aim:** Load an immediate value into a register.

**2. Direct Addressing Mode**  
**Aim:** Access data using its memory address.

**3. Register Addressing Mode**  
**Aim:** Transfer data between registers.

**4. Register Indirect Addressing Mode**  
**Aim:** Access memory using the SI register.

**5. Indexed Addressing Mode**  
**Aim:** Access array elements using an index.

### Conclusion

Thus, we studied 8086 assembly language programming, DOS function `INT 21H`, and different addressing modes through simulation.

### Lab Outcomes

1.  Execute 8086 programs using arithmetic and logical instructions.
    
2.  Execute 8086 programs using loop instructions.
    
3.  Understand addressing modes of the 8051.
    
4.  Implement C programs using the 8051 instruction set.
    
5.  Implement C programs for interfacing devices with 8051.
    

**Simple:** This keeps the important theory and steps while removing repetitive explanations and unnecessary details.