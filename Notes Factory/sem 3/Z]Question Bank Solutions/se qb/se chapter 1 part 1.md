# SE Chapter 1 Notes (part 1)


# Part 1: Java Fundamentals

## 1. Variables and Constants

### Variable

A variable is a named memory location used to store data. Its value can change during program execution.

Syntax:

```java
dataType variableName = value;
```

Example:

```java
int age = 21;
System.out.println(age);

age = 22;
System.out.println(age);
```

Output:

```text
21
22
```

Here, `age` is a variable of type `int`. Its value changes from `21` to `22`.

### Constant

A constant is a value that cannot be reassigned after initialization. In Java, the `final` keyword is used to declare a constant.

Example:

```java
final double PI = 3.14;
System.out.println(PI);
```

Output:

```text
3.14
```

Trying to assign `PI = 3.15;` later will cause a compilation error.

### Difference between Variable and Constant

| Variable | Constant |
|---|---|
| Value can change | Value cannot be reassigned |
| Declared using a data type | Declared using a data type and `final` |
| Example: `int age = 21;` | Example: `final int MAX = 100;` |

## 2. Primitive and Non-Primitive Data Types

A data type specifies the kind of value a variable can store.

### Primitive Data Types

Java has eight primitive data types.

| Data type | Used for | Example |
|---|---|---|
| `byte` | Small integers | `byte a = 10;` |
| `short` | Short integers | `short a = 100;` |
| `int` | Integers | `int age = 21;` |
| `long` | Large integers | `long n = 1000L;` |
| `float` | Decimal numbers | `float x = 2.5f;` |
| `double` | Decimal numbers with greater precision | `double pi = 3.14;` |
| `char` | A single character | `char grade = 'A';` |
| `boolean` | True or false | `boolean pass = true;` |

Remember:
- `char` uses single quotes, such as `'A'`.
- `String` uses double quotes, such as `"Dev"`.
- `float` literals normally use the suffix `f`, such as `2.5f`.

### Non-Primitive Data Types

Non-primitive types include classes, objects, arrays, interfaces and `String`. They represent objects or references to objects.

Example:

```java
String name = "Dev";
int[] marks = {80, 85, 90};
```

Here, `name` is a `String` reference and `marks` is an array reference.

| Primitive | Non-primitive |
|---|---|
| Eight built-in types | Includes classes, arrays, `String`, etc. |
| Stores a value directly | Variables generally hold references to objects |
| Cannot call methods on a primitive value | Objects can provide methods |
| Example: `int a = 10;` | Example: `String s = "Hello";` |

# Part 2: Object-Oriented Programming (OOP)

## 3. Class

A **class** is a user-defined blueprint or prototype from which objects are created. It defines the properties and methods common to objects of that type.

### Components of a Class Declaration

1. **Modifier:** Controls access, such as `public` or default access.
2. **Class name:** Conventionally starts with a capital letter.
3. **Superclass:** Optional parent class specified using `extends`.
4. **Interfaces:** Optional interfaces specified using `implements`.
5. **Body:** Contains variables, constructors and methods within `{ }`.

General syntax:

```java
class ClassName {
    // Variables
    // Methods
}
```

Example:

```java
class Student {
    int rollNo;
    String name;

    void study() {
        System.out.println("Studying");
    }
}
```

Here, `Student` is a class, `rollNo` and `name` are instance variables, and `study()` is a method.

**Naming convention:** Class names usually begin with an uppercase letter, such as `Student` or `Animal`. This is a convention, not a strict Java requirement.

## 4. Object

An **object** is an instance of a class and is a basic unit of object-oriented programming. Objects represent entities and interact by invoking methods.

An object has three main characteristics:

1. **State:** The properties or data of an object.
2. **Behavior:** The actions represented by its methods.
3. **Identity:** What distinguishes one object from another.

### Example of a Class and Object

```java
class Student {
    int rollNo;
    String name;

    void display() {
        System.out.println("Roll No: " + this.rollNo);
        System.out.println("Name: " + this.name);
    }
}

class Main {
    public static void main(String[] args) {
        Student s1 = new Student();

        s1.rollNo = 62;
        s1.name = "Dev";

        s1.display();
    }
}
```

Output:

```text
Roll No: 62
Name: Dev
```

