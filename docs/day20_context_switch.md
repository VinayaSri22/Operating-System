# Context Switching 

## What is Context Switching?
> Think of it like saving your game progress before switching to another game

### Definition
- Process of saving and restoring state of a CPU
- Allows multiple processes to share a single CPU
- Essential for multitasking operating systems

## Components Involved in Context Switch

### Process Control Block (PCB)
- **Program Counter**: Address of next instruction
- **CPU Registers**: Current register contents
- **Memory Info**: Memory mapping information
- **I/O State**: List of allocated I/O devices
- **Scheduling Info**: Process priority, queue pointers

```c
struct PCB {
    int process_id;
    int process_state;      // running, ready, blocked
    int program_counter;    // next instruction
    int cpu_registers[16];  // register values
    int memory_limits;      // memory boundaries
    // other process info
};
```

## Context Switch Process Flow

1. **Interrupt or System Call Occurs**
   - Higher priority process needs CPU
   - Current process time quantum expires
   - I/O request made by process

2. **Save Current State**
   - Save all CPU registers
   - Update PCB of current process
   - Move process to appropriate queue

3. **Load New Process**
   - Load PCB of new process
   - Update memory management
   - Load new process registers

## Performance Considerations

### Overhead Involved
- Time spent saving/restoring registers
- Cache/pipeline flushing
- Memory mapping updates

### Reducing Context Switch Impact
1. Efficient process scheduling
2. Optimal time quantum selection
3. Proper interrupt handling

## Key Takeaways
1. Context switching enables multitasking
2. PCB stores process state information
3. Interrupts trigger context switches
4. Involves overhead but necessary for modern OS
