> [!attention] These DO NOT include:
•Trees
•Linked Lists
•Infix to postfix
Since I hv skipped those topics
> Contents

### INSERTION IN ARRAY:
```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("The elements of the array are:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    int element;
    printf("Enter the element to insert: ");
    scanf("%d", &element);

    int position;
    printf("Enter the position to insert the element (0 to %d): ", n);
    scanf("%d", &position);

    if (position < 0 || position > n) {
        printf("Invalid position to insert\n");
        return 1;
    }
    else {
        for (i = n; i > position; i--) {
            arr[i] = arr[i - 1];
        }

        arr[position] = element;

        n++;
    }
    printf("Array after insertion:\n");
    for (i = 0; i < n; i++) {
        printf("%d \n", arr[i]);
    }

    return 0;
}

```
### DELETION IN ARRAY:
```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("The elements of the array are:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    int index;
    printf("Enter the index to delete (0 to %d): ", n - 1);
    scanf("%d", &index);

    if (index < 0 || index >= n) {
        printf("Invalid index to delete\n");
        return 1;
    }
    else {
        for (i = index; i < n - 1; i++) {
            arr[i] = arr[i + 1];
        }

        n--;
    }
    printf("Array after deletion:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```

### LINEAR SEARCH:
```c
#include <stdio.h>

int main() {
    int size, target, found = 0;

    printf("Enter the number of elements: ");
    scanf("%d", &size);

    int arr[size];

    printf("Enter %d elements:\n", size);
    for (int i = 0; i < size; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Enter the element to search: ");
    scanf("%d", &target);

    printf("Element found at indices: ");
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            printf("%d ", i);
            found = 1;
        }
    }

    if (!found) {
        printf("Element not found in the array");
    }

    printf("\n");
    return 0;
}
```



### BINARY SEARCH:
```c
#include <stdio.h>

int main() {
    int n, i, j, temp, search, found = 0;

    printf("enter the no of elements : ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements :\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    printf("sorted array in ascending order:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    printf("enter the element to search: ");
    scanf("%d", &search);

    int left = 0, right = n - 1, mid;
    while (left <= right) {
        mid = left + (right - left) / 2;

        if (arr[mid] == search) {
            printf(" found %d at index %d\n", search, mid);
            found++;
            break;
        } else if (arr[mid] < search) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    if (found == 0) {
        printf("element %d not found \n", search);
    }

    return 0;
}
```

### BUBBLE SORT:
```c
#include <stdio.h>

int main() {
    int n, i, j, temp;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    printf("Sorted array in ascending order:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```

### SELECTION SORT:
```c
#include <stdio.h>

int min(int *arr,int k,int n);

void main() {
    int n, k, i, temp, loc;

    printf("Enter number of the elements : ");
    scanf("%d", &n);
    int arr[n];

    for (i = 1; i <= n; i++) {
        printf("Enter %d element :", i);
        scanf("%d", &arr[i]);
    }

    for (k = 1; k <= n; k++) {
        loc = min(arr, k, n);
        temp = arr[loc];
        arr[loc] = arr[k];
        arr[k] = temp;
        for (i = 1; i <= n; i++) {
            printf("%d , ", arr[i]);
        }
        printf("\n");
    }
    printf("Sorted Array : \n");
    for (i = 1; i <= n; i++) {
        printf("%d ,", arr[i]);
    }
}

int min(int *arr, int k, int n) {
    int min = k;
    for (min = k; k <= n; k++) {
        if (arr[min] > arr[k]) {
            min = k;
        }
    }
    return min;
}
```
### INSERTION SORT:
```c
#include <stdio.h>

int main() {
    int a[100], n, k, temp, ptr;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        printf("Enter Element[%d]: ", i);
        scanf("%d", &a[i]);
    }

    for (k = 1; k < n; k++) {
        temp = a[k];
        ptr = k - 1;

        while (ptr >= 0 && temp < a[ptr]) {
            a[ptr + 1] = a[ptr];
            ptr = ptr - 1;
        }
        a[ptr + 1] = temp;

        printf("Elements after Pass %d:\n", k);
        for (int u = 0; u < n; u++) {
            printf("%d ", a[u]);
        }
        printf("\n");
    }

    printf("Sorted array:\n");
    for (int j = 0; j < n; j++) {
        printf("Element %d is: %d\n", j, a[j]);
    }

    return 0;
}
```

