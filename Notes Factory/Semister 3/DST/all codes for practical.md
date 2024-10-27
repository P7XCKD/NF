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