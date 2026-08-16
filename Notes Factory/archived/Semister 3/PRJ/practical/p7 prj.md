#### single inheritance
```java
 class Person
{
    protected  String name;
    protected int age;

    public Person(String name ,int age){
       this.name=name;
       this.age=age;

    }
public void display(){
System.out.println("name:"+name+"age:"+ age);
}
}
 class faculty extends Person
 {
private final int id;
private final String department;
private final String designation;
private final int salary;

public faculty(String name,int age,String department, int id , String designation,int salary){
    super(name ,age);
    this.department= department;
    this.id= id;
    
    this.designation=designation;
    this.salary=salary;
}
@Override
public void display(){
    super.display();
System.out.println("faculty ID: " + id +  "department: " + department + "designation: "+ designation + "salary: " + salary );
}

public static void main(String[] args) {

    
    faculty s=new faculty("probz ",19,"cse ",20 ,"da ma^(n)ager ",7);

    System.out.println("\n Info:");
    s.display();
   
        
}
 }

```
output:
name: probz
age: 19
faculty id: 20
designation: da ma^(n)ager
salary: 7
***

#### multi level inheritence

```java
public class Multilevelinheritance
{
    public static void main (String[] args)
    {
        Manager mgr = new Manager("DEV",18,"S1A027","Programmer");
        mgr.display();
    }
}
class Person
{
    String name;
    int age;

    public Person(String name, int age)
    {
        this.name=name;
        this.age=age;
    }
    public void display()
    {
        System.out.println("Name" + name);
        System.out.println("Age" + age);
    }
}
class Employee extends Person
{
    String EmployeeId;
    public Employee(String name, int age, String EmployeeId)
    {
        super(name,age);
        this.EmployeeId=EmployeeId;
    }
    public void display()
    {
        super.display();
        System.out.println("Employee ID " + EmployeeId);
    }
}
class Manager extends Employee
{
    String department;
     public Manager(String name, int age, String EmployeeId, String department)
     {
        super(name,age,EmployeeId);
        this.department = department;
     }
     public void display()
     {
        super.display();
        System.out.println("Department" + department);
     }
}

```

***
roses are red, violets are blue
I forgot the name of the code
now what should you do

```java
public class Multilevelinheritance1
{
    public static void main (String[] args)
    {
        department dep = new department("SBMP","A5evfc","056",57);
        dep.display();
    }
}
class university
{
    String name; 

    public university(String name)
    {
        this.name=name;
    }
    public void display()
    {
        System.out.println("Name" + name);
    }
}
class college extends university
{
    String collegeId;
    public college(String name, String collegeId)
    {
        super(name);
        this.collegeId=collegeId;
    }
    public void display()
    {
        super.display();
        System.out.println("college ID " + collegeId);
    }
}
class department extends college
{
    String department;
    String departmentId;
    int totstaff;
     public department(String name, String departmentId, String department, int totstaff)
     {
        super(name,department);
        this.departmentId = departmentId;
        this.department=department;
        this.totstaff=totstaff;
     }
     @Override
     public void display()
     {
        super.display();
        System.out.println("DepartmentId" + departmentId);
        System.out.println("Department" + department);
        System.out.println("Total Staff" + totstaff);
     }
***
}


```

***
hierachical 
```java
public class Multilevelinheritance2
{
    public static void main (String[] args)
    {
        faculty fac = new  faculty("Harshal" , 18,"324324");
        fac.display();
    }
}
class person
{
    String name;
    int age;
    public person(String name, int age)
    {
        this.name=name;
        this.age=age;
    }
    public void display()
    {
        System.out.println("Name: " + name);
        System.out.println("Age:" + age);
    }
}
class student extends person
{
    String studentId;
    public student(String name, int age, String studentId)
    {
        super(name,age);
        this.studentId=studentId;
    }
    @Override
    public void display()
    {
        super.display();
        System.out.println("StudentId" + studentId);
    }
}
class faculty extends student
{
    String facultyId;
    public faculty(String name, int age, String facultyId)
    {
        super(name,age,facultyId);
        this.facultyId=facultyId;
    }
    @Override
    public void display()
    {
        super.display();
        System.out.println("FacultyId" + facultyId);

    }
}

```
1276
***
dynamic method dispatch
```java
public class Dispatch
{
    public static void main(String[] args)
    {
        A a = new A();
        B d = new B();
        C c = new C();
        A ref;
        ref = a;
        ref.m1();
        ref = d;
        ref.m1();
        ref = c;
        ref.m1();
    }
}class A
{
    void m1()
    {
        System.out.println("Inside A's m1 method");
    }
}
class B extends A
{
    void m1()
    {
        System.out.println("Inside B's m1 method");
    }
}
class C extends A
{
    void m1()
    {
        System.out.println("Inside C's m1 method");
    }
}

public class Dispatch
{
    public static void main(String[] args)
    {
        A a = new A();
        B d = new B();
        C c = new C();
        A ref;
        ref = a;
        ref.m1();
        ref = d;
        ref.m1();
        ref = c;
        ref.m1();
    }
}class A
{
    void m1()
    {
        System.out.println("Inside A's m1 method");
    }
}
class B extends A
{
    void m1()
    {
        System.out.println("Inside B's m1 method");
    }
}
class C extends A
{
    void m1()
    {
        System.out.println("Inside C's m1 method");
    }
}

```

***

another hierachical

```java

public class Dispatch1
{
    public static void main(String[] args)
    {
        employee e = new employee();
        programmer p = new programmer();
        manager m = new manager();
        employee ref;
        ref = e;
        ref.work();
        ref = p;
        ref.work();
        ref = m;
        ref.work();
    }
}
class employee
{
    void work()
    {
        System.out.println("Employee's Working ");
    }
}
class programmer extends employee
{
    void work()
    {
        System.out.println("Programmer's Working");
    }
}
class manager extends employee
{
    void work()
    {
        System.out.println("Manager's Working");
    }
}


```