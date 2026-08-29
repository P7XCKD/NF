<p>
    <span style="float:left;">
        <h3> Java  Experiment 3
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">
### Aim:

To develop a Java program demonstrating **default, parameterized, and copy constructors** for object initialization in a Urine Test Strip diagnostic system.

### Objective:

1.  To understand the concept of constructors in Java.
    
2.  To implement default constructors.
    
3.  To implement parameterized constructors.
    
4.  To implement copy constructors.
    
5.  To initialize Patient, Test Strip, and diagnostic device objects using constructors.
    
6.  To understand how constructors initialize and copy object data.
    

### Software Used:

-   Java Development Kit (JDK)
    
-   Visual Studio Code
    
-   Command Prompt / Terminal
    
-   Java Compiler (`javac`)
    

### Theory:

A **constructor** is a special member of a class that is automatically called when an object is created. It is mainly used to initialize the data members of an object.

A **default constructor** does not require parameters and initializes an object with predefined or default values. A **parameterized constructor** accepts parameters and initializes an object with the values supplied by the user. A **copy constructor** creates a new object by copying the values of an existing object.

In this experiment, these constructors are demonstrated using a urine test strip diagnostic system. The `Patient` class stores patient information, while the `TestStrip` class stores diagnostic test information. The `DiagnosticDevice` class stores device and reagent information.

The program demonstrates how different constructors can be used to create and initialize objects with different sets of values.

### Program:

```java
import java.util.Scanner;

class Patient {
    private int patient_id;
    private String patient_name;
    private int age;

    // default
    Patient() {
        patient_id = 0;
        patient_name = "";
        age = 0;
    }

    // parameterized
    Patient(int patient_id, String patient_name, int age) {
        this.patient_id = patient_id;
        this.patient_name = patient_name;
        this.age = age;
    }

    // copy
    Patient(Patient p) {
        patient_id = p.patient_id;
        patient_name = p.patient_name;
        age = p.age;
    }

    public void display_patient() {
        System.out.println("Patient ID: " + patient_id);
        System.out.println("Patient Name: " + patient_name);
        System.out.println("Age: " + age);
    }
}


class TestStrip {
    private int strip_id;
    private String test_date;
    private double glucose;
    private double protein;

    TestStrip() {
        strip_id = 0;
        test_date = "";
        glucose = 0;
        protein = 0;
    }

    TestStrip(int strip_id, String test_date,
              double glucose, double protein) {
        this.strip_id = strip_id;
        this.test_date = test_date;
        this.glucose = glucose;
        this.protein = protein;
    }

    TestStrip(TestStrip t) {
        strip_id = t.strip_id;
        test_date = t.test_date;
        glucose = t.glucose;
        protein = t.protein;
    }

    public void display_test() {
        System.out.println("Strip ID: " + strip_id);
        System.out.println("Test Date: " + test_date);
        System.out.println("Glucose: " + glucose);
        System.out.println("Protein: " + protein);
    }
}


class DiagnosticDevice {
    private int device_id;
    private String reagent;

    DiagnosticDevice() {
        device_id = 0;
        reagent = "";
    }

    DiagnosticDevice(int device_id, String reagent) {
        this.device_id = device_id;
        this.reagent = reagent;
    }

    DiagnosticDevice(DiagnosticDevice d) {
        device_id = d.device_id;
        reagent = d.reagent;
    }

    public void display_device() {
        System.out.println("Device ID: " + device_id);
        System.out.println("Reagent: " + reagent);
    }
}


public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter patient id: ");
        int patient_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter patient name: ");
        String patient_name = sc.nextLine();

        System.out.print("Enter age: ");
        int age = sc.nextInt();

        System.out.print("Enter strip id: ");
        int strip_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter test date: ");
        String test_date = sc.nextLine();

        System.out.print("Enter glucose level: ");
        double glucose = sc.nextDouble();

        System.out.print("Enter protein level: ");
        double protein = sc.nextDouble();

        System.out.print("Enter device id: ");
        int device_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter reagent information: ");
        String reagent = sc.nextLine();

        Patient p1 = new Patient(patient_id, patient_name, age);

        TestStrip t1 = new TestStrip(
            strip_id, test_date, glucose, protein
        );

        DiagnosticDevice d1 = new DiagnosticDevice(
            device_id, reagent
        );

        Patient p2 = new Patient(p1);
        TestStrip t2 = new TestStrip(t1);
        DiagnosticDevice d2 = new DiagnosticDevice(d1);

        System.out.println("\nOriginal Patient:");
        p1.display_patient();

        System.out.println("\nCopied Patient:");
        p2.display_patient();

        System.out.println("\nOriginal Test Strip:");
        t1.display_test();

        System.out.println("\nCopied Test Strip:");
        t2.display_test();

        System.out.println("\nOriginal Diagnostic Device:");
        d1.display_device();

        System.out.println("\nCopied Diagnostic Device:");
        d2.display_device();

        sc.close();
    }
}
```

### Output:

#### Sample Output

```text
PS C:\Users\Public\Probz\Code\xp> javac .\Main.java
PS C:\Users\Public\Probz\Code\xp> java .\Main.java 
error: can't find main(String[]) method in class: Patient
PS C:\Users\Public\Probz\Code\xp> java .\Main      
Error: Could not find or load main class .\Main
Caused by: java.lang.ClassNotFoundException: /\Main
PS C:\Users\Public\Probz\Code\xp> java Main
Enter patient id: 1
Enter patient name: alex
Enter age: 20
Enter strip id: 100
Enter test date: 29/08/26
Enter glucose level: 15
Enter protein level: 25
Enter device id: 200
Enter reagent information: gluc

Original Patient:
Patient ID: 1
Patient Name: alex
Age: 20

Copied Patient:
Patient ID: 1
Patient Name: alex
Age: 20

Original Test Strip:
Strip ID: 100
Test Date: 29/08/26
Glucose: 15.0
Protein: 25.0

Copied Test Strip:
Strip ID: 100
Test Date: 29/08/26
Glucose: 15.0
Protein: 25.0

Original Diagnostic Device:
Device ID: 200
Reagent: gluc

Copied Diagnostic Device:
Device ID: 200
Reagent: gluc
PS C:\Users\Public\Probz\Code\xp> 
```

### Outcome:

The program successfully demonstrates **default, parameterized, and copy constructors**. It initializes Patient, Test Strip, and Diagnostic Device objects and creates copies of existing objects using copy constructors.

### Conclusion:

The experiment successfully demonstrates the use of different types of constructors in Java. It provides practical understanding of **object initialization, parameterized constructors, default constructors, and copying object data** in a urine test strip diagnostic system.