# Process Termination 

## 1. What is Process Termination?
> Process termination is the completion or stopping of a process by the operating system

## 2. Normal Termination Reasons 🎯

1. **Natural Completion**
   - Process finishes its task
   - Returns from main method
   - Calls `exit()` system call

```c
// Example of normal termination
int main() {
    // Process tasks
    return 0;    // Normal termination
}
```

2. **User Request**
   - User closes application
   - Logout command
   - Keyboard interrupt (Ctrl+C)

## 3. Abnormal Termination Reasons

1. **Fatal Errors**
   - Segmentation fault
   - Memory access violation
   - Division by zero
   - Invalid instruction

2. **Resource Limits**
   - Memory exhaustion
   - Time limit exceeded
   - CPU usage limits

3. **System Requirements**
   - System shutdown
   - Resource reallocation
   - Priority adjustments

## 4. Parent Terminating Child Processes

### Common Reasons
1. **Child exceeds resource limits**
   - CPU time
   - Memory usage
   - File descriptors

2. **Task no longer needed**
   - User cancels operation
   - Parent process changing tasks

3. **Parent terminating**
   - Cascading termination
   - System cleanup

```c
// Example of parent terminating child
pid_t child_pid = fork();
if (child_pid > 0) {  // Parent
    kill(child_pid, SIGTERM);  // Terminate child
}
```

## 6. Resource Cleanup 

- Close open files
- Release memory
- Remove temporary files
- Free system resources
- Update process tables