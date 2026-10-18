
<p>
    <span style="float:left;">
        <h3>MPMC Experiment 10</h3>
    </span>
</p>

### AIM

Interfacing of Seven Segment Display with the 8051 Microcontroller using Assembly Language Programming.

### SOFTWARE REQUIRED

8051 MCU IDE.

### THEORY

A 7-segment display is commonly used to display decimal numbers from 0 to 9 and some basic characters. It consists of seven LED segments arranged to display numeric information.

Seven-segment displays are commonly used in calculators, digital clocks, microwave ovens, washing machines, and radios.

There are two types of seven-segment displays:

- **Common Anode:** All the anode terminals of the LEDs are connected together.
- **Common Cathode:** All the cathode terminals of the LEDs are connected together.

Each segment is controlled using binary or hexadecimal codes. The 8051 microcontroller sends these codes through an output port to display the required digit.

### ALGORITHM / PROCEDURE

1. Start the 8051 MCU IDE.
2. Create a new project named **Seven Segment**.
3. Select the processor type as **AT89C51**.
4. Write the Assembly Language program.
5. Use the Seven Segment Editor under Utilities to obtain the hexadecimal codes.
6. Save the program as `seven segment.ASM`.
7. Open **Virtual HW → LED Display → Settings**.
8. Select Common Cathode, choose a colour, and configure port pins 0 to 7.
9. Switch on the display.
10. Simulate the program.
11. Open Virtual MCU and select Show Code Memory to view the hexadecimal codes.
12. Execute the program step by step and observe the program counter.
13. Set a breakpoint at `CLR A` and execute the program continuously.
14. Observe and capture the output.

### OUTCOME

Interfacing of a seven-segment display with the 8051 Microcontroller was demonstrated using Assembly Language Programming in 8051 MCU IDE.

### CONCLUSION

Thus, the experiment successfully demonstrated interfacing of a seven-segment display with the 8051 Microcontroller using Assembly Language Programming in 8051 MCU IDE.