Explanation:
- `Student` is the class.
- `new Student()` creates a new object.
- `s1` is a reference variable referring to that object.
- `s1.rollNo` and `s1.name` set the object's state.
- `s1.display()` calls its method.
- `this.rollNo` and `this.name` refer to the current object's instance variables.

The `this` keyword is useful for referring to the current object. In this example, it is valid but not strictly necessary because the parameter names do not conflict with the instance variable names.

### The `main()` Method

```java
public static void main(String[] args)
```

- `public`: Accessible to the Java runtime.
- `static`: Can be called without creating a `Main` object.
- `void`: Does not return a value.
- `main`: The program's entry-point method.
- `String[] args`: An array of strings that can receive command-line arguments.

`String[] args` is correct. `String s[]` is also valid Java array declaration syntax, but it declares a single `String` variable named `s` as an array, not a variable named `args`. Java is case-sensitive, so `String` must start with a capital `S`.

## 5. Interface

An **interface** specifies what a class must do, rather than how it must do it. It defines a contract that implementing classes follow.

Interface methods declared without a body are implicitly `public abstract`.

### Important Points

- An interface is declared using `interface`.
- A class implements an interface using `implements`.
- A class can implement multiple interfaces.
- A class can extend only one direct superclass.
- A concrete implementing class must implement all inherited abstract methods, unless it is declared `abstract`.
- Interface variables are implicitly `public static final`.

### Example

```java
interface Vehicle {
    void start();
}

class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car starts with a key.");
    }
}

class Main {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.start();
    }
}
```

Output:

```text
Car starts with a key.
```

Explanation:
1. `Vehicle` declares the `start()` method.
2. `Car implements Vehicle` means `Car` agrees to provide the required method.
3. `public void start()` supplies the method body.
4. `Vehicle v = new Car();` stores a `Car` object in a `Vehicle` reference.
5. `v.start()` executes the `Car` implementation.

The `public` modifier is necessary because the interface method is implicitly public, and an implementing method cannot reduce its visibility.

## 6. Inheritance and Polymorphism

### Inheritance

Inheritance allows a child class to acquire and extend the properties and methods of a parent class.

Syntax:

```java
class Child extends Parent {
    // Additional code
}
```

Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```

A `Dog` object can use both `eat()` and `bark()`.

### Polymorphism

Polymorphism means **one name or reference can take multiple forms**.

Two important forms in Java are:
- Compile-time polymorphism: method overloading.
- Runtime polymorphism: method overriding.

# Part 3: Arrays and Variables

## 7. Arrays

An **array** is a collection of elements of the same data type, referred to by a common name.

### Important Points about Java Arrays

1. Arrays are objects in Java.
2. Arrays are dynamically allocated when created.
3. Array elements are ordered and indexed, starting from `0`.
4. The `length` property gives the number of elements.
5. The size of an array is fixed after creation.
6. The array size must be specified using an `int` value.
7. An array can be declared as a local variable, an instance field or a static field.
8. The direct superclass of an array type is `Object`.

### Array Declaration

```java
int[] marks;
```

This declares an array reference. It does not create the array itself.

### Array Creation

```java
marks = new int[5];
```

This creates an integer array with five elements, initially set to `0`.

### Declaration and Initialization Together

```java
int[] marks = {80, 85, 42, 90};
```

This creates an array containing four values.

### Accessing Array Elements

```java
System.out.println(marks[0]);
System.out.println(marks[2]);
```

Output:

```text
80
42
```

Remember that indexing begins at `0`, so the last index is `length - 1`.

### Traversing an Array Using a Loop

```java
class Main {
    public static void main(String[] args) {
        int[] marks = {80, 85, 42, 90};

        for (int i = 0; i < marks.length; i++) {
            System.out.println(marks[i]);
        }
    }
}
```

Output:

```text
80
85
42
90
```

Here, `marks.length` is `4`. The loop prints elements at indices `0`, `1`, `2` and `3`.

Trying to access `marks[4]` would cause an `ArrayIndexOutOfBoundsException`.

## 8. Types of Variables

Java commonly classifies variables into three types: local, instance and static.

### A. Local Variable

A local variable is declared inside a method, constructor or block. It can only be accessed within that scope.

```java
class Student {
    void display() {
        int marks = 90;
        System.out.println(marks);
    }
}
```

Here, `marks` is a local variable.

A local variable does not receive a default value automatically; it must be initialized before use.

### B. Instance Variable

An instance variable is declared inside a class but outside methods and without `static`. Each object has its own copy.

```java
class Student {
    int rollNo;
}
```

Example:

```java
Student s1 = new Student();
Student s2 = new Student();

