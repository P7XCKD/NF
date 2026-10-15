<p>
    <span style="float:left;">
        <h3>MPMC Experiment 9</h3>
    </span>
</p>

### AIM

Implementation of Interfacing of LCD with the 8051 Microcontroller using Assembly Language Programming.

### OBJECTIVE

- To understand the interfacing of an LCD with the 8051 Microcontroller.
- To display characters on the LCD using Assembly Language programming in 8051 MCU IDE.

### THEORY

A Liquid Crystal Display (LCD) is used to display information and provide a user interface. Common alphanumeric LCDs include 1×16, 2×16, and 4×20 displays.

The LCD requires three control lines: RS, R/W, and EN, along with 8 or 4 data lines. In 8-bit mode, eight data lines are used, while 4-bit mode uses four data lines.

- **RS (Register Select):** When low (0), the LCD receives a command. When high (1), it receives character data.
- **R/W (Read/Write):** When low (0), data is written to the LCD. When high (1), data is read from the LCD.
- **EN (Enable):** Latches the data when the enable signal changes from HIGH to LOW.

The Display Data RAM (DDRAM) stores the characters displayed on the LCD. Commands and character data are sent to the LCD through the data lines.

### ALGORITHM

1. Start the 8051 MCU IDE.
2. Click on **Help** and open the Welcome dialog.
3. Scroll down and select the demonstration projects.
4. Click on **Virtual HW**.
5. Open the LCD `.VHC` file.
6. Start the simulation.
7. Switch on the LCD.
8. Click **RUN** to execute the program.
9. Observe the characters displayed on the LCD.
10. Capture and save the output screenshot.

### OUTCOME

LCD interfacing with the 8051 Microcontroller was demonstrated successfully using Assembly Language programming in 8051 MCU IDE.

### CONCLUSION

Thus, the experiment successfully demonstrated interfacing of an LCD with the 8051 Microcontroller using Assembly Language programming.