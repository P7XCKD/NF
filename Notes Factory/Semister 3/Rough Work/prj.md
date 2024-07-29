1. procedureal oriented programming  **V/S**  object oriented programming 
![image](.attachments/a0378cbf5675896eaa6f6d5452bfc6119aa863c5.jpg)
2. features of object oriented programming
   ![image](.attachments/398fb22adf1de1d4f45af0737bbcae28f7412c74.jpg)
3. enlist famous language of object oriented programming
- C#
- C++
- Java
- Python
- Ruby
- Swift

4. explain the role of jvm in execution of java program
![image](.attachments/6cf738d2763dc73222dfe6346825572d68e11268.webp)


### Need for Java Program Execution

To execute a Java program, the source code must be compiled into bytecode and run by the Java Virtual Machine (JVM). This ensures platform independence and efficient execution.

### Role of JVM in Java Program Execution

1. **Class Loading**: The JVM loads the compiled `.class` files into memory via the ClassLoader.
2. **Bytecode Verification**: It checks the bytecode for security and correctness.
3. **Memory Allocation**: The JVM allocates memory into the heap (for objects) and the stack (for methods and local variables). Static members are also loaded.
4. **Execution**: The JVM identifies and executes the `main` method, with the JIT compiler optimizing performance by converting bytecode to machine code.
5. **Error Handling**: If the `main` method is absent, the JVM throws an error and halts execution.
6. **Garbage Collection**: The JVM's garbage collector reclaims memory from unused objects post-execution.

This process ensures secure and efficient execution of Java programs.