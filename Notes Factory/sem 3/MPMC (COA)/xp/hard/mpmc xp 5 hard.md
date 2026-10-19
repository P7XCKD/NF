<p>
    <span style="float:left;">
        <h3> MPMC Experiment 5
    </span>

### AIM

Simulation of selected instructions to understand the addressing modes and instruction set of 8051 Microcontroller.

### OBJECTIVE

-   To write a program to print “Hello World”.
    
-   To write a program to print the student's name using the 8051 Microcontroller.
    

### THEORY

The 8051 Microcontroller supports different instructions for data processing, input/output operations and serial communication. UART is used to transmit data serially, while Timer 1 generates the baud-rate timing required for serial communication.

In this experiment, UART is configured using the Serial Control Register (SCON) and Timer 1. The `printf()` function transmits the message through UART, which is displayed on the serial terminal. Port 1 bit 0 (P1.0) is toggled continuously during program execution.

### ALGORITHM

#### Print Hello World

1.  Initialize the serial communication settings.
    
2.  Configure Timer 1 for baud-rate generation.
    
3.  Start Timer 1.
    
4.  Transmit “Hello World” using `printf()`.
    
5.  Display the message on the serial terminal.
    

#### Print Name

1.  Initialize the serial communication settings.
    
2.  Configure and start Timer 1.
    
3.  Transmit the student's name using `printf()`.
    
4.  Display the name on the serial terminal.
    

### OUTCOME

The 8051 Microcontroller was configured for UART serial communication, and messages were transmitted through the serial terminal. Port 1 bit 0 was toggled during execution.

### CONCLUSION

Thus, the experiment demonstrated UART serial communication, Timer 1 configuration and the use of selected instructions of the 8051 Microcontroller.