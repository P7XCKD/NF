
# Assignment 1 — Climate Heatwave Monitoring Using Queue
> [!question] Climate Heatwave Monitoring Using Queue
> Climate Heatwave Monitoring Using Queue Design and implement a menu-driven C program using an array-based Queue to manage weather observations for a Climate Heatwave Monitoring System. Each observation should contain Observation ID, Location, Timestamp, Temperature, and Humidity. Implement Enqueue, Dequeue, Peek, Display, Search, Count, and Queue Status operations. Demonstrate FIFO processing and analyze the time and space complexity of the Queue operations
## 1. C Program

```c
#include <stdio.h>

#define MAX 5

typedef struct {
    int id;
    char location[30];
    char timestamp[20];
    float temperature, humidity;
} Observation;

Observation q[MAX];
int front = -1, rear = -1, count = 0;

void enqueue() {
    Observation o;

    if (count == MAX) {
        printf("Queue is full.\n");
        return;
    }

    printf("Enter ID, location, timestamp, temperature and humidity:\n");
    scanf("%d %29s %19s %f %f", &o.id, o.location,
          o.timestamp, &o.temperature, &o.humidity);

    if (count == 0)
        front = 0;

    rear = (rear + 1) % MAX;
    q[rear] = o;
    count++;

    printf("Observation added.\n");
}

void dequeue() {
    if (count == 0) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Removed observation ID: %d\n", q[front].id);
    front = (front + 1) % MAX;
    count--;

    if (count == 0)
        front = rear = -1;
}

void peek() {
    if (count == 0)
        printf("Queue is empty.\n");
    else
        printf("Front observation: ID=%d, Location=%s, Temperature=%.1f C\n",
               q[front].id, q[front].location, q[front].temperature);
}

void display() {
    int i, index;

    if (count == 0) {
        printf("Queue is empty.\n");
        return;
    }

    for (i = 0; i < count; i++) {
        index = (front + i) % MAX;
        printf("%d %s %s %.1f C %.1f%%\n",
               q[index].id, q[index].location, q[index].timestamp,
               q[index].temperature, q[index].humidity);
    }
}

void search() {
    int id, i, index;

    printf("Enter observation ID to search: ");
    scanf("%d", &id);

    for (i = 0; i < count; i++) {
        index = (front + i) % MAX;

        if (q[index].id == id) {
            printf("Observation found at location %s\n",
                   q[index].location);
            return;
        }
    }

    printf("Observation not found.\n");
}

int main() {
    int choice;

    do {
        printf("\n1.Enqueue 2.Dequeue 3.Peek 4.Display\n");
        printf("5.Search 6.Count 7.Queue Status 0.Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: enqueue(); break;
            case 2: dequeue(); break;
            case 3: peek(); break;
            case 4: display(); break;
            case 5: search(); break;
            case 6: printf("Count = %d\n", count); break;
            case 7:
                if (count == 0)
                    printf("Queue is empty.\n");
                else if (count == MAX)
                    printf("Queue is full.\n");
                else
                    printf("Queue is not full.\n");
                break;
            case 0: printf("Exiting.\n"); break;
            default: printf("Invalid choice.\n");
        }
    } while (choice != 0);

    return 0;
}
````
## output
```text
1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 1
Enter ID, location, timestamp, temperature and humidity:
1
delhi
19/10/2026
45
69
Observation added.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 1
Enter ID, location, timestamp, temperature and humidity:
2
mumbai
19/10/2026
38.5
65
Observation added.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 1
Enter ID, location, timestamp, temperature and humidity:
3
pune
19/10/2026
36.2
58
Observation added.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 4
1 delhi 19/10/2026 45.0 C 69.0%
2 mumbai 19/10/2026 38.5 C 65.0%
3 pune 19/10/2026 36.2 C 58.0%

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 3
Front observation: ID=1, Location=delhi, Temperature=45.0 C

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 5
Enter observation ID to search: 2
Observation found at location mumbai

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 6
Count = 3

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 7
Queue is not full.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 2
Removed observation ID: 1

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 4
2 mumbai 19/10/2026 38.5 C 65.0%
3 pune 19/10/2026 36.2 C 58.0%

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 5
Enter observation ID to search: 9
Observation not found.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 1
Enter ID, location, timestamp, temperature and humidity:
4
surat
19/10/2026
39.4
62
Observation added.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 1
Enter ID, location, timestamp, temperature and humidity:
5
nashik
19/10/2026
35.8
55
Observation added.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 1
Queue is full.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 7
Queue is full.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 2
Removed observation ID: 2

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 2
Removed observation ID: 3

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 2
Removed observation ID: 4

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 2
Removed observation ID: 5

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 2
Queue is empty.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 3
Queue is empty.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 4
Queue is empty.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 6
Count = 0

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 7
Queue is empty.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 9
Invalid choice.

1.Enqueue 2.Dequeue 3.Peek 4.Display
5.Search 6.Count 7.Queue Status 0.Exit
Enter choice: 0
Exiting.

```
## 2. Time and Space Complexity

| Operation | Time Complexity |
| --- | --- |
| Enqueue | O(1) |
| Dequeue | O(1) |
| Peek | O(1) |
| Display | O(n) |
| Search | O(n) |
| Count | O(1) |
| Queue Status | O(1) |

Space Complexity: O(n)

