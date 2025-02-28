# Virtual Memory Management Guide

## 1. Virtual Memory Basics

### Definition
Virtual memory is a memory management technique that provides an idealized abstraction of storage resources to users and enables processes to use more memory than physically available.

```ascii
Virtual Memory Architecture
-------------------------
Virtual Address Space         Physical Memory
┌──────────────┐             ┌──────────────┐
│  Page 1      │------------>│  Frame 3     │
├──────────────┤             ├──────────────┤
│  Page 2      │     ┌------>│  Frame 1     │
├──────────────┤     │      ├──────────────┤
│  Page 3      │-----┘      │  Frame 4     │
├──────────────┤            ├──────────────┤
│  Page 4      │-----┐      │  Frame 2     │
└──────────────┘     │      └──────────────┘
                     ▼
              ┌──────────────┐
              │  Disk Storage│
              └──────────────┘
```

## 2. Demand Paging

### Core Concept
- Pages loaded only when requested
- Uses page fault mechanism
- Requires page table with valid/invalid bits

```markdown
Page Table Entry Format:
[Valid bit | Modified bit | Referenced bit | Protection bits | Page Frame Number]
```

### Page Fault Handling
```ascii
Page Fault Process
-----------------
1. Trap to OS
   ↓
2. Save registers
   ↓
3. Locate page on disk
   ↓
4. Read page into frame
   ↓
5. Update page table
   ↓
6. Restart instruction
```

## 3. Page Replacement Algorithms

### 1. FIFO (First-In-First-Out)
```python
# Example implementation
class FIFO:
    def __init__(self, capacity):
        self.capacity = capacity
        self.pages = []

    def page_fault(self, page):
        if page not in self.pages:
            if len(self.pages) >= self.capacity:
                self.pages.pop(0)  # Remove oldest
            self.pages.append(page)
            return True
        return False
```

### 2. Optimal Page Replacement
- Replaces page that won't be used for longest time
- Theoretical algorithm (requires future knowledge)

### 3. LRU (Least Recently Used)
```ascii
LRU Implementation
-----------------
Counter Method:        Stack Method:
┌────┬────────┐       ┌────┐
│Page│Counter │       │Most│ Page 1
├────┼────────┤       ├────┤
│ 1  │  100   │       │    │ Page 4
│ 2  │   85   │       ├────┤
│ 3  │   95   │       │    │ Page 2
└────┴────────┘       └────┘
                      Least
```

## 4. Advanced Concepts

### Working Set Model
```ascii
Working Set Window
----------------
Time →  t-Δ ... t
Pages: {2,3,5,1,2,3,4}
Working Set = {1,2,3,4}
```

### Thrashing
- Condition: Excessive paging
- Cause: Too many active pages for available frames
- Solution: Working set management

```ascii
Thrashing Graph
--------------
   CPU
   Use
    ↑
    │    ╭─────╮
    │   ╱      ╲
    │  ╱        ╲____
    │ ╱              ╲
    │╱                ╲
    └─────────────────→
        Degree of
    Multiprogramming
```

## 5. Memory Management Policies

### Frame Allocation
1. **Equal Allocation**
   - Each process gets same number of frames
2. **Proportional Allocation**
   - Allocation based on process size
3. **Priority Allocation**
   - Based on process priority

### Page Buffering
- Modified pages list
- Free frame buffer
- Multiple free frames ready

## 6. Performance Improvements

1. **Copy-on-Write**
   - Share pages until modification
   - Create copies only when needed
   
2. **Page Size Selection**
   - Larger pages: Less overhead
   - Smaller pages: Less internal fragmentation

3. **TLB Management**
   - Fast translation cache
   - Reduce memory access time

```ascii
Performance Graph
---------------
Page    │    ╭───
Fault   │   ╱
Rate    │  ╱
        │ ╱
        │╱
        └──────────
          Number of
          Frames
```

