### ARRAY INSERTION OF AN ELEMENT

```c
#include <stdio.h>

int n = 0, item, pos;

void insert(int arr[], int len, int item, int pos);

void main() {
    printf("Enter the length of array: ");
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        printf("Enter number %d: ", i + 1);
        scanf("%d", &arr[i]);
    }
    printf("Enter the data element to be inserted: ");
    scanf("%d", &item);
    printf("Enter the position where you want to insert the data element: ");
    scanf("%d", &pos);
    insert(arr, n, item, pos);
}

void insert(int arr[], int len, int item, int pos) {
    int index = pos - 1;
    for (int i = len; i > index; i--) {
        arr[i] = arr[i - 1];
    }
    arr[index] = item;
    printf("\nArray after Insertion: ");
    for (int i = 0; i <= len; i++) {
        printf("%d ", arr[i]);
    }
}
```
***
### Array deletion of an element 
```c
#include <stdio.h>

int n = 0, pos;

void delete(int arr[], int len, int pos);

void main() {
    printf("Enter the length of array: ");
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        printf("Enter the element %d: ", i + 1);
        scanf("%d", &arr[i]);
    }
    printf("Enter the position at which the element needs to be deleted: ");
    scanf("%d", &pos);
    delete(arr, n, pos);
}

void delete(int arr[], int len, int pos) {
    int index = pos - 1;
    for (int i = index; i < len - 1; i++) {
        arr[i] = arr[i + 1];
    }
    printf("Array after Deletion: ");
    for (int i = 0; i < len - 1; i++) {
        printf("%d ", arr[i]);
    }
}
```

***

### linear search

  ```c
  #include <stdio.h>

int n, item;

void searchItem(int arr[], int len, int item);

void main() {
    printf("Enter the length of array: ");
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        printf("Enter number %d: ", i + 1);
        scanf("%d", &arr[i]);
    }
    printf("Enter the search element: ");
    scanf("%d", &item);
    searchItem(arr, n, item);
}

void searchItem(int arr[], int len, int item) {
    int flag = -1;
    for (int i = 0; i < len; i++) {
        if (arr[i] == item) {
            flag = i;
            break;
        }
    }
    if (flag == -1) {
        printf("No element found in the array!\n");
    } else {
        printf("Element found at position: %d\n", flag + 1);
    }
}
  ```

***
### binary search
```c
#include <stdio.h>

int n = 0, item;

void binarySearch(int arr[], int len, int item);

void main() {
    printf("Enter the length of array: ");
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        printf("Enter number %d: ", i + 1);
        scanf("%d", &arr[i]);
    }
    printf("Enter the item to be searched within the array: ");
    scanf("%d", &item);
    binarySearch(arr, n, item);
}

void binarySearch(int arr[], int len, int item) {
    int lb = 0, ub = len - 1;
    int mid;
    int flag = -1;
    
    while (lb <= ub) {
        mid = (lb + ub) / 2;
        if (arr[mid] > item) {
            ub = mid - 1;
        } else if (arr[mid] < item) {
            lb = mid + 1;
        } else {
            flag = mid;
            break;
        }
    }
    if (flag == -1) {
        printf("No element found in the array!\n");
    } else {
        printf("Element found at position %d\n", flag + 1);
    }
}

```

***
### selection sort
```c
#include <stdio.h>

int n = 0;

int min(int arr[], int len, int index);
void selectionSort(int arr[], int len);

void main() {
    printf("Enter the length of array: ");
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        printf("Enter number %d: ", i + 1);
        scanf("%d", &arr[i]);
    }
    selectionSort(arr, n);
}

int min(int arr[], int len, int index) {
    int minIndex = index;
    for (int j = index + 1; j < len; j++) {
        if (arr[j] < arr[minIndex]) {
            minIndex = j;
        }
    }
    return minIndex;
}

void selectionSort(int arr[], int len) {
    for (int i = 0; i < len - 1; i++) {
        int loc = min(arr, len, i);
        int temp = arr[i];
        arr[i] = arr[loc];
        arr[loc] = temp;
        
        printf("\nPass %d: ", i + 1);
        for (int j = 0; j < len; j++) {
            printf("%d ", arr[j]);
        }
    }

    printf("\nSorted Array: ");
    for (int i = 0; i < len; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

```

***
### quick sort
```c
#include <stdio.h>

int pass = 1;

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

void printArray(int arr[], int len) {
    printf("Pass %d: ", pass++);
    for (int i = 0; i < len; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high, int len) {
    if (low < high) {
        int pi = partition(arr, low, high);
        printArray(arr, len);
        quickSort(arr, low, pi - 1, len);
        quickSort(arr, pi + 1, high, len);
    }
}

void main() {
    int n;
    printf("Enter the length of array: ");
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        printf("Enter number %d: ", i + 1);
        scanf("%d", &arr[i]);
    }
    quickSort(arr, 0, n - 1, n);
    printf("Sorted Array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

```

### insertion sort

```c
#include<stdio.h>
int main(){
     int a[100];
     int n;
     int k;
     int temp;
     int ptr;
     printf("Enter number of elements: ");
     scanf("%d",& n);
     for(int i = 0; i <n ; i++){
        printf("Enter Element[%d]: ", i);
        scanf("%d", &a[i]);
     }
     for(k =0; k<n; k++){
        temp = a[k];
        ptr = k-1;
        while(temp < a[ptr]){
            a[ptr+1] = a[ptr];
            ptr = ptr-1;
        }
        a[ptr+1] = temp;
         printf("Elements after Pass %d: \n ", k);
        for(int u=0; u<n; u++){
           printf("%d ", a[u]);
            if(u >= n){
                break;
            }
        }
        printf("\n");
     }
     for(int j = 0; j <n; j++){
        printf("Element %d is: %d \n", j, a[j]);
     }
     return 0;
}


```
### push and pop

```c
#include <stdio.h>

int choice, item;
int MAX_STACK = 10;
int top = -1;

void push(int arr[], int item);
void pop(int arr[]);
void peep(int arr[]);
void printStack(int arr[]);

void main() {
    int stack[MAX_STACK];
    int uch = 1;
    while (uch == 1) {
        printf("Enter 1 for Push operation\n");
        printf("Enter 2 for Pop operation\n");
        printf("Enter 3 for Peep operation\n");
        printf("Enter 4 for Print operation\n");
        printf("Enter Your Choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter the number to be pushed: ");
                scanf("%d", &item);
                push(stack, item);
                break;
            case 2:
                pop(stack);
                break;
            case 3:
                peep(stack);
                break;
            case 4:
                printStack(stack);
                break;
            default:
                printf("Invalid Choice\n");
        }
        printf("Do you want to continue? Enter 1 for Yes, 0 for No: ");
        scanf("%d", &uch);
    }
}

void push(int arr[], int item) {
    if (top == MAX_STACK - 1) {
        printf("Stack Overflow\n");
    } else {
        arr[++top] = item;
        printf("%d pushed into stack\n", item);
    }
}

void pop(int arr[]) {
    if (top == -1) {
        printf("Stack Underflow\n");
    } else {
        printf("%d popped from stack\n", arr[top--]);
    }
}

void peep(int arr[]) {
    if (top == -1) {
        printf("No elements to display!\n");
    } else {
        printf("Top element is %d\n", arr[top]);
    }
}

void printStack(int arr[]) {
    printf("Stack: ");
    for (int i = 0; i <= top; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

```