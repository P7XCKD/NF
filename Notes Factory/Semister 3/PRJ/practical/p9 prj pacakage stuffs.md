arith.java
```java
package ari;

public class arith {

    public void add(int a, int b) {
    int c = a+b;
    System.out.println("Sum is " + c);
    }

    public void sub(int a, int b) {
        int c = a-b;
        System.out.println("Sum is " + c);
    }

    public void div(int a, int b) {
        int c = a/b;
    System.out.println("Sum is " + c);
    }

    public void mul(int a, int b) {
        int c = a*b;
        System.out.println("Sum is " + c);
    }

    public void mod(int a, int b) {
        int c = a%b;
        System.out.println("Sum is " + c);
    }
}
```
testarith.java
```java
import ari.arith;
import java.util.Scanner;

class testarith {

    public static void main(String[] args) {
        arith a = new arith();
        Scanner sc = new Scanner(System.in);
        for (int i = 0; i <= 10000; i++) {
            System.out.println("Enter Number 1:");
            int n1 = sc.nextInt();
            System.out.println("\n Enter Number 2:");
            int n2 = sc.nextInt();
            System.out.println("Enter Number for action:");
            System.out.println("1 for add");
            System.out.println("2 for sub");
            System.out.println("3 for div");
            System.out.println("4 for mul");
            System.out.println("5 for mod");
            System.out.println("6 for exit");
            int s = sc.nextInt();
            switch (s) {
                case 1:
                    a.add(n1, n2);
                    break;
                case 2:
                    a.sub(n1, n2);
                    break;
                case 3:
                    a.div(n1, n2);
                    break;
                case 4:
                    a.mul(n1, n2);
                    break;
                case 5:
                    a.mod(n1, n2);
                    break;
                case 6:
                    if (s == 6) {
                        break;
                    }
                    break;
                default:
                    System.out.println("\n Invalid");
                    break;
            }
        }
    }
}


```
***

interface

```java
interface Bank
{
    float rateOfInterest();
}
class SBI implements Bank
{
    public float rateOfInterest(){return 9.15f;}
}
class PNB implements Bank
{
    public float rateOfInterest(){return 9.7f;}
}
class TestInteference2
{
    public static void main(String[] args)
    {
        Bank b=new SBI();
        System.out.println("ROI" + b.rateOfInterest());
    }
}

```
