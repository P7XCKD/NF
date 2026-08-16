interface
file name duck.java
```java
interface Printable {

    void print();
}

class duck implements Printable {

    public void print() {
        System.out.println("hello");
    }

    public static void main(String[] args) {
        duck k = new duck();
        k.print();
    }
}


```
![image](.attachments/6c7006636b9142545ed1571f865c2fc6a5d4fc24.png) 