non premtive FCFS Priority Code 

```c
#include <stdio.h>

#define MAX_PROCESSES 100

int main() {
    int n;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    if (n > MAX_PROCESSES) {
        printf("Error: Number of processes exceeds limit.\n");
        return 1;
    }

    int arrival[MAX_PROCESSES], burst[MAX_PROCESSES], priority[MAX_PROCESSES];
    int completion[MAX_PROCESSES] = {0};
    int turnaround[MAX_PROCESSES], waiting[MAX_PROCESSES], response[MAX_PROCESSES];

    for (int i = 0; i < n; i++) {
        printf("Enter the arrival time, burst time, and priority for process %d: ", i + 1);
        scanf("%d %d %d", &arrival[i], &burst[i], &priority[i]);
    }

    int current_time = 0;
    int completed = 0;

    while (completed < n) {
        int highest_priority = -1;
        int highest_priority_index = -1;

        for (int i = 0; i < n; i++) {
            if (arrival[i] <= current_time && completion[i] == 0) {
                if (highest_priority == -1 || priority[i] < highest_priority) {
                    highest_priority = priority[i];
                    highest_priority_index = i;
                }
            }
        }

        if (highest_priority_index == -1) {
            current_time++;
        } else {
            completion[highest_priority_index] = current_time + burst[highest_priority_index];
            turnaround[highest_priority_index] = completion[highest_priority_index] - arrival[highest_priority_index];
            waiting[highest_priority_index] = turnaround[highest_priority_index] - burst[highest_priority_index];
            response[highest_priority_index] = current_time - arrival[highest_priority_index];
            current_time = completion[highest_priority_index];
            completed++;
        }
    }

    printf("\nPID\tAT\tBT\tPrio\tCT\tTAT\tWT\tRT\n");
    for (int i = 0; i < n; i++) {
        printf("%d\t%d\t%d\t%d\t%d\t%d\t%d\t%d\n", i + 1, arrival[i], burst[i], priority[i], completion[i], turnaround[i], waiting[i], response[i]);
    }

    float avg_tat = 0, avg_wt = 0;
    for (int i = 0; i < n; i++) {
        avg_tat += turnaround[i];
        avg_wt += waiting[i];
    }
    printf("\nAverage Turnaround Time (TAT): %.2f\n", avg_tat / n);
    printf("Average Waiting Time (WT): %.2f\n", avg_wt / n);

    return 0;
}
```

Brian Version
```c
#include <stdio.h>

// Structure to store process information
typedef struct {
    int process_id;
    int arrival_time;
    int burst_time;
    int priority;
    int start_time;
    int completion_time;
    int waiting_time;
    int turnaround_time;
    int is_completed;
} Process;

void sort_by_arrival(Process processes[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (processes[j].arrival_time > processes[j + 1].arrival_time) {
                Process temp = processes[j];
                processes[j] = processes[j + 1];
                processes[j + 1] = temp;
            }
        }
    }
}

int find_next_process(Process processes[], int n, int current_time) {
    int idx = -1;
    int min_priority = 1e9; // A large number representing the lowest priority

    for (int i = 0; i < n; i++) {
        if (!processes[i].is_completed && processes[i].arrival_time <= current_time) {
            if (processes[i].priority < min_priority) {
                min_priority = processes[i].priority;
                idx = i;
            } else if (processes[i].priority == min_priority) {
                if (processes[i].arrival_time < processes[idx].arrival_time) {
                    idx = i;
                }
            }
        }
    }
    return idx;
}

int main() {
    int n;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    Process processes[n];

    printf("Enter Arrival Time, Burst Time, and Priority for each process:\n");
    for (int i = 0; i < n; i++) {
        processes[i].process_id = i + 1;
        processes[i].is_completed = 0;
        printf("Process %d: ", i + 1);
        scanf("%d %d %d", &processes[i].arrival_time, &processes[i].burst_time, &processes[i].priority);
    }

    sort_by_arrival(processes, n);

    int current_time = 0;
    int completed = 0;

    while (completed < n) {
        int idx = find_next_process(processes, n, current_time);

        if (idx == -1) {
            current_time++;
        } else {
            processes[idx].start_time = current_time;
            processes[idx].completion_time = current_time + processes[idx].burst_time;
            processes[idx].turnaround_time = processes[idx].completion_time - processes[idx].arrival_time;
            processes[idx].waiting_time = processes[idx].turnaround_time - processes[idx].burst_time;
            processes[idx].is_completed = 1;

            current_time = processes[idx].completion_time;
            completed++;
        }
    }

    // Print the results
    printf("\nProcess\tAT\tBT\tPriority\tST\tCT\tTAT\tWT\n");
    for (int i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t%d\t\t%d\t%d\t%d\t%d\n",
               processes[i].process_id,
               processes[i].arrival_time,
               processes[i].burst_time,
               processes[i].priority,
               processes[i].start_time,
               processes[i].completion_time,
               processes[i].turnaround_time,
               processes[i].waiting_time);
    }

    return 0;
}