s1.rollNo = 62;
s2.rollNo = 63;
```

The two objects have separate `rollNo` values.

### C. Static Variable

A static variable is declared using `static`. It belongs to the class and is shared among its instances.

```java
class Student {
    static String college = "KJSIT";
}
```

It can be accessed using the class name:

```java
System.out.println(Student.college);
```

### Complete Comparison

| Local variable | Instance variable | Static variable |
|---|---|---|
| Declared inside a method/block | Declared in a class, outside methods | Declared in a class using `static` |
| Belongs to a scope | Belongs to an object | Belongs to a class |
| No automatic default value | Receives a default value | Receives a default value |
| Exists within its scope | Associated with each object | One shared class variable |

Example combining all three:

```java
class Student {
    int rollNo = 62;                 // Instance
    static String college = "KJSIT"; // Static

    void display() {
        int marks = 90;              // Local
        System.out.println(marks);
    }
}
```

# Part 4: Control Statements

## 9. Control Statements

Control statements determine the order in which program statements are executed.

The topics in your notes are `if`, nested `if`, `switch`, `break`, `continue`, and iteration statements.

### A. If Statement

An `if` statement executes a block only when its condition is true.

Syntax:

```java
if (condition) {
    // Statements
}
```

Example:

```java
int age = 20;

if (age >= 18) {
    System.out.println("Eligible to vote");
}
```

Output:

```text
Eligible to vote
```

### B. If-Else Statement

Executes one block if the condition is true and another if it is false.

```java
int marks = 35;

if (marks >= 40) {
    System.out.println("Pass");
} else {
    System.out.println("Fail");
}
```

Output:

```text
Fail
```

### C. Nested If

A nested `if` is an `if` statement placed inside another `if` statement.

```java
int age = 21;

if (age >= 18) {
    if (age >= 21) {
        System.out.println("Eligible");
    }
}
```

Output:

```text
Eligible
```

The inner condition is checked only if the outer condition is true.

### D. Switch Statement

A `switch` statement selects a block of code based on the value of an expression.

```java
int day = 2;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;

    case 2:
        System.out.println("Tuesday");
        break;

    default:
        System.out.println("Invalid day");
}
```

Output:

```text
Tuesday
```

Important keywords:
- `case`: Specifies a possible value.
- `break`: Exits the switch after a matching case executes.
- `default`: Executes when no case matches.

Without `break`, execution may continue into subsequent cases. This is called fall-through.

### E. Break Statement

The `break` statement terminates the nearest enclosing loop or switch.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        break;
    }
    System.out.println(i);
}
```

Output:

```text
1
2
```

When `i` becomes `3`, the loop terminates.

### F. Continue Statement

The `continue` statement skips the remaining statements in the current loop iteration and proceeds to the next iteration.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;
    }
    System.out.println(i);
}
```

Output:

```text
1
2
4
5
```

The value `3` is skipped, but the loop continues.

### Break vs. Continue

| `break` | `continue` |
|---|---|
| Terminates the loop | Skips the current iteration |
| Control moves outside the loop | Control proceeds to the next iteration |
| Used in loops and switches | Used in loops |

## 10. Iteration Statements (Loops)

An iteration statement repeats a block of code while a condition allows it.

### A. For Loop

A `for` loop is commonly used when the number of iterations is known.

Syntax:

```java
for (initialization; condition; update) {
    // Statements
}
```

Example:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

Output:

```text
1
2
3
4
5
```

Execution order:
1. Initialize `i = 1`.
2. Check `i <= 5`.
3. Execute the loop body.
4. Update `i++`.
5. Repeat until the condition becomes false.

### B. While Loop

A `while` loop checks the condition before executing the body. It may execute zero times if the condition is initially false.

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

Output:

```text
1
2
3
4
5
```

### C. Do-While Loop

A `do-while` loop checks the condition after executing the body. Therefore, it executes at least once.

```java
int i = 1;

