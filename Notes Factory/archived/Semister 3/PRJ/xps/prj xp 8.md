


# Experiment 8:
**Aim**: To create packages with access control and import them in appropriate classes.

## Theory:

### Package in Java:
A package is a namespace that groups related classes, interfaces, and sub-packages together. It helps in organizing and managing Java code by avoiding naming conflicts and controlling access with access modifiers. Packages also make it easier to maintain and understand large codebases.

### Built-in Packages in Java:
Java comes with several built-in packages that provide a wide range of pre-written classes and interfaces. Key examples include:
- `java.lang`: Contains fundamental classes such as `String`, `Math`, and `Object`. Automatically imported in every Java program.
- `java.util`: Provides utility classes like `ArrayList`, `HashMap`, and `Date` for data structures and utility functions.
- `java.io`: Includes classes for input and output operations, such as `File`, `InputStream`, and `BufferedReader`.

### User-defined Package in Java:
You can create your own packages to group related classes and interfaces that you develop. This enhances code organization and modularity.
## Steps to Create a User-defined Package in Java:


1. **Create a Directory**: Define a directory structure that matches your package name. For instance, a package named `com.example.utils` would be in a directory path `com/example/utils`.
2. **Place Source Files**: Put your Java source files in the appropriate directory.
3. **Declare the Package**: At the beginning of each source file, use the `package` keyword followed by the package name to declare that the file belongs to that package. For example:
   
```java
   package com.example.utils;
```

## Procedure:
wap package program

**File: `Demo.java`**
```java
package datademo;

public class Demo {
    public void show() {
        System.out.println("Hi Everyone");
    }

    public void view() {
        System.out.println("Hello");
    }
}
```

**File: `Demo2.java`**
```java
import datademo.Demo;

public class Demo2 {
    public static void main(String[] args) {
        Demo d = new Demo();
        d.show();
        d.view();
    }
}
```

### compilation / output
```plaintext
PS C:\A5EV5C> javac -d . Demo.java
PS C:\A5EV5C> javac Demo2.java
PS C:\A5EV5C> java Demo2
```

```plaintext
Hi Everyone
Hello
```


***



**File Name: `arith.java`**
```java
package ari;

public class arith {

    public void add(int a, int b) {
        int c = a + b;
        System.out.println("Sum is " + c);
    }

    public void sub(int a, int b) {
        int c = a - b;
        System.out.println("Difference is " + c);
    }

    public void div(int a, int b) {
        if (b != 0) {
            int c = a / b;
            System.out.println("Quotient is " + c);
        } else {
            System.out.println("Error: Division by zero");
        }
    }

    public void mul(int a, int b) {
        int c = a * b;
        System.out.println("Product is " + c);
    }

    public void mod(int a, int b) {
        if (b != 0) {
            int c = a % b;
            System.out.println("Remainder is " + c);
        } else {
            System.out.println("Error: Modulus by zero");
        }
    }
}
```

**File Name: `testarith.java`**
```java
import ari.arith;
import java.util.Scanner;

class testarith {

    public static void main(String[] args) {
        arith a = new arith();
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter Number 1:");
        int n1 = sc.nextInt();
        System.out.println("Enter Number 2:");
        int n2 = sc.nextInt();

        a.add(n1, n2);
        a.sub(n1, n2);
        a.div(n1, n2);
        a.mul(n1, n2);
        a.mod(n1, n2);

        sc.close();
    }
}
```

OUTPUT

```plaintext
PS C:\A5EV5C> javac -d . arith.java
PS C:\A5EV5C> javac testarith.java
PS C:\A5EV5C> java testarith
Enter Number 1:
10
Enter Number 2:
5
Sum is 15
Difference is 5
Quotient is 2
Product is 50
Remainder is 0

```

## Conclusion:
hence we successfully created packages with access control and imported them in appropriate classes.
***
## -PR7BZ
