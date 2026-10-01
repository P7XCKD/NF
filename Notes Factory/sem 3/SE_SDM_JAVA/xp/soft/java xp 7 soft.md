
<p>
    <span style="float:left;">
        <h3> Java Experiment 7
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Aim:

Develop modular Java applications using packages and interfaces to implement abstraction and code reusability.

### Objective:

1. To understand the use of packages in Java.
2. To create a modular healthcare application.
3. To create separate packages for patient, diagnostic, and report modules.
4. To define and use an interface for diagnostic analysis.
5. To implement the `DiagnosticAnalyzer` interface using a test module.
6. To understand abstraction and code reusability using packages and interfaces.

### Software Used:

- Java Development Kit (JDK)
- Visual Studio Code
- Command Prompt / Terminal
- Java Compiler (`javac`)

### Theory:

Java packages are used to organize classes into separate modules and provide code reusability.

In this experiment, packages such as `patient`, `diagnostic`, and `report` are created for a modular healthcare application. The `patient` package contains the `Patient` class for storing patient details. The `diagnostic` package contains the `DiagnosticAnalyzer` interface and `BloodTest` class. The `BloodTest` class implements the `DiagnosticAnalyzer` interface. The `report` package contains the `Report` class for displaying patient details and diagnostic results.

### Program:

#### Patient.java

```java
package patient;

public class Patient {
    public int patient_id;
    public String patient_name;

    public Patient(int patient_id, String patient_name) {
        this.patient_id = patient_id;
        this.patient_name = patient_name;
    }
}
````

#### DiagnosticAnalyzer.java

```java
package diagnostic;

public interface DiagnosticAnalyzer {
    void analyze();
}
```

#### BloodTest.java

```java
package diagnostic;

public class BloodTest implements DiagnosticAnalyzer {
    public void analyze() {
        System.out.println("Blood Test Analysis Completed");
    }
}
```

#### Report.java

```java
package report;

import patient.Patient;
import diagnostic.BloodTest;

public class Report {
    public void display(Patient p, BloodTest b) {
        System.out.println("Patient ID: " + p.patient_id);
        System.out.println("Patient Name: " + p.patient_name);
        b.analyze();
    }
}
```

#### xp7.java

```java
import java.util.Scanner;
import patient.Patient;
import diagnostic.BloodTest;
import report.Report;

public class xp7 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter Patient ID: ");
        int patient_id = sc.nextInt();

        sc.nextLine();

        System.out.print("Enter Patient Name: ");
        String patient_name = sc.nextLine();

        Patient p = new Patient(patient_id, patient_name);
        BloodTest b = new BloodTest();
        Report r = new Report();

        r.display(p, b);
    }
}
```

### Output:

```powershell
PS D:\A5EV5C> cd .\patient\
PS D:\A5EV5C\patient> javac .\Patient.java
PS D:\A5EV5C\patient> cd ..
PS D:\A5EV5C> cd .\diagnostic\
PS D:\A5EV5C\diagnostic> javac .\DiagnosticAnalyzer.java
PS D:\A5EV5C\diagnostic> cd ..
PS D:\A5EV5C> cd .\diagnostic\
PS D:\A5EV5C\diagnostic> javac .\BloodTest.java
.\BloodTest.java:3: error: cannot find symbol
public class BloodTest implements DiagnosticAnalyzer {
                                  ^
  symbol: class DiagnosticAnalyzer
1 error
PS D:\A5EV5C\diagnostic> javac -cp .. .\BloodTest.java
PS D:\A5EV5C\diagnostic> cd ..
PS D:\A5EV5C> cd .\report\
PS D:\A5EV5C\report> javac .\Report.java
.\Report.java:3: error: package patient does not exist
import patient.Patient;
              ^
.\Report.java:4: error: package diagnostic does not exist
import diagnostic.BloodTest;
                 ^
.\Report.java:7: error: cannot find symbol
    public void display(Patient p, BloodTest b) {
                        ^
  symbol:   class Patient
  location: class Report
.\Report.java:7: error: cannot find symbol
    public void display(Patient p, BloodTest b) {
                                   ^
  symbol:   class BloodTest
  location: class Report
4 errors
PS D:\A5EV5C\report> javac -cp .. .\Report.java
PS D:\A5EV5C\report> cd ..
PS D:\A5EV5C> javac .\xp7.java
PS D:\A5EV5C> java .\xp7
Error: Could not find or load main class .\xp7
Caused by: java.lang.ClassNotFoundException: /\xp7
PS D:\A5EV5C> java .\xp7.java
Enter Patient ID: 1
Enter Patient Name: probz
Patient ID: 1
Patient Name: probz
Blood Test Analysis Completed
PS D:\A5EV5C>
```
### Outcome:

The program successfully implements a modular healthcare application using packages and interfaces.

### Conclusion:

The experiment successfully demonstrates abstraction and code reusability using Java packages and interfaces.