do {
    System.out.println(i);
    i++;
} while (i <= 5);
```

Output:

```text
1
2
3
4
5
```

Notice the semicolon after `while (i <= 5);`.

### Loop Comparison

| For loop | While loop | Do-while loop |
|---|---|---|
| Condition checked before body | Condition checked before body | Condition checked after body |
| Initialization, condition and update are together in the header | Initialization and update are usually separate | Initialization and update are usually separate |
| May execute zero times | May execute zero times | Executes at least once |

**Common mistake:** Forgetting to update the loop variable in a `while` or `do-while` loop can create an infinite loop.

# Part 5: Java Methods

## 11. Methods

A **method** is a block of code that performs a specific task. It allows code to be reused instead of writing the same statements repeatedly.

A method and a function are similar concepts; in Java, functions are normally defined as methods inside classes or interfaces.

### Syntax

```java
returnType methodName(parameters) {
    // Method body
}
```

Components:
- `returnType`: The type of value returned, such as `int`, `double` or `String`. Use `void` if no value is returned.
- `methodName`: The name used to call the method.
- `parameters`: Optional input values.
- `method body`: The statements executed when the method is called.
- `return`: Sends a result back to the caller when the method has a non-`void` return type.

### A. Method Without Parameters and Without a Return Value

```java
void greet() {
    System.out.println("Hello");
}
```

Call it using:

```java
greet();
```

Output:

```text
Hello
```

### B. Method with Parameters

Parameters allow a method to receive input.

```java
void greet(String name) {
    System.out.println("Hello " + name);
}
```

Call:

```java
greet("Dev");
```

Output:

```text
Hello Dev
```

Here, `name` is the parameter and `"Dev"` is the argument passed to it.

### C. Method with a Return Value

```java
int add(int a, int b) {
    return a + b;
}
```

Call:

```java
int result = add(10, 20);
System.out.println(result);
```

Output:

```text
30
```

The method calculates the sum and returns it to the caller.

### Complete Method Example

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }
}

class Main {
    public static void main(String[] args) {
        Calculator c = new Calculator();

        int result = c.add(10, 20);
        System.out.println(result);
    }
}
```

Output:

```text
30
```

## 12. Method Overloading

**Method overloading** is a feature in Java that allows a class to have multiple methods with the same name but different parameter lists.

It is an example of **compile-time polymorphism**.

Methods can be overloaded by changing:
1. The number of parameters.
2. The types of parameters.
3. The order of parameter types.

### Example 1: Different Number of Parameters

```java
class Calculator {
    void add(int a, int b) {
        System.out.println(a + b);
    }

    void add(int a, int b, int c) {
        System.out.println(a + b + c);
    }
}
```

Calls:

```java
Calculator c = new Calculator();

c.add(10, 20);
c.add(10, 20, 30);
```

Output:

```text
30
60
```

The compiler chooses the appropriate `add()` method based on the arguments.

### Example 2: Different Parameter Types

```java
class Display {
    void show(int a) {
        System.out.println("Integer: " + a);
    }

    void show(String a) {
        System.out.println("String: " + a);
    }
}
```

Calls:

```java
Display d = new Display();

d.show(10);
d.show("Hello");
```

Output:

```text
Integer: 10
String: Hello
```

### Example 3: Different Order of Parameter Types

```java
class Display {
    void show(int a, String b) {
        System.out.println(a + " " + b);
    }

    void show(String a, int b) {
        System.out.println(a + " " + b);
    }
}
```

Both methods have two parameters, but their types appear in a different order.

### Important: Return Type Alone Is Not Enough

This is invalid:

```java
int add(int a, int b) {
    return a + b;
}

double add(int a, int b) {
    return a + b;
}
```

Both methods have the same name and exactly the same parameter types. Only their return types differ.

Java cannot overload methods based only on return type, so this produces a compilation error.

A valid alternative is to change the parameter list:

```java
int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}
```

Now the methods have different parameter types.

## 13. Method Overriding

**Method overriding** occurs when a child class provides its own implementation of an inherited instance method from the parent class.

It supports **runtime polymorphism**.

