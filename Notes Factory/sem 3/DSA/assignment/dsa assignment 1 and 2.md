
# Assignment 1 — Climate Heatwave Monitoring Using Queue

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

# Assignment 2 — Student Recommendation System Using Sorting and Searching

## 1. C Program

```c
#include <stdio.h>
#include <time.h>

#define MAX 1000

typedef struct {
    int id;
    char name[30];
    float score;
} Student;

Student a[MAX], temp[MAX];
long long comparisons;

void bubbleSort(Student a[], int n) {
    int i, j;
    Student t;
    comparisons = 0;

    for (i = 0; i < n - 1; i++)
        for (j = 0; j < n - i - 1; j++) {
            comparisons++;
            if (a[j].score < a[j + 1].score) {
                t = a[j];
                a[j] = a[j + 1];
                a[j + 1] = t;
            }
        }
}

void selectionSort(Student a[], int n) {
    int i, j, max;
    Student t;
    comparisons = 0;

    for (i = 0; i < n - 1; i++) {
        max = i;

        for (j = i + 1; j < n; j++) {
            comparisons++;
            if (a[j].score > a[max].score)
                max = j;
        }

        t = a[i];
        a[i] = a[max];
        a[max] = t;
    }
}

void insertionSort(Student a[], int n) {
    int i, j;
    Student key;
    comparisons = 0;

    for (i = 1; i < n; i++) {
        key = a[i];
        j = i - 1;

        while (j >= 0) {
            comparisons++;
            if (a[j].score < key.score) {
                a[j + 1] = a[j];
                j--;
            } else {
                break;
            }
        }

        a[j + 1] = key;
    }
}

void merge(Student a[], int l, int m, int r) {
    int i = l, j = m + 1, k = l;

    while (i <= m && j <= r) {
        comparisons++;

        if (a[i].score >= a[j].score)
            temp[k++] = a[i++];
        else
            temp[k++] = a[j++];
    }

    while (i <= m) temp[k++] = a[i++];
    while (j <= r) temp[k++] = a[j++];

    for (i = l; i <= r; i++)
        a[i] = temp[i];
}

void mergeSort(Student a[], int l, int r) {
    if (l < r) {
        int m = (l + r) / 2;
        mergeSort(a, l, m);
        mergeSort(a, m + 1, r);
        merge(a, l, m, r);
    }
}

int sequentialSearch(Student a[], int n, int id,
                     long long *comp) {
    int i;
    *comp = 0;

    for (i = 0; i < n; i++) {
        (*comp)++;
        if (a[i].id == id)
            return i;
    }

    return -1;
}

int binarySearch(Student a[], int n, int id,
                 long long *comp) {
    int low = 0, high = n - 1, mid;
    *comp = 0;

    while (low <= high) {
        mid = (low + high) / 2;
        (*comp)++;

        if (a[mid].id == id)
            return mid;
        else if (id < a[mid].id)
            high = mid - 1;
        else
            low = mid + 1;
    }

    return -1;
}

int main() {
    int n, i, id, pos;
    long long comp;
    clock_t start, end;
    double elapsed;

    printf("Enter number of students (1-1000): ");
    scanf("%d", &n);

    if (n < 1 || n > MAX) {
        printf("Invalid number of students.\n");
        return 0;
    }

    for (i = 0; i < n; i++) {
        a[i].id = i + 1;
        printf("Enter name and score: ");
        scanf("%29s %f", a[i].name, &a[i].score);
    }

    start = clock();
    comparisons = 0;
    mergeSort(a, 0, n - 1);
    end = clock();

    elapsed = (double)(end - start) / CLOCKS_PER_SEC;

    printf("\nRanked Students:\n");
    printf("ID\tName\tScore\n");

    for (i = 0; i < n; i++)
        printf("%d\t%s\t%.2f\n",
               a[i].id, a[i].name, a[i].score);

    printf("Merge Sort time: %.6f seconds\n", elapsed);
    printf("Merge Sort comparisons: %lld\n", comparisons);

    printf("\nEnter student ID to search: ");
    scanf("%d", &id);

    start = clock();
    pos = sequentialSearch(a, n, id, &comp);
    end = clock();

    printf("Sequential Search: Position=%d, Comparisons=%lld, Time=%.6f seconds\n",
           pos, comp, (double)(end - start) / CLOCKS_PER_SEC);

    /* Sort records by ID before Binary Search. */
    for (i = 0; i < n; i++) {
        int j;
        for (j = i + 1; j < n; j++) {
            if (a[i].id > a[j].id) {
                Student t = a[i];
                a[i] = a[j];
                a[j] = t;
            }
        }
    }

    start = clock();
    pos = binarySearch(a, n, id, &comp);
    end = clock();

    printf("Binary Search: Position=%d, Comparisons=%lld, Time=%.6f seconds\n",
           pos, comp, (double)(end - start) / CLOCKS_PER_SEC);

    return 0;
}
```
### output
```
STUDENT RECOMMENDATION SYSTEM
Ranked Students:
ID	Name	Score
5	e	91.00
4	d	74.00
3	c	57.00
2	b	40.00
1	a	23.00
Merge Sort time: 0.000002 seconds
Merge Sort comparisons: 5

Sequential Search: Position=0, Comparisons=1, Time=0.000001 seconds
Binary Search: Position=4, Comparisons=3, Time=0.000001 seconds
```
```
Ranked Students:
ID	Name	Score
23	w	94.00
17	q	93.00
11	k	92.00
5	e	91.00
22	v	77.00
16	p	76.00
10	j	75.00
4	d	74.00
21	u	60.00
15	o	59.00
9	i	58.00
3	c	57.00
20	t	43.00
14	n	42.00
8	h	41.00
2	b	40.00
25	y	27.00
19	s	26.00
13	m	25.00
7	g	24.00
1	a	23.00
24	x	10.00
18	r	9.00
12	l	8.00
6	f	7.00
Merge Sort time: 0.000004 seconds
Merge Sort comparisons: 86

Sequential Search: Position=16, Comparisons=17, Time=0.000002 seconds
Binary Search: Position=24, Comparisons=5, Time=0.000016 seconds
```