### QUICK SORT:
```c
#include <stdio.h>
#include <conio.h>
#define size 100
int partition(int a[], int beg, int end);
void quick_sort(int a[], int beg, int end);
void main()
{
    int arr[size], i, n;
    printf("\n Enter the number of elements in the array: ");
    scanf("%d", &n);
    printf("\n Enter the elements of the array: ");
    for(i=0;i<n;i++)
    {
        scanf("%d", &arr[i]);
    }
    quick_sort(arr, 0, n-1);
    printf("\n The sorted array is: \n");
    for(i=0;i<n;i++)
        printf(" %d\t", arr[i]);
    getch();
}
int partition(int a[], int beg, int end)
{
    int left, right, temp, loc, flag;
    loc = left = beg;
    right = end;
    flag = 0;
    while(flag != 1)
    {
        while((a[loc] <= a[right]) && (loc!=right))
            right--;
        if(loc==right)
            flag =1;
        else if(a[loc]>a[right])
        {
            temp = a[loc];
            a[loc] = a[right];
            a[right] = temp;
            loc = right;
        }
        if(flag!=1)
        {
            while((a[loc] >= a[left]) && (loc!=left))
                left++;
            if(loc==left)
                flag =1;
            else if(a[loc] <a[left])
            {
                temp = a[loc];
                a[loc] = a[left];
                a[left] = temp;
                loc = left;
            }
        }
    }
    return loc;
}
void quick_sort(int a[], int beg, int end)
{
    int loc;
    if(beg<end)
    {
        loc = partition(a, beg, end);
        quick_sort(a, beg, loc-1);
        quick_sort(a, loc+1, end);
    }
}
```


### stack push pop and peep
```c
#include <stdio.h>

int stack[100], top = -1, n, MAX = 100;

void push();
void pop();
void show();
void peep();

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

    while (choice != 5) {
        printf("\nChoose one from the below options...\n");
        printf("1. Push\n2. Pop\n3. Show\n4. Peep\n5. Exit\n");
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
                peep();
                break;
            case 5:
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

void peep() {
    if (top == -1) {
        printf("No elements to display.\n");
    } else {
        printf("Top element is: %d\n", stack[top]);
    }
}

void show() {
    if (top == -1) {
        printf("Stack is empty.\n");
    } else {
        printf("Stack elements are:\n");
        for (int i = 0; i <= top; i++) {
            printf("%d\n", stack[i]);
        }
    }
}

```

### queue insertion and deletion 

```c
#include <stdio.h>

int main() {
    int q[100];
    int n;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    int front = 0;
    int rear = 0;
    int io;
    int item;

    for (int i = 0; i < 10000; i++) {
        printf("What do you want to do? 1 for insert 2 for delete\n");
        scanf("%d", &io);
        switch (io) {
            case 1:
                item = 0;
                printf("What do you want to insert?\n");
                scanf("%d", &item);
                if ((front == 1 && rear == n) || front == rear + 1) {
                    printf("Queue overflow.\n");
                } else {
                    if (front == 0) {
                        front = front + 1;
                        rear = rear + 1;
                        q[rear] = item;
                    } else if (rear == n) {
                        rear = 1;
                        q[rear] = item;
                    } else {
                        rear = rear + 1;
                        q[rear] = item;
                    }
                }
                for (int i = 1; i <= n; i++) {
                    printf("Element %d: %d\n", i, q[i]);
                }
                break;
            case 2:
                item = q[front];
                if (front == 0) {
                    printf("Queue underflow.\n");
                } else {
                    if (front == rear) {
                        front = 0;
                        rear = 0;
                    } else if (front == n) {
                        front = 1;
                    } else {
                        front = front + 1;
                    }
                }
                for (int i = front; i <= n; i++) {
                    printf("Element %d: %d\n", i, q[i]);
                }
                break;
            default:
                printf("Invalid choice.\n");
                break;
        }
    }
}

```