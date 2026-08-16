## fmp chapter 1 qb solution
***Q.1 Explain features of 8086 (each 4 mks) – min 4 points in feature.***  
#answer

![image](.attachments/cac8c40b4da5bf08344d0e36071f412ff72a57e1.png) 
![image](.attachments/36b21f2ae1292eeac0ed8a0c8b09cf732b9b8d4c.png) 
![image](.attachments/ea00752f9f5450c5f6bca0756e0d8505445ba33f.png) 
***

***Q.2 Define term Microprocessor - def 2mks, function – 2mks. PPT 4***  
#answer

- A **microprocessor** is an electronic component that acts as the **central processing unit (CPU)** of a computer, integrated onto a single chip that contains millions of tiny components, including transistors, resistors, and diodes.

- Functions of a microprocessor include:
  - **Arithmetic Operations**: Performs calculations such as addition and subtraction.
  - **Logic Operations**: Compares values and executes logical operations.
  - **Data Transfer**: Moves data between different memory locations.

***

***Q.3 Draw and explain architecture of 8086. Only draw – 4 mks. Draw explain any specific block - (each for 2 mks). PPT 4/6/8***  
#answer
![image](.attachments/31a0a3b17132da361803d8048d99aa123b2b6bf7.png) 
![image](.attachments/fa93640c0c5ebe2a6fde9bfb0162885e783893bf.png) 
![image](.attachments/83d631deff0764157519d4eafad3cecdff37b0a3.png) 
![image](.attachments/1a1f233af969f9459f248d8b66255d1f7fec02c2.png) ![image](.attachments/62c40c47fb22d4e5f2fad76863fd268e66bd4456.png) 

***

***Q.4 Define term pipelining and explain any two advantages of pipelining. PPT 4***  
#answer
![image](.attachments/b97807fbb26e5bb1e880f698081d4e9268fc7383.png) 


***

***Q.5 Draw flag register of 8086 and explain (only draw - 2 mks, any flag explanation with example) each 2 mks. PPT 4/6***  
#answer
![image](.attachments/d4cb2cfb8d84cbd3220ca10f18969b2bc3126d0c.png) 
![image](.attachments/952b5c85ee5362edf43e35cca714c0317f453a6f.png) 
![image](.attachments/6de6beb1c69544abd901412f27a497cdb49e0be6.png) 
![image](.attachments/6dcf9f49b1b7325f5a6e9d3c820d38097d620944.png) 
![image](.attachments/09c43c191d1ebec771cde6e70504685503c797d4.png) 
![image](.attachments/b76db57b14d4c6bbc72b42ce67bcd187ea2eed40.png) 
***

***Q.6 Explain special functions of general purpose registers (AX, BX, CX, DX)***  
- **Each register for 2 mks (minimum 2 functions)**  
- **Any one register with 3 functions for 3 mks**  
PPT 4/6/8  
#answer
![image](.attachments/c58b68d89e06b212ad537acc27f1d3b2e998b19c.png)
![image](.attachments/fbf38aa16a357f667098b6f79c3dc417c85f36e2.png) ![image](.attachments/a4b042c1eace40de76ed0a58d93ae47d10b467af.png) 
***

***Q.7 Explain use of any pin or signal of 8086 (each for 2 mks). PPT 4***  
#answer
![image](.attachments/ee613acc72420c9e2f612b7d3fa21768d447b057.png) 
![image](.attachments/d945d2a55caa76dd86d3bb374cc64a9042e3cce3.png) 
![image](.attachments/15c232bdbf0984d479160ebca156bf0c33716870.png) 
![image](.attachments/0f95029aa12f3b7ff7e35a195e31a138a2caa437.png) 
![image](.attachments/2b38336f4fc75d7ea2798e0af1eaf02c40b2691d.png) 
***

