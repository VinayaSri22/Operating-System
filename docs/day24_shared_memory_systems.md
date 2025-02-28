# Shared Memory Systems

## 1. Shared Memory Systems

### Basic Concept
- Region of memory shared between processes
- Faster IPC method (direct memory access)
- Requires explicit synchronization

```markdown
Process A ↔ [Shared Memory Region] ↔ Process B
```

### Implementation Example
```c
// Creating shared memory segment
#include <sys/shm.h>
#include <sys/stat.h>

// Create segment
int segment_id = shmget(KEY, SIZE, S_IRUSR | S_IWUSR);

// Attach to shared memory
char *shared_memory = (char *)shmat(segment_id, NULL, 0);
```

## 2. Producer-Consumer Problem 

### Overview
- Classic synchronization problem
- Two processes sharing fixed-size buffer
- Producer: Generates data
- Consumer: Uses data

```markdown
Producer → [Buffer] → Consumer
```

### Real-world Examples
1. Print spooler (Producer: Apps, Consumer: Printer)
2. Web Server (Producer: Web App, Consumer: Client)
3. Video Streaming (Producer: Video Source, Consumer: Player)

## 3. Buffer Types 

### 1. Unbounded Buffer
```markdown
Producer → [∞ Buffer Size] → Consumer
```
- **Characteristics**:
  - No size limit
  - Producer never waits
  - Consumer must wait if buffer empty
  - Theoretical concept (infinite memory)

### 2. Bounded Buffer
```markdown
Producer → [Fixed Size Buffer] → Consumer
```
- **Characteristics**:
  - Fixed size buffer
  - Producer waits if buffer full
  - Consumer waits if buffer empty
  - Practical implementation

## 4. Synchronization Requirements 

### Producer Must Check:
- Buffer full condition
- Update buffer pointers
- Signal consumer

### Consumer Must Check:
- Buffer empty condition
- Update buffer pointers
- Signal producer

## 5. Common Issues 🚫

1. **Race Conditions**
   - Simultaneous buffer access
   - Inconsistent count updates

2. **Deadlocks**
   - Producer waiting for full buffer
   - Consumer waiting for empty buffer

3. **Buffer Overflow/Underflow**
   - Producing to full buffer
   - Consuming from empty buffer

## Key Points to Remember 

1. Shared memory provides fast IPC
2. Buffer acts as temporary storage
3. Synchronization is crucial
4. Bounded buffers are practical
5. Need to handle race conditions

