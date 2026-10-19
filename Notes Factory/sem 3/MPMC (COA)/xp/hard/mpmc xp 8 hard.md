<p>
    <span style="float:left;">
        <h3> MPMC Experiment 8
    </span>

### AIM

To write and execute a program to perform serial communication between a microcontroller and a computer.

To transmit and receive data serially using the UART communication protocol.

### OBJECTIVE

- To transmit the character `A` continuously at 4800 baud using Assembly Language programming on the 8051 Microcontroller.
- To receive characters using the 8051 Microcontroller and display them through the serial window at 9600 baud.

### THEORY

Serial communication is a method of transferring data one bit at a time between a microcontroller and a computer. The 8051 Microcontroller supports UART (Universal Asynchronous Receiver/Transmitter) communication for serial data transmission and reception.

The `SCON` register configures the serial communication mode, while Timer 1 generates the baud-rate timing. The `SBUF` register is used to transmit and receive data. The `TI` flag indicates completion of transmission, and the `RI` flag indicates that data has been received.

In this experiment, the character `A` is transmitted continuously using UART. In the reception program, the microcontroller receives a character and transmits it back to the serial terminal for display.

### ALGORITHM

#### Serial Transmission

1. Initialize the program at address `00H`.
2. Configure Timer 1 in Mode 2 using `TMOD = 20H`.
3. Load the appropriate reload value into `TH1` to set the baud rate.
4. Configure the serial port using `SCON = 50H`.
5. Start Timer 1 using `SETB TR1`.
6. Load the character `A` into the `SBUF` register.
7. Wait until the `TI` flag becomes 1.
8. Clear the `TI` flag.
9. Repeat the process to transmit the character continuously.

#### Serial Reception

1. Initialize the program at address `00H` and jump to the main program.
2. Start the main program at address `30H`.
3. Configure the serial port using `SCON = 50H`.
4. Configure Timer 1 in Mode 2 using `TMOD = 20H`.
5. Load `-3` into `TH1` to generate approximately 9600 baud with an 11.0592 MHz crystal.
6. Start Timer 1 using `SETB TR1`.
7. Wait until the `RI` flag becomes 1.
8. Read the received character from `SBUF` into accumulator `A`.
9. Transfer the character back to `SBUF` for transmission.
10. Clear the `TI` and `RI` flags.
11. Repeat the process to receive and transmit the next character.

### OUTCOME

Serial communication was implemented on the 8051 Microcontroller using Assembly Language programming. The character `A` was transmitted continuously, and received characters were transmitted back and displayed through the UART serial terminal.

### CONCLUSION

Thus, the experiment successfully demonstrated serial data transmission and reception using the UART communication protocol on the 8051 Microcontroller.