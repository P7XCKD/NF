12-24 marks
```c
#include <stdio.h>

int factorial(int n) {
    return (n == 0) ? 1 : n * factorial(n - 1);
}

int fibonacci(int n) {
    return (n <= 1) ? n : fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int num = 5;
    printf("Factorial of %d is %d\n", num, factorial(num));
    printf("Fibonacci of %d is %d\n", num, fibonacci(num));
    return 0;
}
```
***
| **Symbol Scanned** | **Postfix Result (P)**    | **Stack**        |
|--------------------|---------------------------|------------------|
| `(`                |                           | `(`              |
| `A`                | `A`                       | `(`              |
| `–`                | `A`                       | `( -`            |
| `(`                | `A`                       | `( - (`          |
| `B`                | `A B`                     | `( - (`          |
| `/`                | `A B`                     | `( - ( /`        |
| `C`                | `A B C`                   | `( - ( /`        |
| `)`                | `A B C /`                 | `( -`            |
| `*`                | `A B C /`                 | `( - *`          |
| `D`                | `A B C / D`               | `( - *`          |
| `+`                | `A B C / D *`             | `( +`            |
| `E`                | `A B C / D * E`           | `( +`            |
| `)`                | `A B C / D * E +`         |                  |
| `*`                | `A B C / D * E +`         | `*`              |
| `F`                | `A B C / D * E + F`       | `*`              |
| `%`                | `A B C / D * E + F`       | `* %`            |
| `G`                | `A B C / D * E + F G`     | `* %`            |
|                    | `A B C / D * E + F G % *` |                  |

***
