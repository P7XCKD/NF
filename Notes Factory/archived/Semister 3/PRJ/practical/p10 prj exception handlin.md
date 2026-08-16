illegal exception
divide by zero 
null exception

use all 5 keywords
try
throw
throws
catch
finally
***
v1
```java

class ThrowsDemo {

    static void throwOne() throws IllegalAccessException {
        System.out.println("Inside throwOne.");
        throw new IllegalAccessException("demo");
    }

    static void demoproc() {
        try {
            throw new NullPointerException("demo");
        } catch (NullPointerException e) {
            System.out.println("Caught inside demoproc");
            throw e;
        }
    }

    public static void main(String[] args) {
        try {
            throwOne();
        } catch (IllegalAccessException e) {
            System.out.println("Caught: " + e);
        }

        try {
            demoproc();
        } catch (NullPointerException e) {
            System.out.println("Recaught:" + e);
        }

        try {
            int a = args.length;
            System.out.println("a = " + a);
            int b = 42 / a;
            int[] c = new int[4];
            c[69] = 99;
        } catch (ArithmeticException e) {
            System.out.println("Divide by 0: " + e);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index out of bounds: " + e);
        } finally {
            System.out.println("This will be executed regardless of whether an exception occurs or not.");
        }

        System.out.println("Rest of the code...");
    }
}


``` 
artist version
***
```java
class Duck {
    static void throwOne() throws IllegalAccessException {
        System.out.println("Inside throwOne.");
        throw new IllegalAccessException("demo");
    }

    public static void main(String[] args) {
        try {
            throwOne();
        } catch (IllegalAccessException e) {
            System.out.println("Caught: " + e);
        }

        try {
            int a = args.length;
            System.out.println("a = " + a);
            int b = 42 / a;
            int[] c = new int[4];
            c[69] = 99;
            
            String str = null;
            int length = str.length();
            
        } catch (ArithmeticException e) {
            System.out.println("Divide by 0: " + e);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index out of bounds: " + e);
        } catch (NullPointerException e) {
            System.out.println("Null pointer exception: " + e);
        } finally {
            System.out.println("This will be executed regardless of whether an exception occurs or not.");
        }

        System.out.println("Rest of the code...");
    }
}
