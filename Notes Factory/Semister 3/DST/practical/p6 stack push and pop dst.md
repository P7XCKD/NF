```c
#include <stdio.h>

int stack[100];
int top = -1;
int n;
int MAX = 100;

void push();
void pop();
void show();

int main()
{
    int choice = 0;

    printf("Enter the number of elements in the stack (max %d): ", MAX);
    scanf("%d", &n);

    if (n > MAX) {
        printf("The number of elements cannot exceed %d.\n", MAX);
        return 1;
    }

    printf("Enter %d elements to initialize the stack:\n", n);
    for (int i = 0; i < n; i++) {
        int value;
        printf("Element %d: ", i + 1);
        scanf("%d", &value);
        stack[++top] = value;
    }

    while (choice != 4) {
        printf("\nChoose one from the below options...\n");
        printf("1. Push\n2. Pop\n3. Show\n4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                push();
                break;
            case 2:
                pop();
                break;
            case 3:
                show();
                break;
            case 4:
                printf("Exiting...\n");
                break;
            default:
                printf("Please enter a valid choice.\n");
        }
    }

    return 0;
}

void push() {
    int val;

    if (top >= MAX - 1) {
        printf("Overflow: Stack is full.\n");
    } else {
        printf("Enter the value to push: ");
        scanf("%d", &val);
        stack[++top] = val;
    }
}

void pop() {
    if (top == -1) {
        printf("Underflow: Stack is empty.\n");
    } else {
        printf("Popped value: %d\n", stack[top--]);
    }
}

void show() {
    if (top == -1) {
        printf("Stack is empty.\n");
    } else {
        printf("Stack elements are:\n");
        for (int i = top; i >= 0; i--) {
            printf("%d\n", stack[i]);
        }
    }
}
```