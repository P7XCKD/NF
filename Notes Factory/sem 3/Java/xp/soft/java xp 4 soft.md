
<p>
    <span style="float:left;">
        <h3> Java Experiment 4
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Aim:

To develop a Java program using arrays to store and analyze multi-parameter urine test results.

### Objective:

1. To understand the concept of one-dimensional arrays in Java.

2. To store urine test parameters and their values using arrays.

3. To compare test values with their normal minimum and maximum ranges.

4. To identify and count abnormal parameters.

5. To calculate the average value of the tested parameters.

6. To determine the severity level based on the number of abnormal parameters.

### Software Used:

- Java Development Kit (JDK)

- Visual Studio Code

- Command Prompt / Terminal

- Java Compiler (`javac`)

### Theory:

An **array** is a collection of elements of the same data type stored under a single variable name. Arrays are useful for storing and processing multiple related values efficiently.

A **one-dimensional array** stores data in a linear sequence and can be accessed using an index. In this experiment, arrays are used to store urine analyte names, their test values, and their normal minimum and maximum values.

The program compares each actual test value with its corresponding normal range. If a value is below the minimum or above the maximum, it is considered **abnormal**. The program then counts the abnormal parameters, calculates the average value, and determines the severity level based on the number of abnormal parameters.

### Program:

```java
import java.util.Scanner;

public class xp4 {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String[] analytes = {"glucose", "protien", "ph"};

        double[] values = new double[3];
        double[] normal_min = new double[3];
        double[] normal_max = new double[3];

        System.out.println("urine test analysis");

        for(int i = 0; i < 3; i++) {

            System.out.print("\nEnter normal minimum value for "
                    + analytes[i] + ": ");
            normal_min[i] = sc.nextDouble();

            System.out.print("Enter normal maximum value for "
                    + analytes[i] + ": ");
            normal_max[i] = sc.nextDouble();

            System.out.print("Enter " + analytes[i] + " value: ");
            values[i] = sc.nextDouble();
        }

        int abnormal_count = 0;
        double total = 0;

        for(int i = 0; i < 3; i++) {

            total = total + values[i];

            if(values[i] < normal_min[i] ||
               values[i] > normal_max[i]) {
                abnormal_count++;
            }
        }

        double average = total / 3;

        String severity;

        if(abnormal_count == 0) {
            severity = "Normal";
        }
        else if(abnormal_count == 1) {
            severity = "Mild";
        }
        else {
            severity = "Severe";
        }

        System.out.println("\nUrine Test Report");

        for(int i = 0; i < 3; i++) {

            System.out.println(analytes[i] + ": " + values[i]);

            if(values[i] < normal_min[i] ||
               values[i] > normal_max[i]) {
                System.out.println("Status: Abnormal");
            }
            else {
                System.out.println("Status: Normal");
            }
        }

        System.out.println("\nAnalysis");
        System.out.println("Total Parameters Tested: 3");
        System.out.println("Abnormal Parameter Count: "
                + abnormal_count);
        System.out.println("Average Value: " + average);
        System.out.println("Severity Level: " + severity);

        sc.close();
    }
}
````

### Output:

#### Sample Output

```text
PS D:\A5EV5C> javac .\xp4.java
PS D:\A5EV5C> java xp4
urine test analysis

Enter normal minimum value for glucose: 5
Enter normal maximum value for glucose: 10
Enter glucose value: 7

Enter normal minimum value for protien: 3
Enter normal maximum value for protien: 5
Enter protien value: 2

Enter normal minimum value for ph: 5
Enter normal maximum value for ph: 7
Enter ph value: 11

Urine Test Report
glucose: 7.0
Status: Normal
protien: 2.0
Status: Abnormal
ph: 11.0
Status: Abnormal

Analysis
Total Parameters Tested: 3
Abnormal Parameter Count: 2
Average Value: 6.666666666666667
Severity Level: Severe
PS D:\A5EV5C>
```

### Outcome:

The program successfully uses **one-dimensional arrays** to store and analyze urine test parameters. It identifies abnormal values, counts abnormal parameters, calculates the average value, and determines the severity level.

### Conclusion:

The experiment successfully demonstrates the use of **one-dimensional arrays in Java** for storing, processing, and analyzing multiple urine test parameters. The program also provides practical understanding of comparing values with normal ranges and generating an analysis report.