### Example

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
    }
}
```

Output:

```text
Dog barks
```

Explanation:
- `Animal` is the parent class.
- `Dog` is the child class.
- `extends Animal` establishes inheritance.
- `@Override` indicates that `Dog` overrides the inherited method.
- `Animal a = new Dog();` creates a `Dog` object and stores its reference in an `Animal` variable.
- `a.sound()` executes the overridden method in `Dog`.

### One Reference, Different Objects

Assume `Cat extends Animal` and overrides `sound()` to print `"Cat meows"`.

```java
Animal a;

a = new Dog();
a.sound();

a = new Cat();
a.sound();
```

Output:

```text
Dog barks
Cat meows
```

The reference variable `a` is declared only once. It first refers to a `Dog` object and then to a `Cat` object.

You can also use two separate variables:

```java
Animal a = new Dog();
a.sound();

Animal b = new Cat();
b.sound();
```

Both approaches are valid.

## 14. Difference Between Method Overloading and Method Overriding

| Method overloading | Method overriding |
|---|---|
| Same method name, different parameter lists | Same method signature for the overridden method |
| Can occur in the same class | Occurs between parent and child classes |
| Inheritance is not required | Inheritance is required |
| Compile-time polymorphism | Runtime polymorphism |
| Method selected using the arguments and applicable method rules | Overridden instance method selected based on the actual object |
| Commonly described as static binding | Uses dynamic binding |

Remember:
- **Overloading:** Same name, different parameters.
- **Overriding:** Same method, new implementation in the child class.

## 15. Static Binding and Dynamic Binding

**Binding** means deciding which method implementation will execute.

### A. Static Binding

Static binding means the method is selected at compile time. In introductory Java examples, it is associated with method overloading.

```java
class Calculator {
    void add(int a, int b) {
        System.out.println("Two integers");
    }

    void add(int a, int b, int c) {
        System.out.println("Three integers");
    }
}
```

Calls:

```java
Calculator c = new Calculator();

