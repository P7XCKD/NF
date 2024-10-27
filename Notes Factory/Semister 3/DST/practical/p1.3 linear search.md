```c
#include <stdio.h>

void ls(int data[], int n, int item, int *loc) {
    data[n] = item;
    int loc_var = 1;
    while (data[loc_var - 1] != item) {
        loc_var++;
    }
    if (loc_var == n + 1) {
        loc_var = 0;
    }
    *loc = loc_var;
}

int main() {
    int data[100], n, item, loc;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter elements:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &data[i]);
    }
    printf("Enter item to search: ");
    scanf("%d", &item);
    ls(data, n, item, &loc);
    if (loc == 0) {
        printf("Item not found.\n");
    } else {
        printf("Item found at position: %d\n", loc);
    }
    return 0;
}

```