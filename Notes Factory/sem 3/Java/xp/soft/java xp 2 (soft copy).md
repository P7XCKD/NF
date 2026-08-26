## Experiment No. 2
### Name: Dev Mandora
### Roll number: 62

### Aim:

To design and implement a Java program using **classes, objects, methods, and encapsulation** for developing a Patient and Test Strip Management System.

### Objective:

1.  To understand the use of classes and objects in Java.
    
2.  To implement constructors for initializing objects.
    
3.  To understand and implement encapsulation using private data members.
    
4.  To create and use methods in Java classes.
    
5.  To create relationships between `Patient`, `TestStrip`, and `DiagnosticReport` classes.
    
6.  To calculate and display the overall health status based on specified test conditions.
    

### Software Used:

-   Java Development Kit (JDK)
    
-   Visual Studio Code
    
-   Command Prompt / Terminal
    
-   Java Compiler (`javac`)
    

### Theory:

Java is an object-oriented programming language that allows programs to be designed using **classes and objects**.

A **class** is a blueprint that defines data members and methods. An **object** is an instance of a class. In this experiment, three classes are used: `Patient`, `TestStrip`, and `DiagnosticReport`.

The `Patient` class stores patient details such as patient ID, patient name, and age. Its data members are declared as `private`, demonstrating the concept of **encapsulation**. The constructor initializes these values, and the `display_patient()` method displays the patient information.

The `TestStrip` class stores glucose, protein, pH, and blood type values. The `health_status()` method checks whether all the given values are within the specified normal ranges. It uses relational operators, logical operators, and String comparison using `.equals()`.

The `DiagnosticReport` class contains `Patient` and `TestStrip` objects. Its `display_report()` method displays the patient information, test results, and overall health status.

The `Scanner` class is used to accept input from the user. The program creates objects of the required classes and uses their methods to generate the final diagnostic report.

> **Note:** The thresholds and blood-type condition used in this program are simplified values for demonstrating Java programming concepts and are not intended for actual medical diagnosis.

### Program:

```java
import java.util.Scanner;

class Patient {
    private int patient_id, age;
    private String patient_name;

    Patient(int patient_id, String patient_name, int age) {
        this.patient_id = patient_id;
        this.patient_name = patient_name;
        this.age = age;
    }

    public void display_patient() {
        System.out.println("Patient ID: " + patient_id);
        System.out.println("Patient Name: " + patient_name);
        System.out.println("Age: " + age);
    }
}


class TestStrip {
    private double glucose, protein, ph;
    private String bloodtype;

    TestStrip(double glucose, double protein, double ph, String bloodtype) {
        this.glucose = glucose;
        this.protein = protein;
        this.ph = ph;
        this.bloodtype = bloodtype;
    }

    public String health_status() {
        if(glucose >= 0 && glucose <= 50 &&
           protein >= 0 && protein <= 50 &&
           ph >= 5 && ph <= 7.5 &&
           (bloodtype.equals("O+") || bloodtype.equals("O-"))) {
            return "Normal";
        }
        else {
            return "Abnormal - Consult a doctor";
        }
    }

    public void display_test() {
        System.out.println("Glucose: " + glucose);
        System.out.println("Protein: " + protein);
        System.out.println("pH: " + ph);
        System.out.println("Blood Type: " + bloodtype);
    }
}


class DiagnosticReport {
    private Patient patient;
    private TestStrip test_strip;

    DiagnosticReport(Patient patient, TestStrip test_strip) {
        this.patient = patient;
        this.test_strip = test_strip;
    }

    public void display_report() {
        System.out.println("\n--- Diagnostic Report ---");

        patient.display_patient();
        test_strip.display_test();

        System.out.println("Overall Report: " + test_strip.health_status());
    }
}


public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter Patient ID: ");
        int patient_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter Patient Name: ");
        String patient_name = sc.nextLine();

        System.out.print("Enter Age: ");
        int age = sc.nextInt();

        System.out.println("\n--- Normal Ranges ---");
        System.out.println("Glucose: 0 - 50");
        System.out.println("Protein: 0 - 50");
        System.out.println("pH: 5 - 7.5");
        System.out.println("Blood Type: O+ or O-");

        System.out.print("\nEnter the glucose level: ");
        double glucose = sc.nextDouble();

        System.out.print("Enter the protein level: ");
        double protein = sc.nextDouble();

        System.out.print("Enter the pH level: ");
        double ph = sc.nextDouble();

        System.out.print("Enter the blood type: ");
        String bloodtype = sc.next();

        Patient p = new Patient(patient_id, patient_name, age);

        TestStrip t = new TestStrip(glucose, protein, ph, bloodtype);

        DiagnosticReport r = new DiagnosticReport(p, t);

        r.display_report();

        sc.close();
    }
}
```

### Output:

#### Sample Output 1 — Normal Result

```text
PS D:\A5EV5C> javac Main.java
PS D:\A5EV5C> java Main.java
Enter Patient ID: 1
Enter Patient Name: alex
Enter Age: 19

--- Normal Ranges ---
Glucose: 0 - 50
Protein: 0 - 50
pH: 5 - 7.5
Blood Type: O+ or O-

Enter the glucose level: 11
Enter the protein level: 12
Enter the pH level: 5.5
Enter the blood type: O+

--- Diagnostic Report ---
Patient ID: 1
Patient Name: alex
Age: 19
Glucose: 11.0
Protein: 12.0
pH: 5.5
Blood Type: O+
Overall Report: Normal
PS D:\A5EV5C>
```

#### Sample Output 2 — Abnormal Result

```text
PS D:\A5EV5C> java Main.java
Enter Patient ID: 2
Enter Patient Name: Brian
Enter Age: 22

--- Normal Ranges ---
Glucose: 0 - 50
Protein: 0 - 50
pH: 5 - 7.5
Blood Type: O+ or O-

Enter the glucose level: 55
Enter the protein level: 45
Enter the pH level: 7
Enter the blood type: AB-

--- Diagnostic Report ---
Patient ID: 2
Patient Name: Brian
Age: 22
Glucose: 55.0
Protein: 45.0
pH: 7.0
Blood Type: AB-
Overall Report: Abnormal - Consult a doctor
PS D:\A5EV5C>
```

### Outcome:

The Java program successfully creates and uses `Patient`, `TestStrip`, and `DiagnosticReport` classes. It accepts patient and test strip information from the user and uses methods and encapsulated data members to generate the diagnostic report.

The experiment demonstrates the practical use of **classes, objects, constructors, methods, encapsulation, object composition, conditional statements, and String comparison** in Java.

### Conclusion:

The experiment successfully demonstrates the implementation of object-oriented programming concepts in Java using a Patient and Test Strip Management System. The program shows how multiple classes can work together to solve a real-world-based problem while maintaining data encapsulation and modularity.