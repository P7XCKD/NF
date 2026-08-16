> [!attention] SOME CODES ARE WRONG


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

### insertion and deletion element in queue
```c
#include <stdio.h>

void printQueue(int arr[], int n);

void main() {
    int n;
    printf("Enter the maximum size of queue: ");
    scanf("%d", &n);
    int arr[n];
    int uch = 1;
    int rear = -1;
    int front = -1;
    int choice;

    for (int i = 0; i < n; i++) {
        arr[i] = 0; // initialize the queue
    }

    while (uch == 1) {
        printf("\nEnter 1 to insert element");
        printf("\nEnter 2 to delete element");
        printf("\nEnter 3 to print queue\n");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                if (front == 0 && rear == n - 1) {
                    printf("Queue Overflow!\n");
                    return;
                }
                int item;
                printf("Enter the element to insert: ");
                scanf("%d", &item);
                if (front == -1 && rear == -1) {
                    front = 0;
                    rear = 0;
                } else if (rear == n - 1) {
                    rear = 0;
                } else {
                    rear = rear + 1;
                }
                arr[rear] = item;
                printf("Item %d inserted at position %d\n", item, rear);
                printQueue(arr, n);
                break;
            case 2:
                if (front == -1 && rear == -1) {
                    printf("Queue Underflow!\n");
                    return;
                }
                int num = arr[front];
                arr[front] = 0;
                if (front == rear) {
                    front = -1;
                    rear = -1;
                } else if (front == n - 1) {
                    front = 0;
                } else {
                    front = front + 1;
                }
                printf("Item %d deleted from queue\n", num);
                printQueue(arr, n);
                break;
            case 3:
                printQueue(arr, n);
                break;
            default:
                printf("Invalid Choice!\n");
        }
        printf("Enter 1 to continue, 0 to exit: ");
        scanf("%d", &uch);
    }
}

void printQueue(int arr[], int n) {
    printf("QUEUE: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

```

### infix to postfix

```c
#include <stdio.h>
#include <string.h>

int question(char c)
{
    if (c == '^')
        return 3;
    else if (c == '/' || c == '*')
        return 2;
    else if (c == '+' || c == '-')
        return 1;
    else
        return -1;
}

char direction(char c) {
    if (c == '^')
        return 'R';
    return 'L';
}

void infix_to_postfix(char s[], char result[])
{
    int resultindex = 0;
    int len = strlen(s);
    char storage[1000];
    int storageindex = -1;

    for (int i = 0; i < len; i++)
        {
        char symbol = s[i];

        if ((symbol >= 'a' && symbol <= 'z') || (symbol >= 'A' && symbol <= 'Z') || (symbol >= '0' && symbol <= '9'))
        {
            result[resultindex++] = symbol;
        }
        else if (symbol == '(')
        {
            storage[++storageindex] = symbol;
        }
        else if (symbol == ')')
            {
            while (storageindex >= 0 && storage[storageindex] != '(') {
                result[resultindex++] = storage[storageindex--];
            }
            storageindex--;
        } else {
            while (storageindex >= 0 && (question(s[i]) < question(storage[storageindex]) ||
            (question(s[i]) == question(storage[storageindex]) && direction(s[i]) == 'L')))
            {
                result[resultindex++] = storage[storageindex--];
            }
            storage[++storageindex] = symbol;
        }
    }

    while (storageindex >= 0)
    {
        result[resultindex++] = storage[storageindex--];
    }

    result[resultindex] = '\0';
}

int main()
 {
    char exp[] = "a+b(c*d)(f-g)+h";
    char result[1000];

    infix_to_postfix(exp, result);

    printf("Postfix expression: %s\n", result);

    return 0;
}

```

### implementation of linked list and traverse it

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* createNode(int new_data) {
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = NULL;
    return new_node;
}

void traverseList(struct Node* head) {
    while (head != NULL) {
        printf("%d\n", head->data);
        head = head->next;
    }
}

void main() {
    struct Node* head = createNode(10);
    head->next = createNode(20);
    head->next->next = createNode(30);
    head->next->next->next = createNode(40);
    traverseList(head);
}

