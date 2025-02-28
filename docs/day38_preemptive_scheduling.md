# Preemptive vs. Non-Preemptive Scheduling

## 1. CPU Scheduler

*   **Definition:** Selects the next process to be executed from the ready queue.
*   **Goal:** Optimize system performance based on scheduling algorithm criteria (e.g., minimize waiting time, maximize throughput).

## 2. Dispatcher

*   **Definition:** Module that gives control of the CPU to the process selected by the scheduler.
*   **Tasks:**
    *   Context switching (saving the state of the old process and loading the state of the new process).
    *   Switching to user mode.
    *   Jumping to the proper location in the user program to restart execution.
*   **Dispatch Latency:** The time it takes for the dispatcher to stop one process and start another. Critical for real-time systems.

## 3. Preemptive Scheduling

*   **Definition:** The CPU can be taken away from a running process.
*   **Conditions:**
    *   Process switches from running to ready state (e.g., interrupt).
    *   Process switches from waiting to ready state (e.g., I/O completion).
*   **Advantages:**
    *   Better response time.
    *   More fair allocation of CPU time.
*   **Disadvantages:**
    *   Higher overhead due to context switching.
    *   Potential for race conditions (requires synchronization mechanisms).

### Example (Preemptive)

```c
#include <stdio.h>
#include <signal.h>
#include <unistd.h>

void signal_handler(int signum) {
    printf("Interrupt signal received!\n");
    // Context switch would occur here in a real OS
}

int main() {
    signal(SIGINT, signal_handler); // Register interrupt handler

    while(1) {
        printf("Running...\n");
        sleep(1); // Simulate CPU burst
    }

    return 0;
}
```

## 4. Non-Preemptive Scheduling

*   **Definition:** A process keeps the CPU until it voluntarily releases it.
*   **Conditions:**
    *   Process switches from running to waiting state (e.g., I/O request).
    *   Process terminates.
*   **Advantages:**
    *   Lower overhead (less context switching).
    *   Simpler to implement.
*   **Disadvantages:**
    *   Poor response time.
    *   A long-running process can starve other processes.

### Example (Non-Preemptive)

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    printf("Process started\n");
    sleep(5); // Simulate long CPU burst
    printf("Process finished\n");

    return 0;
}
```

## Summary Table

| Feature           | Preemptive                  | Non-Preemptive               |
| ----------------- | --------------------------- | ---------------------------- |
| CPU Release       | Involuntary                 | Voluntary                    |
| Context Switching | More Frequent             | Less Frequent                |
| Response Time     | Better                      | Worse                        |
| Overhead          | Higher                      | Lower                        |
| Fairness          | More Fair                   | Less Fair                    |
