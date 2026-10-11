# Java Experiment 8

### Aim

Develop robust Java applications using exception handling, custom exceptions, and input validation techniques.

### Problem Statement

Implement Secure Patient Data Validation using Exception Handling.

### Objective

-   Validate patient ID, age, and analyte values.
    
-   Handle invalid inputs and missing data.
    
-   Handle divide-by-zero and array errors.
    
-   Implement custom medical exceptions.
    

### Software Used

-   JDK
    
-   VS Code
    
-   Command Prompt / PowerShell
    

### Theory

Exception handling is used to handle runtime errors without stopping the program suddenly. Java provides `try`, `catch`, `throw`, `throws`, and `finally` for exception handling. Custom exceptions can be created for application-specific errors.

In this experiment:

-   `try` contains code that may cause an error.
    
-   `catch` handles the error.
    
-   `throw` generates a custom exception.
    
-   `throws` declares an exception.
    
-   `finally` executes after exception handling.
    
-   `MedicalException` handles invalid patient data.
    

### Program

```java
// Experiment 8
// Aim: Develop robust Java applications using exception handling,
// custom exceptions, and input validation techniques.

// Implement Secure Patient Data Validation using Exception Handling

import java.util.Scanner;
import java.util.InputMismatchException;

public class xp8 {

    static class MedicalException extends Exception {
        MedicalException(String msg) {
            super(msg);
        }
    }

    static void check(int id, String name, int age, double analyte)
            throws MedicalException {

        if (id <= 0)
            throw new MedicalException("Invalid Patient ID");

        if (name.isEmpty())
            throw new MedicalException("Patient Name is missing");

        if (age <= 0 || age > 120)
            throw new MedicalException("Invalid Age");

        if (analyte < 0)
            throw new MedicalException("Invalid Analyte Value");
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        try {
            System.out.print("Enter Patient ID: ");
            int id = sc.nextInt();

            sc.nextLine();

            System.out.print("Enter Patient Name: ");
            String name = sc.nextLine();

            System.out.print("Enter Age: ");
            int age = sc.nextInt();

            System.out.print("Enter Analyte Value: ");
            double analyte = sc.nextDouble();

            try {
                check(id, name, age, analyte);
                System.out.println("\nPatient data is valid.");

            } catch (MedicalException e) {
                // Custom exception
                System.out.println("Medical Error: " + e.getMessage());
            }

            System.out.println("\nPatient Report");
            System.out.println("Patient ID: " + id);
            System.out.println("Patient Name: " + name);
            System.out.println("Age: " + age);
            System.out.println("Analyte Value: " + analyte);

            try {
                int[] data = {10, 20, 30};
                System.out.println(data[5]);

            } catch (ArrayIndexOutOfBoundsException e) {
                // Array exception
                System.out.println("Array Error: Invalid index.");
            }

            try {
                int result = age / 0;
                System.out.println(result);

            } catch (ArithmeticException e) {
                // Divide by zero
                System.out.println("Arithmetic Error: Cannot divide by zero.");
            }

        } catch (InputMismatchException e) {
            // Invalid input
            System.out.println("Input Error: Enter valid values.");

        } finally {
            // Always executes
            System.out.println("Patient data validation completed.");
            sc.close();
        }
    }
}
```

### Output

**Valid Input**

```text
PS D:\A5EV5C> javac .\xp8.java                    
PS D:\A5EV5C> java .\xp8.java                    
Enter Patient ID: 100
Enter Patient Name: Arnold
Enter Age: 18
Enter Analyte Value: 45.5

Patient data is valid.

Patient Report 
Patient ID: 100
Patient Name: Arnold
Age: 18
Analyte Value: 45.5
Array Error: Invalid index.
Arithmetic Error: Cannot divide by zero.
Patient data validation completed.
PS D:\A5EV5C> java .\xp8.java
Enter Patient ID: aaaaaa
Input Error: Enter valid values.
Patient data validation completed.
PS D:\A5EV5C> java .\xp8.java
Enter Patient ID: 100
Enter Patient Name: Mark
Enter Age: 0
Enter Analyte Value: 45.5
Medical Error: Invalid Age

Patient Report 
Patient ID: 100
Patient Name: Mark
Age: 0
Analyte Value: 45.5
Array Error: Invalid index.
Arithmetic Error: Cannot divide by zero.
Patient data validation completed.
PS D:\A5EV5C> 

```
### Outcome

The Java program successfully validated patient data and handled different types of exceptions.

### Conclusion

Thus, exception handling, custom exceptions, and input validation were successfully implemented in Java.