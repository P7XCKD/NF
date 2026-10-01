<p>
    <span style="float:left;">
        <h3> Java Experiment 6
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Experiment No. 6:

### Aim:

To implement method overriding and runtime polymorphism using inheritance in Java.

### Objective:

1. To understand inheritance in Java.
2. To implement method overriding.
3. To demonstrate runtime polymorphism using parent and child class references.
4. To implement multilevel inheritance using medical test classes.

### Software Used:

- Java Development Kit (JDK)
- Visual Studio Code
- Command Prompt / Terminal
- Java Compiler (`javac`)

### Theory:

Method overriding occurs when a child class provides its own implementation of a method already defined in the parent class.

Runtime polymorphism allows a parent class reference to refer to objects of different child classes. The method that is executed is decided at runtime based on the actual object.

In this experiment, `MedicalTest` is the parent class. `UrineTest` and `BloodTest` override the `generateReport()` method. `GlucoseTest` extends `BloodTest` and also overrides the same method, demonstrating multilevel inheritance and runtime polymorphism.

### Program:

```java
class MedicalTest {
    void generateReport() {
        System.out.println("General medical test report");
    }
}

class UrineTest extends MedicalTest {
    @Override
    void generateReport() {
        System.out.println("Urine Test Report: Normal");
    }
}

class BloodTest extends MedicalTest {
    @Override
    void generateReport() {
        System.out.println("Blood Test Report: Normal");
    }
}

class GlucoseTest extends BloodTest {
    @Override
    void generateReport() {
        System.out.println("Glucose Test Report: Blood sugar is normal");
    }
}

public class MedicalTestDemo {
    public static void main(String[] args) {
        MedicalTest urineTest = new UrineTest();
        MedicalTest bloodTest = new BloodTest();
        MedicalTest glucoseTest = new GlucoseTest();

        urineTest.generateReport();
        bloodTest.generateReport();
        glucoseTest.generateReport();
    }
}
````

### Output:

```text
PS D:\A5EV5C> javac MedicalTestDemo.java
PS D:\A5EV5C> java MedicalTestDemo
Urine Test Report: Normal
Blood Test Report: Normal
Glucose Test Report: Blood sugar is normal
PS D:\A5EV5C>
```

### Outcome:

The program successfully demonstrates method overriding, inheritance, multilevel inheritance, and runtime polymorphism in Java.

### Conclusion:

The experiment demonstrates how different medical test classes can provide their own implementation of the `generateReport()` method using inheritance and runtime polymorphism.