c.add(10, 20);
c.add(10, 20, 30);
```

Output:

```text
Two integers
Three integers
```

The compiler selects the method based on the number and types of arguments.

### B. Dynamic Binding

Dynamic binding means the overridden instance method is selected at runtime based on the actual object's class.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

Call:

```java
Animal a = new Dog();
a.sound();
```

Output:

```text
Dog barks
```

Although the reference type is `Animal`, the actual object is `Dog`, so Java runs `Dog`'s overridden method.

### Static vs. Dynamic Binding

| Static binding | Dynamic binding |
|---|---|
| Associated with overloading in basic examples | Associated with overriding |
| Method selection at compile time | Overridden method selection at runtime |
| Based on argument types and method applicability | Based on the actual object |
| Also called early binding | Also called late binding |

**Easy memory trick:** Static binding = compiler decides. Dynamic binding = actual object decides at runtime.

Note: Static methods, private methods and constructors do not participate in runtime overriding in the same way as ordinary overridable instance methods. The table above is the standard introductory comparison for overloading and overriding.

***
# Part 6: AI Use Cases (just read this section)

These five use cases are based on the descriptions you provided. The examples below are simplified for quick exam revision.

## 16. Climate Intelligence for Heatwave Monitoring, Prediction and Early Warning

**Meaning:** An AI-based system that uses weather data, IoT sensors and climate models to monitor temperatures, predict heatwaves and provide early warnings.

### Objectives
- Monitor real-time temperature and environmental conditions.
- Predict upcoming heatwaves using AI and machine learning.
- Send early warnings to communities and authorities.
- Reduce heat-related health risks and economic losses.
- Support disaster management and climate adaptation.

**Example:** If AI predicts extreme temperatures over the next few days, the system can issue an early heatwave warning.

## 17. AI Irrigation Advisory System for Sugarcane

**Meaning:** A system that uses AI and IoT-based sensors to determine when and how much water a sugarcane crop needs.

### Objectives
- Monitor soil moisture, temperature, humidity and rainfall.
- Predict the crop's water requirements.
- Recommend the right time and amount of irrigation.
- Reduce water wastage.
- Improve crop health and productivity.
- Reduce energy and labour costs.
- Provide alerts to farmers through mobile or web applications.
- Use historical and environmental data for irrigation planning.

**Example:** If sensors detect dry soil, the system recommends irrigation to the farmer.

## 18. Urine Test Strip Reader Using Colorimetry

**Meaning:** A diagnostic system that uses color sensors or digital imaging, potentially combined with AI, to analyze color changes on urine test strips and help interpret test results.

### Working
1. A urine sample reacts with chemical pads on a test strip.
2. The pads change color.
3. A camera or color sensor captures the colors.
4. The system analyzes the color variations.
5. It provides test readings for interpretation.

**Applications:** Supporting the detection and monitoring of conditions related to diabetes, kidney disorders, urinary tract infections and liver problems.

**Example:** A camera captures a test strip, and the system analyzes its colored pads to produce readings.

*Note: The system supports testing; clinical interpretation and diagnosis may require a healthcare professional.*

## 19. AI-Based Inter-Satellite Data Routing for PocketQube Missions

**Meaning:** An AI-based communication system that selects suitable routes for sending data between small satellites and ground stations.

### Working
- Multiple small satellites communicate through inter-satellite links.
- AI analyzes available communication routes.
- Data is routed according to availability and transmission priorities.
- The system can select another available route if a connection becomes unavailable.

### Applications
- Space research missions.
- Disaster monitoring networks.

**Example:** If one satellite link becomes unavailable, the system can choose another available route to transfer data.

## 20. AI-Enabled Micro-Channel Battery Thermal Management for EVs

**Meaning:** An AI-based cooling system that monitors electric vehicle battery temperatures and adjusts cooling to help maintain a suitable temperature.

### Working
1. Temperature sensors continuously monitor battery conditions.
2. AI analyzes real-time thermal data.
3. The system predicts temperature changes.
4. It adjusts coolant flow and cooling intensity.
5. The battery temperature is managed to reduce overheating and uneven heating.

### Benefits
- Helps maintain battery performance.
- Can reduce battery degradation.
- Helps manage overheating-related safety risks.
- Improves cooling efficiency.

**Example:** If the battery becomes too hot, the controller increases cooling to bring its temperature toward the desired range.

# Part 7: Final Quick Revision

## Important Definitions

| Term | One-line definition |
|---|---|
| Variable | Named storage whose value can change. |
| Constant | Value that cannot be reassigned, declared using `final`. |
| Primitive type | One of Java's eight built-in data types. |
| Non-primitive type | A type such as a class, array or `String`. |
| Class | Blueprint used to create objects. |
| Object | An instance of a class. |
| Interface | Contract specifying methods a class must implement. |
| Array | Fixed-size collection of elements of the same type. |
| Local variable | Variable declared within a method or block. |
| Instance variable | Variable associated with each object. |
| Static variable | Variable shared at the class level. |
| Method | Reusable block of code that performs a task. |
| Overloading | Same method name with different parameter lists. |
| Overriding | Child class provides its own implementation of an inherited method. |
| Static binding | Method selection at compile time in the usual overloading example. |
| Dynamic binding | Overridden method selection at runtime based on the actual object. |

## Common Exam Mistakes

- Use `String`, not `string`.
- Use `String[] args` in the standard Java entry-point method.
- Class names conventionally start with uppercase letters.
- Array indexing begins at `0`.
- Use `array.length`, not `array.length()`.
- Use `implements` for interfaces and `extends` for class inheritance.
- Use `final` to prevent reassignment of a constant.
- Overloading requires different parameter lists; changing only the return type is insufficient.
- In overriding, an implementing method cannot reduce the visibility of the inherited method.
- Declare a reference variable once before reassigning it to another object.
- A `do-while` loop executes at least once.
- `break` exits a loop; `continue` skips the current iteration.

## Revision Checklist

- [ ] Primitive and non-primitive data types with examples
- [ ] Class and object program that prints object properties
- [ ] Interface example using `implements`
- [ ] Array declaration, traversal and length
- [ ] Local, instance and static variable examples
- [ ] `if`, nested `if` and `switch` programs
- [ ] `for`, `while` and `do-while` loops
- [ ] `break` and `continue` output questions
- [ ] Method with parameters and return value
- [ ] Method overloading with two valid examples
- [ ] Method overriding with parent and child classes
- [ ] Static vs. dynamic binding output questions
- [ ] Five AI use cases and their objectives



**Simple study tip:** First learn the definitions, then practise writing each short Java program without looking at the notes, and finally predict its output.
