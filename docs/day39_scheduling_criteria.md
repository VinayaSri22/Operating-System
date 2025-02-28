# Scheduling Criteria in Operating Systems

## 1. CPU Utilization

*   **Definition:** Percentage of time the CPU is busy executing processes.
*   **Goal:** Maximize CPU utilization to avoid wasting resources.
*   **Formula:** `CPU Utilization = (Busy Time / Total Time) * 100%`
*   **Target:** Typically aim for 40% (lightly loaded) to 90% (heavily loaded).

## 2. Throughput

*   **Definition:** Number of processes completed per unit of time.
*   **Goal:** Maximize throughput to increase system efficiency.
*   **Measurement:** Processes per second, processes per minute, etc.
*   **Factors:** Affected by process length, scheduling algorithm, and system overhead.

## 3. Turnaround Time

*   **Definition:** Total time taken from process submission to completion.
*   **Components:** Includes waiting time, execution time, and I/O time.
*   **Goal:** Minimize turnaround time to improve user experience.
*   **Formula:** `Turnaround Time = Completion Time - Arrival Time`

## 4. Waiting Time

*   **Definition:** Time a process spends waiting in the ready queue.
*   **Goal:** Minimize waiting time to reduce process delays.
*   **Impact:** Directly affects user-perceived performance.
*   **Formula:** `Waiting Time = Turnaround Time - Burst Time`

## 5. Response Time

*   **Definition:** Time it takes for a process to produce its first response.
*   **Goal:** Minimize response time, especially for interactive systems.
*   **Importance:** Critical for user satisfaction in interactive applications.
*   **Difference from Turnaround Time:** Response time focuses on the initial output, while turnaround time considers the entire process duration.

## Summary Table

| Criterion        | Definition                                     | Goal                 | Impact                                  |
| ---------------- | ---------------------------------------------- | -------------------- | --------------------------------------- |
| CPU Utilization  | Percentage of time CPU is busy                 | Maximize             | Efficient resource usage                |
| Throughput       | Number of completed processes per unit time    | Maximize             | System efficiency                       |
| Turnaround Time  | Total time from submission to completion       | Minimize             | User experience                         |
| Waiting Time     | Time spent waiting in the ready queue          | Minimize             | Process delays                          |
| Response Time    | Time to produce the first response             | Minimize             | User satisfaction (interactive systems) |

## Example Scenario

Consider three processes with the following characteristics:

| Process | Arrival Time | Burst Time |
| ------- | ------------ | ---------- |
| P1      | 0            | 8          |
| P2      | 1            | 4          |
| P3      | 2            | 9          |

Using First-Come, First-Served (FCFS) scheduling:

*   P1: Waiting Time = 0, Turnaround Time = 8
*   P2: Waiting Time = 7, Turnaround Time = 11
*   P3: Waiting Time = 11, Turnaround Time = 20

Average Waiting Time = (0 + 7 + 11) / 3 = 6
Average Turnaround Time = (8 + 11 + 20) / 3 = 13

