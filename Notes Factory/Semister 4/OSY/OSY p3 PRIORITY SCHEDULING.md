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

Brian Version for Non Premtive FCFS
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
```
***

Preemptive Priority FCFS

```c
#include <stdio.h>
#include <limits.h>

int main() {
    int n, i, smallest, time, end_time;
    int arrival_time[100], burst_time[100], priority[100], remaining_time[100];
    int completion_time[100], waiting_time[100], turnaround_time[100];
    int total_waiting_time = 0, total_turnaround_time = 0;

    
    // Input number of processes
    printf("Enter the number of processes: ");
    scanf("%d", &n);

    // Input arrival time, burst time, and priority for each process
    printf("Enter Arrival Time, Burst Time, and Priority for each process:\n");
    for (i = 0; i < n; i++) {
        printf("Process %d:\n", i + 1);
        printf("Arrival Time: ");
        scanf("%d", &arrival_time[i]);
        printf("Burst Time: ");
        scanf("%d", &burst_time[i]);
        printf("Priority (Lower value = Higher priority): ");
        scanf("%d", &priority[i]);
        remaining_time[i] = burst_time[i]; // Initialize remaining time
    }

    // Initialize variables
    int completed = 0, current_time = 0;
    smallest = -1; // Indicates the process with the highest priority (lower value)

    // Processing starts
    while (completed != n) {
        smallest = -1;
        int min_priority = INT_MAX;

        // Find the process with the highest priority that has arrived
        for (i = 0; i < n; i++) {
            if (arrival_time[i] <= current_time && remaining_time[i] > 0 && priority[i] < min_priority) {
                smallest = i;
                min_priority = priority[i];
            }
        }

        if (smallest == -1) {
            current_time++; // No process is ready to execute
            continue;
        }

        // Process the selected process
        remaining_time[smallest]--;
        current_time++;

        // If the process is completed
        if (remaining_time[smallest] == 0) {
            completed++;
            end_time = current_time;
            completion_time[smallest] = end_time;
            turnaround_time[smallest] = completion_time[smallest] - arrival_time[smallest];
            waiting_time[smallest] = turnaround_time[smallest] - burst_time[smallest];
            total_waiting_time += waiting_time[smallest];
            total_turnaround_time += turnaround_time[smallest];
        }
    }

    // Write the results to the file
    fprintf(file, "Process\tAT\tBT\tP\tCT\tWT\tTAT\n");
    for (i = 0; i < n; i++) {
        printf(file, "P%d\t%d\t%d\t%d\t%d\t%d\t%d\n",
                i + 1, arrival_time[i], burst_time[i], priority[i], completion_time[i], waiting_time[i], turnaround_time[i]);
    }

    printf(file, "\nAverage Waiting Time: %.2f\n", (float)total_waiting_time / n);
    printf(file, "Average Turnaround Time: %.2f\n", (float)total_turnaround_time / n);

    // Close the file
    fclose(file);

    printf("Priority preemptive scheduling results have been written to 'priority_preemptive_output.txt'.\n");

    return 0;
}
```