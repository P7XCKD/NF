find element in an array at each phase using search index


```c
#include <stdio.h>

int main() {
    int n, i, search, found = 0;

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

    printf("Enter the element to search for: ");
    scanf("%d", &search);

    for (i = 0; i < n; i++) {
        if (arr[i] == search) {
            printf("Element %d found at index %d\n", search, i);
            found += 1;
        }
    }

    if (found == 0) {
        printf("Element %d not found in the array\n", search);
    }

    return 0;
}
```

insert an element in array

```c
#include <stdio.h>

int main() {
    int n, i, search, found = 0;

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
delete an element in array

```c
#include <stdio.h>

int main() {
    int n, i, search, found = 0;

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
    else{
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
### Algorithm: Searching for an Element in an Array  
**Procedure**: **SEARCH(LA, N, SEARCH, FOUND)**  
- **Description**:
  - **LA** is a linear array with **N elements**.
  - **SEARCH** is the element to be located in **LA**.
  - **FOUND** tracks if the element **SEARCH** is present in **LA**.

---

1. **Initialize**  
   - Set **FOUND := 0**

2. **Repeat Steps 3 to 4 for i = 0 to N - 1**

3. **Check if Element Matches**  
   - If **LA[i] == SEARCH**, then:
     - Print **"Element SEARCH found at index i"**
     - Increment **FOUND by 1**

4. **End of Loop**

5. **Check if Element Was Not Found**  
   - If **FOUND == 0**, then:
     - Print **"Element SEARCH not found in the array"**

6. **Exit**

### Algorithm: Inserting New Element in an Array  
**Procedure**: **INSERT(LA, N, K, ITEM)**  
- **Description**:
  - **LA** is a linear array containing **N elements**.
  - **K** is a positive integer such that **K <= N**.
  - This algorithm inserts an element, **ITEM**, into the **Kth position** in **LA**.

---

1. **Initialization**:  
   - **SET J = N**

2. **Repeat Steps 3 and 4 while J >= K**

3. **Move Jth Element Downward**:  
   - **SET LA[J + 1] = LA[J]**

4. **Decrease Counter**:  
   - **SET J = J – 1**
   - **End of Step 2 loop**

5. **Insert Element**:  
   - **SET LA[K] := ITEM**

6. **Update Array Size**:  
   - **SET N = N + 1**

7. **Exit**

---

### Algorithm: Deleting an Element from an Array  
**Procedure**: **DELETE(LA, N, K, ITEM)**  
- **Description**:
  - **LA** is a linear array containing **N elements**.
  - **K** is a positive integer such that **K <= N**.
  - This algorithm deletes the **Kth element** from **LA**.

---

1. **Set ITEM**:  
   - **SET ITEM := LA[K]**

2. **Repeat for J = K to N - 1**  
   - **Move J+1st Element Upward**:  
     - **SET LA[J] := LA[J + 1]**
   - **End of loop**

3. **Reset Array Size**:  
   - **SET N := N - 1**

4. **Exit**

    