# Fork and Exec System Calls

## Fork() System Call

### Basic Concept
- Creates a new process by duplicating the calling process
- The new process is called the child process
- The original process is called the parent process
- Child process is an exact copy of parent process

### Key Characteristics
1. **Process ID (PID)**
   - Parent gets child's PID as return value
   - Child gets 0 as return value
   - Returns -1 on failure

2. **Memory Space**
   - Creates separate memory space
   - Copies all variables and code
   - Changes in child don't affect parent

### Basic Example
```cpp
#include <iostream>
#include <unistd.h>

int main() {
    pid_t pid = fork();
    
    if (pid < 0) {
        // Fork failed
        std::cerr << "Fork failed!" << std::endl;
        return 1;
    } 
    else if (pid == 0) {
        // Child process
        std::cout << "Child process. PID: " << getpid() << std::endl;
    } 
    else {
        // Parent process
        std::cout << "Parent process. Child PID: " << pid << std::endl;
    }
    
    return 0;
}
```

## Exec() System Call

### Basic Concept
- Replaces current process with a new program
- Does not create new process
- PID remains unchanged
- Multiple variants: execl(), execv(), execle(), execve(), execlp(), execvp()

### Key Characteristics
1. **Process Replacement**
   - Completely replaces current process
   - No return unless error occurs
   - Maintains same PID

2. **Memory Space**
   - Clears existing memory
   - Loads new program
   - Previous code after exec() never executes if successful

### Basic Example
```cpp
#include <iostream>
#include <unistd.h>

int main() {
    std::cout << "Before exec()" << std::endl;
    
    // Replace current process with 'ls' command
    execl("/bin/ls", "ls", "-l", NULL);
    
    // This line only executes if execl() fails
    std::cout << "After exec() - This won't be printed if exec succeeds" << std::endl;
    
    return 0;
}
```

## Common Use Cases

1. **Shell Implementation**
   - Fork() to create new process
   - Exec() to run commands

2. **Process Creation**
   ```cpp
   if (fork() == 0) {
       // Child process
       execl("/path/to/program", "program", NULL);
       exit(1);  // Only reaches here if exec fails
   }
   ```

## Key Differences

| Feature | fork() | exec() |
|---------|--------|--------|
| Process ID | Creates new PID | Maintains same PID |
| Memory | Duplicates memory | Replaces memory |
| Control | Returns to next instruction | No return on success |
| Purpose | Create new process | Replace process content |
