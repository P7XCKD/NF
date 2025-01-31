V3 and V4 are best

producuer consumer code
```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>

#define BUFFER_SIZE 5

// Shared variables
int buffer[BUFFER_SIZE];
int in = 0;
int out = 0;
int count = 0;

// Semaphores
sem_t empty;
sem_t full;
sem_t mutex;

// Producer thread function
void* producer(void* arg) {
    int item;
    for (int i = 0; i < 10; ++i) {
        item = rand() % 100; // Generate random item

        // Wait for space in buffer
        sem_wait(&empty);
        // Acquire lock on buffer
        sem_wait(&mutex);

        buffer[in] = item;
        in = (in + 1) % BUFFER_SIZE;
        count++;

        printf("Producer produced %d\n", item);

        // Release lock on buffer
        sem_post(&mutex);
        // Signal that buffer has an item
        sem_post(&full);
    }
    return NULL;
}

// Consumer thread function
void* consumer(void* arg) {
    int item;
    for (int i = 0; i < 10; ++i) {
        // Wait for item in buffer
        sem_wait(&full);
        // Acquire lock on buffer
        sem_wait(&mutex);

        item = buffer[out];
        out = (out + 1) % BUFFER_SIZE;
        count--;

        printf("Consumer consumed %d\n", item);

        // Release lock on buffer
        sem_post(&mutex);
        // Signal that buffer has space
        sem_post(&empty);
    }
    return NULL;
}

int main() {
    // Initialize semaphores
    sem_init(&empty, 0, BUFFER_SIZE); // Initially, buffer is empty
    sem_init(&full, 0, 0);          // Initially, buffer is empty
    sem_init(&mutex, 0, 1);         // Initially, only one thread can access buffer

    // Create producer and consumer threads
    pthread_t producer_thread, consumer_thread;
    pthread_create(&producer_thread, NULL, producer, NULL);
    pthread_create(&consumer_thread, NULL, consumer, NULL);

    // Wait for threads to finish
    pthread_join(producer_thread, NULL);
    pthread_join(consumer_thread, NULL);

    // Destroy semaphores
    sem_destroy(&empty);
    sem_destroy(&full);
    sem_destroy(&mutex);

    return 0;
}
```


2nd code fiend version
```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 5

int queue[MAX];
int front = 0;
int rear = -1;
int itemCount = 0;
int itemProduced = 1;

bool isQueueFull() {
    return itemCount == MAX;
}

bool isQueueEmpty() {
    return itemCount == 0;
}

void addItem(int value) {
    if (isQueueFull()) {
        printf("Buffer is full! Cannot produce more items.\n");
        return;
    }
    rear = (rear + 1) % MAX;
    queue[rear] = value;
    itemCount++;
    printf("\nProducer produces item: %d\n", value);
    printf("Items in queue: %d\n", itemCount);
    printf("Empty spots: %d\n", MAX - itemCount);
}

int removeItem() {
    if (isQueueEmpty()) {
        printf("Buffer is empty! Cannot consume any items.\n");
        return -1;
    }
    int value = queue[front];
    front = (front + 1) % MAX;
    itemCount--;
    return value;
}

void produce() {
    addItem(itemProduced);
    itemProduced++;
}

void consume() {
    int consumedItem = removeItem();
    if (consumedItem != -1) {
        printf("\nConsumer consumes item: %d\n", consumedItem);
        printf("Items in queue: %d\n", itemCount);
        printf("Empty spots: %d\n", MAX - itemCount);
    }
}

int main() {
    int choice;

    while (1) {
        printf("\n1. Produce Item\n2. Consume Item\n3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                produce();
                break;
            case 2:
                consume();
                break;
            case 3:
                exit(0);
            default:
                printf("Invalid choice, try again.\n");
        }
    }

    return 0;
}

```

v3
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <stdbool.h>

int mutex = 1;
int empty;
int full = 0;
int *queue; // Dynamic array for the buffer
int front = 0;
int rear = -1;
int itemCount = 0;
int buffer = 0;
int MAX;

bool isFull() {
    return itemCount == MAX;
}

bool isEmpty() {
    return itemCount == 0;
}

void insertData(int data) {
    if (!isFull()) {
        if (rear == MAX - 1) {
            rear = -1;
        }
        queue[++rear] = data;
        itemCount++;
    }
}

int deleteData() {
    int data = queue[front++];
    if (front == MAX) {
        front = 0;
    }
    itemCount--;
    return data;
}

void producer() {
    --mutex;
    --empty;
    insertData(itemCount);
    printf("\nProducer produces item: %d\n", itemCount);
    ++full;
    ++buffer;
    ++mutex;
    printf("Count: %d\n", itemCount);
    printf("Buffer Count: %d\n", buffer);
    printf("Empty Count: %d\n", empty);
}

void consumer() {
    --mutex;
    --full;
    int x = deleteData();
    printf("\nConsumer consumes item: %d\n", x + 1);
    ++empty;
    --buffer;
    ++mutex;
    printf("Count: %d\n", itemCount);
    printf("Buffer Count: %d\n", buffer);
    printf("Empty Count: %d\n", empty);
}

int main() {
    int n, i;

    // Take user input for buffer size
    printf("Enter the buffer size: ");
    scanf("%d", &MAX);

    // Initialize the buffer and semaphores
    queue = (int *)malloc(MAX * sizeof(int));
    empty = MAX;

    printf("\n1. Press 1 for Producer"
           "\n2. Press 2 for Consumer"
           "\n3. Press 3 for Exit\n");

    while (1) {
        printf("\nEnter your choice: ");
        scanf("%d", &n);

        switch (n) {
        case 1:
            if ((mutex == 1) && (empty != 0)) {
                producer();
            } else if (buffer == MAX) {
                printf("Buffer is full!\n");
            }
            break;
        case 2:
            if ((mutex == 1) && (full != 0)) {
                consumer();
            } else if (buffer == 0) {
                printf("Buffer is empty!\n");
            }
            break;
        case 3:
            free(queue); // Free the dynamically allocated memory
            exit(0);
            break;
        default:
            printf("Invalid choice! Please enter 1, 2, or 3.\n");
        }
    }
}

```