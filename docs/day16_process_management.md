# Operating System Process Management

## Processes
- A process is a program in execution
- Contains:
  - Code (Text) section
  - Data section (global variables)
  - Stack (temporary data)
  - Heap (dynamically allocated memory)
- Has a Process Control Block (PCB) containing:
  - Process ID
  - Process State
  - Program Counter
  - CPU registers
  - Memory limits
  - List of open files

## Threads
- Lightweight unit of execution within a process
- Share process resources:
  - Code section
  - Data section 
  - OS resources
- Have their own:
  - Thread ID
  - Program counter
  - Register set
  - Stack

## Key Differences

| Process | Thread |
|---------|--------|
| Independent execution unit | Subset of a process |
| Has own memory space | Shares memory with other threads |
| Higher creation overhead | Lower creation overhead |
| More expensive context switch | Less expensive context switch |
| Communication is inter-process | Communication is intra-process |

## List Process Information on Windows

1. **Task Manager** (GUI):
- Press `Ctrl + Shift + Esc` or right-click taskbar and select "Task Manager"
- Go to "Processes" tab for basic info
- Go to "Details" tab for more technical information
- Go to "Performance" tab for system-wide metrics

2. **Using PowerShell commands**:
```powershell
# List all processes
Get-Process

# Get detailed process information
Get-Process | Select-Object Name, Id, CPU, WorkingSet, Threads | Format-Table

# Get thread information for a specific process (replace notepad with process name)
Get-Process notepad | Select-Object -ExpandProperty Threads
```

3. **Using Command Prompt**:
```batch
# List all processes
tasklist

# Get detailed process information including threads
tasklist /v

# Show process and thread performance info
typeperf "\Process(*)\Thread Count"
```

4. **Resource Monitor**:
- Press `Windows + R`
- Type `resmon` and press Enter
- Check the "CPU" tab for detailed process and thread information

The Resource Monitor and Task Manager provide real-time visual monitoring, while the command-line tools are better for scripting or automation purposes.