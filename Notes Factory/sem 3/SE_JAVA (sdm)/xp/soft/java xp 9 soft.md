
<p>
    <span style="float:left;">
        <h3> JAVA Experiment 9
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Aim:

To implement a multithreaded Java application to perform concurrent execution and resource sharing by simulating a diagnostic workflow.

### Objective:

1. To understand the concept of multithreading in Java.
2. To create multiple threads using the `Thread` class.
3. To execute multiple tasks concurrently.
4. To simulate patient registration, image processing, analyte computation, and report generation.
5. To understand the use of `start()`, `run()`, and `Thread.sleep()` methods.

### Software Used:

- Java Development Kit (JDK 17)
- Visual Studio Code
- Command Prompt / Terminal
- Java Compiler (`javac`)

### Theory:

Multithreading in Java allows multiple threads to execute concurrently within a program. A thread is a lightweight unit of execution.

The `Thread` class is used to create threads, and the `run()` method contains the instructions executed by each thread. The `start()` method starts a new thread and allows it to execute concurrently with other threads.

The `Thread.sleep()` method pauses a thread for a specified time in milliseconds. In this program, four threads are created to simulate image processing, patient registration, analyte computation, and report generation.

Each thread has a different delay, demonstrating how multiple tasks can execute concurrently.

### Program:

```java
class Image extends Thread {
    public void run() {
        try {
            System.out.println("Thread 1: Image Processing Started");
            Thread.sleep(1000);
            System.out.println("Thread 1: Image Processing Completed");
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class Registration extends Thread {
    public void run() {
        try {
            System.out.println("Thread 2: Patient Registration Started");
            Thread.sleep(2000);
            System.out.println("Thread 2: Patient Registration Completed");
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class Analyte extends Thread {
    public void run() {
        try {
            System.out.println("Thread 3: Analyte Computation Started");
            Thread.sleep(3000);
            System.out.println("Thread 3: Analyte Computation Completed");
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class Report extends Thread {
    public void run() {
        try {
            System.out.println("Thread 4: Report Generation Started");
            Thread.sleep(4000);
            System.out.println("Thread 4: Report Generation Completed");
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

class xp9 {
    public static void main(String[] args) {
        Image t1 = new Image();
        Registration t2 = new Registration();
        Analyte t3 = new Analyte();
        Report t4 = new Report();

        t1.start();
        t2.start();
        t3.start();
        t4.start();
    }
}
````

> **Note:** Exception handling is used because `Thread.sleep()` may throw an exception if the thread is interrupted while sleeping. The `try-catch` block handles such exceptions.
### Output:

#### Sample Output — Multithreaded Execution

```
PS C:\Users\Public\Probz\Code\xp> java xp9
Error: Could not find or load main class xp9
Caused by: java.lang.ClassNotFoundException: xp9
PS C:\Users\Public\Probz\Code\xp> javac .\xp9.java
PS C:\Users\Public\Probz\Code\xp> java .\xp9.class
Error: Could not find or load main class .\xp9.class
Caused by: java.lang.ClassNotFoundException: /\xp9/class
PS C:\Users\Public\Probz\Code\xp> java .\xp9.java 
Thread 1: Image Processing Started
Thread 4: Report Generation Started
Thread 2: Patient Registration Started
Thread 3: Analyte Computation Started
Thread 1: Image Processing Completed
Thread 2: Patient Registration Completed
Thread 3: Analyte Computation Completed
Thread 4: Report Generation Completed
PS C:\Users\Public\Probz\Code\xp> 
```


### Outcome:

The Java program successfully creates and executes four threads to simulate image processing, patient registration, analyte computation, and report generation using the `Thread` class.

### Conclusion:

The experiment successfully demonstrates multithreading in Java. It provides practical understanding of thread creation, concurrent execution, the `start()` method, the `run()` method, and the `Thread.sleep()` method.