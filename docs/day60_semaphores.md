# Semaphores

## 1. Overview

*   **Definition:** A synchronization tool used to control access to shared resources in a concurrent environment.
*   **Purpose:** To manage access to critical sections and prevent race conditions.
*   **Mechanism:** An integer variable that, apart from initialization, is accessed only through two standard atomic operations: `wait()` and `signal()`.

## 2. Semaphore Operations

*   **`wait()` (also known as `P`):**
    *   Decrements the value of the semaphore.
    *   If the value becomes negative, the process executing `wait()` is blocked (added to the semaphore's waiting queue) until another process executes a `signal()` operation.
*   **`signal()` (also known as `V`):**
    *   Increments the value of the semaphore.
    *   If there are any processes blocked on the semaphore, one of them is unblocked (removed from the waiting queue).

### Pseudocode

```
wait(semaphore S) {
    S.value--;
    if (S.value < 0) {
        add this process to S.list;
        block(); // Block the process
    }
}

signal(semaphore S) {
    S.value++;
    if (S.value <= 0) {
        remove a process P from S.list;
        wakeup(P); // Wake up the process
    }
}
```

## 3. Types of Semaphores

### Binary Semaphores

*   **Definition:** A semaphore with an integer value that can only be 0 or 1.
*   **Purpose:** Used to implement mutual exclusion.
*   **Initialization:** Initialized to 1.
*   **Usage:**
    *   `wait()`: Decrements the value to 0, acquiring the lock.
    *   `signal()`: Increments the value to 1, releasing the lock.

### Counting Semaphores

*   **Definition:** A semaphore with an integer value that can range over an unrestricted domain.
*   **Purpose:** Used to control access to a resource with multiple instances.
*   **Initialization:** Initialized to the number of available resources.
*   **Usage:**
    *   `wait()`: Decrements the count when a process uses a resource.
    *   `signal()`: Increments the count when a process releases a resource.

## 4. Usage Examples

### Mutual Exclusion with Binary Semaphore

```
semaphore mutex = 1; // Initialize to 1

do {
    wait(mutex); // Acquire lock

    // Critical Section
    ...

    signal(mutex); // Release lock

    // Remainder Section
    ...
} while (TRUE);
```

### Resource Counting with Counting Semaphore

```
semaphore available = N; // N = number of resources

do {
    wait(available); // Acquire resource

    // Use resource
    ...

    signal(available); // Release resource

    // Remainder Section
    ...
} while (TRUE);
```

## 5. Advantages

*   **Generality:** Can be used to solve a wide range of synchronization problems.
*   **Flexibility:** Can be used to control access to single or multiple resources.

## 6. Disadvantages

*   **Complexity:** Can be complex to use correctly.
*   **Deadlock:** Improper use can lead to deadlocks.
*   **Busy Waiting (in some implementations):** Can lead to busy waiting if the `wait()` operation is not implemented correctly.