***Q.8 Draw and explain memory bank of 8086 (With all cases). PPT 8***  
#answer
![image](.attachments/0d634365f2f5fe683023402c8405410571eac0c9.png) ![image](.attachments/61c4fe350dae431c0b556c413887d9d3b7350d4c.png) 
![image](.attachments/89544027a632bd5f4dcbe5a3425da613095c0c4c.png) 
![image](.attachments/c2876fe2776759a465db54f595a0eb36ea224095.png) 
![image](.attachments/81acbae3a91482072512774fca4b2798cbd97394.png) 
![image](.attachments/f0d84a53e1d9e529ad89fa91467caf2874c6149b.png) 
![image](.attachments/813535e0a58dc6457a9e2f9b5aa78162cde11295.png) 
![image](.attachments/0cd66574e8f4d1a6513f71031b101b0b5380b122.png) 
***

***Q.9 Draw and explain memory segmentation of 8086. PPT 6***  
#answer
### MEMORY SEGMENTATION IN 8086

#### NEED FOR SEGMENTATION / CONCEPT OF SEGMENTATION

1. **Segmentation** means dividing memory into logically different parts called **segments**.
2. The **8086** has a **20-bit address bus**, allowing access to **2 MB** of memory.
3. This means the physical address will also be **20 bits**.
4. A **20-bit address** is not byte-compatible (equivalent to two and a half bytes).
5. To avoid dealing with this incompatible number, a **virtual model** of memory is created.
   - The memory is divided into **4 segments**: **Code, Stack, Data,** and **Extra**.
6. The **maximum size of a segment** is **64KB** and the **minimum size** is **16 bytes**.
7. Programmers can access each location using a **VIRTUAL ADDRESS**, which consists of:
   - **Segment Address**: Indicates where the segment is located in memory (base address).
   - **Offset Address**: Gives the offset of the target location within the segment.
8. Both Segment and Offset Addresses are **16 bits**, making them compatible for use by the programmer.
9. The Segment Address is provided only at the beginning of the program to initialize the segment; thereafter, only the **offset address** is needed.
10. This allows access to **1 MB** of memory using only a **16-bit offset address** for most of the program—this is the advantage of segmentation.
11. Dividing Code, Stack, and Data into different segments makes memory more organized and prevents accidental overwrites.
12. The maximum size of a segment is **64KB** because offset addresses are **16 bits** (2^16 = 64KB).
13. Programmers can create multiple Code/Stack/Data segments, utilizing the entire **1 MB**, but only one of each type can be **active** at a time.
14. The physical address is calculated using the formula:
    - **PHYSICAL ADDRESS = (SEGMENT ADDRESS × 10H) + OFFSET ADDRESS**
15. **Example**: If the Segment Address is **1234H** and the Offset Address is **000GH**, then the Physical Address is calculated as:
    - **(1234H × 10H) + 000GH = 12345H**
16. This formula ensures that the **minimum size** of a segment is **10H bytes (16 bytes)**.
![image](.attachments/9a677f1a3e250415d00277e4c36df53824868d8f.jpg) 
***

***Q.10 Draw and explain significance of queue in 8086. PPT 8***  
#answer
![image](.attachments/f961334854a5df5ded1e05d4fdbb596749bb7a89.png) 

***

***Q.11 When does the pipeline fail? PPT 4***  
#answer
### When Pipeline Fails

When a **Jump (JMP)** or **CALL** instruction appears in the main program, all existing instruction bytes in the queue are **flushed out**, resulting in an **empty queue**. The queue is then **reloaded** with the new instruction bytes corresponding to the locations specified in the JMP or CALL instructions. 

The refilling of the queue continues from these new locations related to the main program.
![image](.attachments/9e130edcbc15a0adfdfb5cae8eee22275c7c6764.png) 
***

***Q.12 Explain overflow flag with the help of example.***  
- **Use of flag – 2 mks**  
- **Range of +ve and -ve numbers – 2 mks**  
- **Example in detail – 2 mks**  
PPT 6  
#answer
![image](.attachments/89cdc79eebe239f3407880f1074afd98c9d11cca.png)
![image](.attachments/02d9262fef520151cb543ef7865a8e4d9b17aa31.png) 

***

***Q.13 Draw functional pin diagram of 8086. Only diagram. PPT 4***  
#answer
![image](.attachments/ce707814793c989a3b75d9b14124892e9d0e813c.png) 
***

***Q.14 Address calculation***  
#answer
![image](.attachments/fbf5bd153678e210e0ae98bd06bd4e26d3a9ebaa.png) 
***