```
Ranked Students:
ID	Name	Score
47	u	98.00
41	o	97.00
35	i	96.00
29	c	95.00
23	w	94.00
17	q	93.00
11	k	92.00
5	e	91.00
46	t	81.00
40	n	80.00
34	h	79.00
28	b	78.00
22	v	77.00
16	p	76.00
10	j	75.00
4	d	74.00
45	s	64.00
39	m	63.00
33	g	62.00
27	a	61.00
21	u	60.00
15	o	59.00
9	i	58.00
3	c	57.00
50	x	48.00
44	r	47.00
38	l	46.00
32	f	45.00
26	z	44.00
20	t	43.00
14	n	42.00
8	h	41.00
2	b	40.00
49	w	31.00
43	q	30.00
37	k	29.00
31	e	28.00
25	y	27.00
19	s	26.00
13	m	25.00
7	g	24.00
1	a	23.00
48	v	14.00
42	p	13.00
36	j	12.00
30	d	11.00
24	x	10.00
18	r	9.00
12	l	8.00
6	f	7.00
Merge Sort time: 0.000004 seconds
Merge Sort comparisons: 210

Sequential Search: Position=24, Comparisons=25, Time=0.000002 seconds
Binary Search: Position=49, Comparisons=6, Time=0.000001 seconds
```
## 2. Sorting Algorithm Complexity

| Algorithm | Best Case | Average Case | Worst Case |
| --- | --- | --- | --- |
| Bubble Sort | O(n²) | O(n²) | O(n²) |
| Selection Sort | O(n²) | O(n²) | O(n²) |
| Insertion Sort | O(n) | O(n²) | O(n²) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) |

## 3. Searching Algorithm Complexity

| Algorithm | Best Case | Average Case | Worst Case |
| --- | --- | --- | --- |
| Sequential Search | O(1) | O(n) | O(n) |
| Binary Search | O(1) | O(log n) | O(log n) |

Note: Binary Search requires records sorted by student ID. Sorting by recommendation score alone is not sufficient.


## 5. Suitable Algorithms

-   Sorting: Merge Sort is suitable for large datasets because its worst-case time complexity is O(n log n).
    
-   Searching: Binary Search is suitable for sorted records because it searches in O(log n) time.
    
-   Conclusion: Merge Sort and Binary Search are efficient choices for managing and retrieving student records.