# Computer System Architecture and OS Fundamentals Notes

## 1. Computer System Structure
- Essential for understanding OS operations
- Core components form the foundation of modern computing

### Basic Architecture
```plaintext
+----------------+     +------------------+
|      CPU       |     | Memory Controller|
|   (one/multi)  |<--->|    & Memory     |
+----------------+     +------------------+
        ^                      ^
        |                      |
        v                      v
+----------------------------------------+
|               System Bus                 |
+----------------------------------------+
        ^                      ^
        |                      |
        v                      v
+----------------+     +------------------+
|    Device      |     |     Device      |
| Controllers    |     |   Controllers    |
+----------------+     +------------------+
```

## 2. Key Components

### CPU (Central Processing Unit)
- **Functions**:
  - Instruction execution
  - Data processing
  - System control
- **Characteristics**:
  - Can be single or multi-core
  - Connects to system bus
  - Direct access to memory

### Device Controllers
- **Purpose**: Interface between hardware and system
- **Features**:
  - Local buffers
  - Special registers
  - Independent operation
- **Examples**:
  ```plaintext
  - Disk controller
  - USB controller
  - Network adapter
  ```

### Memory Controller
- **Primary Functions**:
  - Synchronizes memory access
  - Manages concurrent requests
  - Ensures data integrity
- **Importance**:
  - Prevents memory conflicts
  - Optimizes memory performance

## 3. System Components

### Bootstrap Program
- **Location**: ROM/EPROM
- **Purpose**: Initial system startup
- **Process**:
```plaintext
1. Power ON
2. Load bootstrap
3. Initialize hardware
4. Load OS kernel
5. Transfer control
```

### Kernel
- Core of operating system
- Always resident in memory
- Manages critical resources

### System Communication

#### Interrupts
- **Types**:
  - Hardware
  - Software
  - Timer
- **Flow**:
```plaintext
Event → Interrupt Signal → Save State → 
Handle Interrupt → Restore State → Resume
```

#### System Calls
- Interface between user programs and OS
- **Common Categories**:
```plaintext
- Process Management
- File Operations
- Device Management
- Information Maintenance
- Communications
```

## Summary
- Computer system integrates multiple components
- Memory controller ensures orderly memory access
- Bootstrap initiates system operation
- Interrupts and system calls enable OS-program interaction