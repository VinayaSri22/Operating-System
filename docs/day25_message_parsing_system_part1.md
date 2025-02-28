# Message Passing Systems (Part 1)

## Core Concepts

### 1. Message Passing System Overview
- Enables inter-process communication without shared memory
- Ideal for distributed systems across networked computers
- Essential for processes on different physical machines

### 2. Basic Operations
- **SEND**: Transmits message to destination process
- **RECEIVE**: Accepts message from source process

### 3. Message Types
| Type | System Implementation | Programming Perspective |
|------|----------------------|------------------------|
| Fixed Size | Easier | More challenging |
| Variable Size | More complex | More flexible |

### 4. Communication Link Methods

#### a) Communication Style
- Direct Communication
- Indirect Communication

#### b) Timing Mechanism
- Synchronous Communication
- Asynchronous Communication

#### c) Buffer Management
- Automatic Buffering
- Explicit Buffering

## Associated Challenges
- Process naming and addressing
- Synchronization mechanisms
- Buffer management
- Message size handling
- Communication reliability
