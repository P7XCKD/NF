## Experiment No. 3

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

    // Default constructor
    Patient() {
        patient_id = 0;
        patient_name = "Unknown";
        age = 0;
    }

    // Parameterized constructor
    Patient(int patient_id, String patient_name, int age) {
        this.patient_id = patient_id;
        this.patient_name = patient_name;
        this.age = age;
    }

    // Copy constructor
    Patient(Patient p) {
        this.patient_id = p.patient_id;
        this.patient_name = p.patient_name;
        this.age = p.age;
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

    // Default constructor
    TestStrip() {
        strip_id = 0;
        test_date = "Not Set";
        glucose = 0;
        protein = 0;
    }

    // Parameterized constructor
    TestStrip(int strip_id, String test_date,
              double glucose, double protein) {
        this.strip_id = strip_id;
        this.test_date = test_date;
        this.glucose = glucose;
        this.protein = protein;
    }

    // Copy constructor
    TestStrip(TestStrip t) {
        this.strip_id = t.strip_id;
        this.test_date = t.test_date;
        this.glucose = t.glucose;
        this.protein = t.protein;
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

    // Default constructor
    DiagnosticDevice() {
        device_id = 0;
        reagent = "Not Set";
    }

    // Parameterized constructor
    DiagnosticDevice(int device_id, String reagent) {
        this.device_id = device_id;
        this.reagent = reagent;
    }

    // Copy constructor
    DiagnosticDevice(DiagnosticDevice d) {
        this.device_id = d.device_id;
        this.reagent = d.reagent;
    }

    public void display_device() {
        System.out.println("Device ID: " + device_id);
        System.out.println("Reagent: " + reagent);
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

        System.out.print("Enter Strip ID: ");
        int strip_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter Test Date: ");
        String test_date = sc.nextLine();

        System.out.print("Enter Glucose Level: ");
        double glucose = sc.nextDouble();

        System.out.print("Enter Protein Level: ");
        double protein = sc.nextDouble();

        System.out.print("Enter Device ID: ");
        int device_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter Reagent Information: ");
        String reagent = sc.nextLine();

        // Parameterized objects
        Patient p1 = new Patient(patient_id, patient_name, age);

        TestStrip t1 = new TestStrip(
            strip_id, test_date, glucose, protein
        );

        DiagnosticDevice d1 = new DiagnosticDevice(
            device_id, reagent
        );

        // Copy objects
        Patient p2 = new Patient(p1);
        TestStrip t2 = new TestStrip(t1);
        DiagnosticDevice d2 = new DiagnosticDevice(d1);

        System.out.println("\n--- Original Patient ---");
        p1.display_patient();

        System.out.println("\n--- Copied Patient ---");
        p2.display_patient();

        System.out.println("\n--- Original Test Strip ---");
        t1.display_test();

        System.out.println("\n--- Copied Test Strip ---");
        t2.display_test();

        System.out.println("\n--- Original Diagnostic Device ---");
        d1.display_device();

        System.out.println("\n--- Copied Diagnostic Device ---");
        d2.display_device();

        sc.close();
    }
}
```

### Output:

#### Sample Output

```text
PS D:\A5EV5C> javac Main.java
PS D:\A5EV5C> java Main.java

Enter Patient ID: 1
Enter Patient Name: Alex
Enter Age: 19
Enter Strip ID: 101
Enter Test Date: 26-08-2026
Enter Glucose Level: 11
Enter Protein Level: 12
Enter Device ID: 501
Enter Reagent Information: Glucose Reagent

--- Original Patient ---
Patient ID: 1
Patient Name: Alex
Age: 19

--- Copied Patient ---
Patient ID: 1
Patient Name: Alex
Age: 19

--- Original Test Strip ---
Strip ID: 101
Test Date: 26-08-2026
Glucose: 11.0
Protein: 12.0

--- Copied Test Strip ---
Strip ID: 101
Test Date: 26-08-2026
Glucose: 11.0
Protein: 12.0

--- Original Diagnostic Device ---
Device ID: 501
Reagent: Glucose Reagent

--- Copied Diagnostic Device ---
Device ID: 501
Reagent: Glucose Reagent

PS D:\A5EV5C>
```

### Outcome:

The program successfully demonstrates **default, parameterized, and copy constructors**. It initializes Patient, Test Strip, and Diagnostic Device objects and creates copies of existing objects using copy constructors.

### Conclusion:

The experiment successfully demonstrates the use of different types of constructors in Java. It provides practical understanding of **object initialization, parameterized constructors, default constructors, and copying object data** in a urine test strip diagnostic system.