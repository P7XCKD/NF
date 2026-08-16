Q3
a)
```java
class Employee {
    private String code;
    private String name;

    public Employee(String code, String name) {
        this.code = code;
        this.name = name;
    }

    public String getCode() {
        return code;
    }

    public String getName() {
        return name;
    }
}

class DailyWages extends Employee {
    private double rate_per_hour;
    private int hours_worked;

    public DailyWages(String code, String name, double rate_per_hour, int hours_worked) {
        super(code, name);
        this.rate_per_hour = rate_per_hour;
        this.hours_worked = hours_worked;
    }

    public void calc() {
        double wages = rate_per_hour * hours_worked;
        if (hours_worked > 40) {
            wages += (hours_worked - 40) * 0.5 * rate_per_hour;
        }
        System.out.println("Wages: " + wages);
    }
}

class Permanent extends Employee {
    private String id;
    private double basic_salary;

    public Permanent(String code, String name, String id, double basic_salary) {
        super(code, name);
        this.id = id;
        this.basic_salary = basic_salary;
    }

    public void calc() {
        double da = 0.77 * basic_salary;
        double hra = 0.46 * basic_salary;
        double gross_salary = basic_salary + da + hra;
        double net_salary = gross_salary - (0.05 * gross_salary);
        System.out.println("Net Salary: " + net_salary);
    }
}

public class Main {
    public static void main(String[] args) {
        DailyWages dw = new DailyWages("E001", "John Doe", 50, 45);
        dw.calc();

        Permanent perm = new Permanent("E002", "Jane Smith", "P123", 50000);
        perm.calc();
    }
}
```
***

b)
```java
class ElectricityBill {
    private int consumer_no;
    private String name;
    private int units_consumed;

    public ElectricityBill(int consumer_no, String name, int units_consumed) {
        this.consumer_no = consumer_no;
        this.name = name;
        this.units_consumed = units_consumed;
    }

    public int getConsumerNo() {
        return consumer_no;
    }

    public String getName() {
        return name;
    }

    public int getUnitsConsumed() {
        return units_consumed;
    }

    public void setConsumerNo(int consumer_no) {
        this.consumer_no = consumer_no;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setUnitsConsumed(int units_consumed) {
        this.units_consumed = units_consumed;
    }

    public double calcBill() {
        double charges = 0;
        if (units_consumed <= 250) {
            charges = units_consumed * 0.60;
        } else if (units_consumed <= 350) {
            charges = 200 + (units_consumed - 250) * 0.80;
        } else if (units_consumed <= 450) {
            charges = 350 + (units_consumed - 350) * 1.00;
        } else {
            charges = 480 + (units_consumed - 450) * 1.50;
        }

        charges += charges * 0.09; // Adding 9% CGST
        return charges;
    }
}

public class Main {
    public static void main(String[] args) {
        ElectricityBill[] consumers = new ElectricityBill[3];
        consumers[0] = new ElectricityBill(101, "John Doe", 240);
        consumers[1] = new ElectricityBill(102, "Jane Smith", 360);
        consumers[2] = new ElectricityBill(103, "Alice Brown", 470);

        double totalBillAmount = 0;
        for (ElectricityBill consumer : consumers) {
            double bill = consumer.calcBill();
            System.out.println("Consumer No: " + consumer.getConsumerNo() + ", Name: " + consumer.getName() + ", Bill Amount: " + bill);
            totalBillAmount += bill;
        }

        System.out.println("Total Bill Amount: " + totalBillAmount);
    }
}
```