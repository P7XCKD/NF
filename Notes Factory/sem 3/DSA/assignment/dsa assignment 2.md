

# Assignment 2 
> [!question] Student Recommendation System Using Sorting and Searching
> - Develop and evaluate a Student Recommendation System in C/C++ using appropriate sorting and searching algorithms. The system should manage student records and rank students based on a given recommendation score.  
> - Implement suitable sorting techniques to arrange student records according to their scores and searching techniques to efficiently retrieve a specific student record. Compare the performance of the implemented algorithms for different dataset sizes based on execution time and number of comparisons, and prepare a comparison table showing the performance of each algorithm.  
> - Based on the experimental results, determine the most suitable sorting and searching algorithms for the system.  
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