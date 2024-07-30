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

To run a Java program, the source code must be compiled into bytecode and executed by the JVM.

### Role of JVM in Execution

1. **Compilation**: Converts `.java` to `.class` file.
2. **Class Loader**: Loads `.class` files.
3. **Memory Allocation**: divides memory into  heap (for objects) and stack (for method calls and variables).
4. **Execution**: Runs `main` method.
5. **Garbage Collection**: Reclaims memory from unused objects.
***

5. how is java platform independent 
-> Java is platform-independent because it uses an intermediate form called Java Byte Code. When you write a Java program, it gets compiled into byte code, not machine-specific code. For example, if you write a Java program on a Windows computer, it will be compiled into byte code. You can then run this byte code on a Linux computer or a Mac, as long as there is a Java Virtual Machine (JVM) installed. The JVM interprets the byte code and runs the program, regardless of the underlying operating system. This is what makes Java programs able to run on different platforms without modification.
   ![image](.attachments/9c14f3fb4f7cd50225e2d3be517b9561aa9866bd.png)

***

11. explain the meaning of public  static void main (String[] args)
->
```public  static void main (String[] args) ```  is essential for your program to run, as it is the specific entry point that the Java runtime environment looks for when starting your application.

- **public**: This keyword means that the method is accessible from anywhere in the program. It's public to allow the Java runtime to call it from outside the class.
  
- **static**: This means that the method belongs to the class itself, not to instances of the class. This allows the Java runtime to call this method without having to create an instance of the class.

- **void**: This indicates that the method does not return any value.

- **main**: This is the name of the method. It's special because the Java runtime looks for this method when starting the program.

- **String[] args**: This is an array of `String` objects. It allows the program to accept arguments from the command line when it is run.

