
<p>
    <span style="float:left;">
        <h3> Java Experiment 5
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Aim:

To develop a Java program for managing patient records using Vector and Collections.

### Objective:

1. To understand the use of Vector in Java.
2. To store and manage patient records.
3. To add and display patient records.
4. To search patient records using ID or name.
5. To sort patient records by name.
6. To update existing patient records.
7. To understand the use of Collections for data management.

### Software Used:

- Java Development Kit (JDK)
- Visual Studio Code
- Command Prompt / Terminal
- Java Compiler (`javac`)

### Theory:

Vector is a dynamic collection in Java that can store multiple objects and automatically increases its size when required.

In this experiment, a Vector is used to store Patient objects containing patient ID, name, test history, and diagnostic remarks. The program provides operations such as adding, displaying, searching, sorting, and updating patient records.

The Collections class is used to sort the patient records alphabetically according to the patient name.

### Program:

```java
import java.util.Vector;
import java.util.Collections;
import java.util.Scanner;

class Patient {
    String id, name, testHistory, remarks;

    Patient(String id, String name, String testHistory, String remarks) {
        this.id = id;
        this.name = name;
        this.testHistory = testHistory;
        this.remarks = remarks;
    }

    void display_patient() {
        System.out.println("id: " + id);
        System.out.println("name: " + name);
        System.out.println("test: " + testHistory);
        System.out.println("remarks: " + remarks);
    }
}

public class xp5 {

    static Vector<Patient> patients = new Vector<>();
    static Scanner sc = new Scanner(System.in);

    static String input(String msg) {
        System.out.print(msg);
        return sc.nextLine();
    }

    static void add_patient() {
        String id = input("enter patient id: ");
        String name = input("enter patient name: ");
        String testHistory = input("enter test history: ");
        String remarks = input("enter diagnostic remarks: ");

        patients.add(new Patient(id, name, testHistory, remarks));
        System.out.println("patient added");
    }

    static void display_all() {
        if (patients.isEmpty()) {
            System.out.println("no records");
            return;
        }

        System.out.println("\npatient records");

        for (Patient p : patients) {
            p.display_patient();
            System.out.println();
        }
    }

    static void search_patient() {
        String search = input("enter patient id or name: ");

        for (Patient p : patients) {
            if (p.id.equalsIgnoreCase(search) ||
                p.name.toLowerCase().contains(search.toLowerCase())) {

                System.out.println("\nrecord found");
                p.display_patient();
                return;
            }
        }

        System.out.println("record not found");
    }

    static void sort_patients() {
        Collections.sort(patients,
                (a, b) -> a.name.compareToIgnoreCase(b.name));

        System.out.println("records sorted");
        display_all();
    }

    static void update_patient() {
        String id = input("enter patient id to update: ");

        for (Patient p : patients) {
            if (p.id.equalsIgnoreCase(id)) {

                p.name = input("enter new name: ");
                p.testHistory = input("enter new test history: ");
                p.remarks = input("enter new remarks: ");

                System.out.println("record updated");
                return;
            }
        }

        System.out.println("patient id not found");
    }

    public static void main(String[] args) {

        while (true) {

            System.out.println("\n1.add 2.display 3.search 4.sort 5.update 6.exit");

            String choice = input("enter choice: ");

            switch (choice) {
                case "1":
                    add_patient();
                    break;

                case "2":
                    display_all();
                    break;

                case "3":
                    search_patient();
                    break;

                case "4":
                    sort_patients();
                    break;

                case "5":
                    update_patient();
                    break;

                case "6":
                    System.out.println("exited program");
                    return;

                default:
                    System.out.println("invalid choice");
            }
        }
    }
}
````

### Output:



```text
PS C:\Users\Public\Probz\Code\xp> javac .\xp5.java
PS C:\Users\Public\Probz\Code\xp> java .\xp5
Error: Could not find or load main class .\xp5
Caused by: java.lang.ClassNotFoundException: /\xp5
PS C:\Users\Public\Probz\Code\xp> java xp5

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 1
enter patient id: 100
enter patient name: arnold
enter test history: 09/09/2026
enter diagnostic remarks: no abnomalties
patient added

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 2

patient records
id: 100
name: arnold
test: 09/09/2026
remarks: no abnomalties

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 1
enter patient id: 200
enter patient name: brian
enter test history: 10/09/2026
enter diagnostic remarks: abnomal
patient added

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 3
enter patient id or name: 200

record found
id: 200
name: brian
test: 10/09/2026
remarks: abnomal

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 4
records sorted

patient records
id: 100
name: arnold
test: 09/09/2026
remarks: no abnomalties

id: 200
name: brian
test: 10/09/2026
remarks: abnomal

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 5
enter patient id to update: 200
enter new name: william
enter new test history: 02/09/2026
enter new remarks: normal
record updated

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 2

patient records
id: 100
name: arnold
test: 09/09/2026
remarks: no abnomalties

id: 200
name: william
test: 02/09/2026
remarks: normal

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 4
records sorted

patient records
id: 100
name: arnold
test: 09/09/2026
remarks: no abnomalties

id: 200
name: william
test: 02/09/2026
remarks: normal

1.add 2.display 3.search 4.sort 5.update 6.exit
enter choice: 6
exited program

PS C:\Users\Public\Probz\Code\xp>
```

### Outcome:

The program successfully manages patient records using Vector and performs add, display, search, sort, and update operations.

### Conclusion:

The experiment successfully demonstrates the use of **Vector and Collections in Java** for storing and managing patient records efficiently.