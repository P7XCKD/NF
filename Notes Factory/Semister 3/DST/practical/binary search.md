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
// sortingf part
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
            found += 1;
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