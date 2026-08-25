## Experiment 1      
<div align="right"> Dev Mandora
Roll Number: 62 </div>

### Aim:

To write a Java program using variables, operators, and decision-making statements to analyze basic urine test parameters and classify the overall test result as **Normal** or **Abnormal**.

### Objective:

1.  To understand the use of variables in Java.
2.  To accept input from the user using the `Scanner` class.
3.  To use relational and logical operators.
4.  To implement `if-else` decision-making.
5.  To compare String values using `.equals()`.
6.  To classify the overall urine test report based on specified conditions.

### Software Used:

-   Java Development Kit (JDK)
-   Visual Studio Code
-   Command Prompt / Terminal
-   Java Compiler (`javac`)

### Theory:

Java provides fundamental programming features such as variables, operators, input/output, and control statements.

The `Scanner` class is used to accept input from the user. In this program, `double` variables are used to store glucose, protein, and pH values, while a `String` variable is used to store the blood type.

Relational operators such as `<=` and `>=` are used to check whether numerical values satisfy the specified conditions. Logical operators `&&` and `||` are used to combine multiple conditions.

The `if-else` statement determines the overall result. If all specified conditions are satisfied, the program displays **"Overall Report is Normal"**. Otherwise, it displays **"Overall Report is Abnormal, Consult a doctor"**.

> **Note:** The thresholds and blood-type condition in this program are simplified values for demonstrating Java programming concepts and are not intended for actual medical diagnosis.

### Program:
```java
import java.util.Scanner;

class xp1{
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        double glucose,protein,ph;
        String bloodtype;
        
        System.out.println("Enter the glucose level: ");
        glucose = sc.nextDouble();

        System.out.println("Enter the protein level: ");
        protein = sc.nextDouble();

        System.out.println("Enter the ph level: ");
        ph = sc.nextDouble();

        System.out.println("Enter the blood type: ");
        bloodtype = sc.next();

        if(glucose <= 50 && protein <= 50 && ph <= 7.5 && ph >= 5 && bloodtype.equals("O+") || bloodtype.equals("O-"))
         {
            System.out.println("Overall Report is Normal");
         }
        else
        {
            System.out.println("Overall Report is Abnormal, Consult a doctor");
        }
    }
}
```
### Output:

#### Sample Output 1 — Normal Result

```
PS C:\Users\HP\Desktop\A5EV5C> java .\xp1.java 
Enter the glucose level: 
40  
Enter the protein level: 
40
Enter the ph level: 
5
Enter the blood type: 
O+
Overall Report is Normal
```

#### Sample Output 2 — Abnormal Result
```
PS C:\Users\HP\Desktop\A5EV5C> java .\xp1.java
Enter the glucose level: 
40
Enter the protein level: 
40
Enter the ph level: 
5
Enter the blood type: 
AB+
Overall Report is Abnormal, Consult a doctor
PS C:\Users\HP\Desktop\A5EV5C> 

```

### Outcome:

The Java program successfully accepts glucose, protein, pH, and blood type as inputs and uses **relational operators, logical operators, String comparison, and `if-else` statements** to classify the overall test result.

### Conclusion:

The experiment successfully demonstrates the application of Java fundamentals to a simple real-world problem. The program provides practical understanding of **variables, `Scanner`, operators, String handling, and decision-making statements** in Java.