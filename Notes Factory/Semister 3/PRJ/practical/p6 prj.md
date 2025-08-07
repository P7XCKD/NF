```java
import java.util.*;

class person {

    String nameP;
    int age;
    String City;

    public person(String n) {
        nameP = n;
    }

    public void display() {
        System.out.println("Name is " + nameP);
        System.out.println("Age is " + age);
        System.out.println("City is " + City);
    }
}

class studen extends person {

    int rollno;
    int sapid;
    static String classname;

    static {
        classname = "3A";
        System.out.println("Static block");
    }

    public studen(String na, int rn, int sp) {
        super(na);
        rollno = rn;
        sapid = sp;
    }

    @Override
    public void display() {
        super.display();
        System.out.println("Roll no is " + rollno);
        System.out.println("Sap id is " + sapid);
        System.out.println("Classroom is " + classname);
    }
}

class student {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        studen[] s1 = new studen[5];
        for (int i = 0; i <= 5; i++) {
            System.out.println("Enter Name");
            String nume = sc.next();
            System.out.println("Enter Rollno");
            int roll = sc.nextInt();
            System.out.println("Enter SAP");
            int SAP = sc.nextInt();
            s1[i] = new studen(nume, roll, SAP);
            s1[i].display();
        }
    }
}

```