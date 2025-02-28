# Process Control Block (PCB) 

A Process Control Block (PCB) is a data structure maintained by the operating system for each process. It's essential for process management and contains crucial information needed to manage processes effectively.

## Key Components

### 1. Process ID (PID)
- Unique numerical identifier assigned to each process
- Used by OS to track and manage processes
- Example in Unix/Linux systems: Numbers from 0 to 32,767

### 2. Process State
- Current state of the process:
  - New
  - Ready
  - Running
  - Waiting
  - Terminated

### 3. Program Counter (PC)
- Contains the address of next instruction to be executed
- Crucial for resuming process execution after interruption
- Updated after each instruction execution

### 4. CPU Registers
Stores various types of registers:
- Accumulators
- Index registers
- Stack pointers
- General-purpose registers
- Condition codes

### 5. CPU Scheduling Information
- Process priority
- Scheduling queue pointers
- Other scheduling parameters
- CPU scheduling algorithm information

### 6. Memory Management Information
- Base register
- Limit register
- Page tables
- Segment tables
- Memory allocation details

### 7. Accounting Information
- CPU time used
- Real time used
- Time limits
- Account numbers
- Job/process numbers
- Process privileges

### 8. I/O Status Information
- List of I/O devices allocated
- List of open files
- I/O requests pending
- I/O device status

## Visual Representation
```ascii
+------------------------+
|     Process ID        |
+------------------------+
|    Process State      |
+------------------------+
|   Program Counter     |
+------------------------+
|    CPU Registers      |
+------------------------+
| Scheduling Information|
+------------------------+
| Memory Management     |
+------------------------+
| Accounting Info       |
+------------------------+
|    I/O Status        |
+------------------------+
```