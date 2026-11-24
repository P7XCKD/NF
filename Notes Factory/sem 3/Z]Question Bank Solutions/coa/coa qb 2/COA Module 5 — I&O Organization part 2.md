# COA Module 5 — I/O Organization
## Extra Answers — Questions Not Fully Covered
### Exam-Oriented | 4-Mark Answers

These answers cover the topics missing or only partially covered in the supplied Module 5 solution.

---

## Question 3: Differentiate between Memory-Mapped I/O and Isolated (I/O-Mapped) I/O.

### Answer

| Memory-Mapped I/O | Isolated (I/O-Mapped) I/O |
|---|---|
| 1. I/O devices share the same address space as memory. | 1. I/O devices have a separate address space. |
| 2. Memory instructions are used to access I/O devices. | 2. Special I/O instructions are used to access devices. |
| 3. It uses memory address space. | 3. It does not use the memory address space. |
| 4. More addressing modes may be available for I/O access. | 4. I/O access is generally limited to specific instructions. |
| 5. It may reduce the address space available for main memory. | 5. It does not reduce the address space available for main memory. |

**Conclusion:** Memory-mapped I/O uses the memory address space to access devices, whereas isolated I/O uses a separate address space and special instructions.

---

## Question 5: Draw the working diagram of the DMA controller and discuss the working of DMA.

### Answer

**Direct Memory Access (DMA)** allows data to transfer directly between an I/O device and main memory with little CPU involvement.

### Diagram

```text
                 System Bus
        +---------------------------+
        |                           |
      +-----+                 +------------+
      | CPU |                 | Main       |
      +-----+                 | Memory     |
        |                     +------------+
        |                           |
        +-----------+---------------+
                    |
              +-------------+
              | DMA         |
              | Controller  |
              +-------------+
                    |
              +-------------+
              | I/O Device  |
              +-------------+
```

### Working

1. The CPU initializes the DMA controller with the starting memory address, transfer count and read/write direction.
2. The I/O device requests a DMA transfer.
3. The DMA controller requests control of the system bus.
4. The CPU grants bus control when it can.
5. The DMA controller transfers data directly between the I/O device and main memory.
6. After the transfer is complete, the DMA controller sends an interrupt to the CPU.

**Conclusion:** DMA transfers a block of data directly between an I/O device and memory, reducing CPU workload.

---

## Question 8: Explain the role of Tri-State Buffers and Latches in I/O Module Interfacing.

### Answer

**Tri-State Buffers:**
- A tri-state buffer has three output states: 0, 1 and high impedance (Z).
- The high-impedance state disconnects the device from the bus.
- It allows multiple devices to share the same data bus without interfering with one another.

**Latches:**
- A latch is a temporary storage circuit.
- It holds data until new data is provided.
- It helps retain output data sent by the CPU so that the peripheral device can use it.

**Conclusion:** Tri-state buffers control access to shared bus lines, while latches temporarily store data during I/O operations.

---

## Question 10: Explain how DMA works and describe its modes of operation.

### Answer

**Direct Memory Access (DMA)** is a technique in which a DMA controller transfers data directly between an I/O device and main memory without the CPU handling every data item.

### Working of DMA

1. The CPU provides the starting memory address, transfer count and transfer direction to the DMA controller.
2. The I/O device sends a DMA request.
3. The DMA controller obtains control of the system bus.
4. Data is transferred directly between the I/O device and main memory.
5. After the transfer is complete, the DMA controller interrupts the CPU.

### Modes of DMA Operation

1. **Burst Mode (Block Mode):** The DMA controller transfers the entire block of data continuously. The CPU cannot use the system bus during this transfer.

2. **Cycle Stealing Mode:** The DMA controller transfers one data word at a time by taking individual bus cycles from the CPU. The CPU is paused briefly for each transfer.

3. **Transparent Mode:** The DMA controller transfers data only when the CPU is not using the system bus. Therefore, it does not interrupt normal CPU bus operations.

**Conclusion:** DMA reduces CPU workload. Its modes determine how the DMA controller shares the system bus with the CPU.

---

## Coverage Check

| Question | Topic | Status |
|---|---|---|
| 1 | Programmed I/O vs DMA | Already covered |
| 2 | Programmed I/O vs Interrupt-Driven I/O and DMA | Already covered |
| 3 | Memory-Mapped I/O vs Isolated I/O | Added here |
| 4 | Concept of DMA | Already covered |
| 5 | DMA controller diagram and working | Added a text diagram and working steps here |
| 6 | I/O Module structure | Already covered |
| 7 | Need and primary functions of an I/O module | Already covered in the basics section |
| 8 | Tri-State Buffers and Latches | Added here |
| 9 | Major functions of an I/O module | Already covered in the basics section |
| 10 | DMA working and modes of operation | Added here |
