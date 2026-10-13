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

### Aim:

To implement method overriding and runtime polymorphism using inheritance in Java.

### Objective:

1. To understand inheritance.
2. To implement method overriding.
3. To demonstrate runtime polymorphism.
4. To implement multilevel inheritance.

### Software Used:

Java Development Kit (JDK)

### Theory:

Method overriding occurs when a child class provides its own implementation of a method already defined in the parent class.

Runtime polymorphism allows a parent class reference to refer to objects of different child classes. The method executed is decided at runtime.

In this experiment, `MedicalTest` is the parent class. `UrineTest` and `BloodTest` override `generateReport()`. `GlucoseTest` extends `BloodTest` and also overrides the method.

### Outcome:

The program successfully demonstrates method overriding, inheritance, multilevel inheritance, and runtime polymorphism.

### Conclusion:

The experiment demonstrates how different medical test classes can provide their own implementation of `generateReport()` using inheritance and runtime polymorphism.