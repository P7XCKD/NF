-  ARRAY INSERTION OF AN ELEMENT

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
2) 