```

### operations on linked list insertion and deletion 

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* createNode(struct Node* s) {
    int n;
    printf("Enter the node value: ");
    scanf("%d", &n);
    struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
    temp->data = n;
    temp->next = NULL;
    struct Node* start = s;

    if (start == NULL) {
        start = temp;
        printf("First Node Created\n");
        return start;
    }

    struct Node* travel = s;
    while (travel->next != NULL) {
        travel = travel->next;
    }
    travel->next = temp;
    return start;
}

struct Node* insertNode(struct Node* s) {
    printf("Welcome to insert node operation\n");
    int num, choice;
    struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
    printf("Enter the node value: ");
    scanf("%d", &temp->data);
    temp->next = NULL;
    struct Node* start = s;
    struct Node* travel = s;

    printf("Enter the options for the following choices:\n");
    printf("1 - Insert at the beginning\n");
    printf("2 - Insert at the end\n");
    printf("3 - Insert after specified node data\n");
    scanf("%d", &choice);

    switch (choice) {
        case 1:
            temp->next = start;
            start = temp;
            break;
        case 2:
            while (travel->next != NULL) {
                travel = travel->next;
            }
            travel->next = temp;
            break;
        case 3:
            printf("Enter the data part after which you want to enter the new node: ");
            scanf("%d", &num);
            while (travel->data != num && travel->next != NULL) {
                travel = travel->next;
            }
            if (travel->data == num) {
                temp->next = travel->next;
                travel->next = temp;
            } else {
                printf("As desired node not found, we cannot add the new node\n");
                free(temp);
            }
            break;
        default:
            printf("Invalid Option\n");
            free(temp);
            break;
    }
    return start;
}

struct Node* delNode(struct Node* s) {
    int num;
    struct Node* travel = s;
    struct Node* start = s;

    if (travel == NULL) {
        printf("Linked List is empty\n");
        return NULL;
    }

    printf("Enter the node data to be deleted: ");
    scanf("%d", &num);
    struct Node* prev = NULL;

    while (travel->data != num && travel->next != NULL) {
        prev = travel;
        travel = travel->next;
    }

    if (travel->data == num) {
        if (travel == start) {
            start = travel->next;
        } else {
            prev->next = travel->next;
        }
        free(travel);
        printf("Node with value %d deleted\n", num);
    } else {
        printf("Node with value %d not found\n", num);
    }
    return start;
}

void displayNodes(struct Node* s) {
    struct Node* travel = s;
    printf("The list of nodes is as follows:\n");
    while (travel != NULL) {
        printf("%d ", travel->data);
        travel = travel->next;
    }
    printf("\n");
}

int main() {
    struct Node* head = NULL;
    int choice;

    do {
        printf("1 - Create Node\n");
        printf("2 - Insert Node\n");
        printf("3 - Delete Node\n");
        printf("4 - Display Nodes\n");
        printf("5 - Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                head = createNode(head);
                break;
            case 2:
                head = insertNode(head);
                break;
            case 3:
                head = delNode(head);
                break;
            case 4:
                displayNodes(head);
                break;
            case 5:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 5);

    return 0;
}

```

### tree traversal
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int item;
    struct node* left;
    struct node* right;
};

void inorderTraversal(struct node* root) {
    if (root == NULL) return;
    inorderTraversal(root->left);
    printf("%d → ", root->item);
    inorderTraversal(root->right);
}

void preorderTraversal(struct node* root) {
    if (root == NULL) return;
    printf("%d → ", root->item);
    preorderTraversal(root->left);
    preorderTraversal(root->right);
}

void postorderTraversal(struct node* root) {
    if (root == NULL) return;
    postorderTraversal(root->left);
    postorderTraversal(root->right);
    printf("%d → ", root->item);
}

struct node* createNode(int value) {
    struct node* newNode = (struct node*)malloc(sizeof(struct node));
    newNode->item = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct node* insertLeft(struct node* root, int value) {
    root->left = createNode(value);
    return root->left;
}

struct node* insertRight(struct node* root, int value) {
    root->right = createNode(value);
    return root->right;
}

int main() {
    struct node* root = createNode(1);
    insertLeft(root, 12);
    insertRight(root, 9);
    insertLeft(root->left, 5);
    insertRight(root->left, 6);

    printf("Inorder traversal: \n");
    inorderTraversal(root);
    printf("\nPreorder traversal: \n");
    preorderTraversal(root);
    printf("\nPostorder traversal: \n");
    postorderTraversal(root);
    printf("\n");

    return 0;
}

```