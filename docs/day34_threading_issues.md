# Threading Issues with Fork() and Exec() System Calls

## Two Versions of Fork

### 1. Single-Thread Fork
- Only duplicates the calling thread
- Lighter weight operation
- Used when `exec()` follows immediately
- Other threads in parent process are not duplicated

```cpp
#include <pthread.h>
#include <unistd.h>
#include <iostream>

void* threadFunction(void* arg) {
    // Thread work here
    return nullptr;
}

int main() {
    pthread_t thread;
    pthread_create(&thread, nullptr, threadFunction, nullptr);

    // Fork only current thread
    pid_t pid = fork();
    if (pid == 0) {
        // Child process - only this thread exists
        execl("/bin/ls", "ls", nullptr);
        exit(1);  // Only reached if exec fails
    }
    
    return 0;
}
```

### 2. Multi-Thread Fork
- Duplicates all threads in the process
- Heavier operation
- Used when child process needs to continue with multiple threads
- All threads from parent are replicated

```cpp
#include <pthread.h>
#include <unistd.h>
#include <iostream>
#include <vector>

std::vector<pthread_t> threads;

void* workerThread(void* arg) {
    while(true) {
        // Thread work here
        sleep(1);
    }
    return nullptr;
}

int main() {
    // Create multiple threads
    for(int i = 0; i < 3; i++) {
        pthread_t thread;
        pthread_create(&thread, nullptr, workerThread, nullptr);
        threads.push_back(thread);
    }

    // Fork all threads
    pid_t pid = fork();
    if (pid == 0) {
        // Child process - all threads continue running
        // Do work that requires multiple threads
    }
    
    return 0;
}
```

## Best Practices

### 1. Thread Safety
```cpp
// Use async-signal-safe functions between fork and exec
void prepareFork() {
    // Lock necessary resources
    pthread_mutex_lock(&globalMutex);
}

void parentFork() {
    // Parent process cleanup
    pthread_mutex_unlock(&globalMutex);
}

void childFork() {
    // Child process cleanup
    pthread_mutex_unlock(&globalMutex);
}

int main() {
    pthread_atfork(prepareFork, parentFork, childFork);
    // ... rest of the code
}
```

### 2. Resource Handling
```cpp
// Proper resource cleanup in child process
if (fork() == 0) {
    // Close unnecessary file descriptors
    for(int fd = 3; fd < getdtablesize(); fd++) {
        close(fd);
    }
    
    // Reset signal handlers
    signal(SIGTERM, SIG_DFL);
    
    execl("/path/to/program", "program", nullptr);
    exit(1);
}
```

## Common Issues to Avoid

1. **Deadlocks**
   - Mutex locked in parent remains locked in child
   - Use `pthread_atfork()` handlers

2. **Resource Leaks**
   - File descriptors
   - Memory allocations
   - Network connections

3. **Signal Handlers**
   - Reset signal handlers in child process
   - Use only async-signal-safe functions

4. **Thread Synchronization**
   - Be careful with shared resources
   - Clean up thread-specific data

