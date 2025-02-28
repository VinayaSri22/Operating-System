# Message Passing Systems in Operating Systems

## Core Components

### 1. Basic Primitives
- send()
- receive()

### 2. Communication Types

#### Synchronous (Blocking)
```python
class SynchronousCommunication:
    def blocking_send(self, message):
        while not receiver.is_ready():
            wait()
        send_message(message)
        
    def blocking_receive(self):
        while queue.empty():
            wait()
        return queue.get()
```

#### Asynchronous (Non-Blocking)
```python
class AsynchronousCommunication:
    def non_blocking_send(self, message):
        queue.put(message)
        return  # Immediate return
        
    def non_blocking_receive(self):
        return queue.get() if not queue.empty() else None
```

### 3. Buffer Types

#### Zero Capacity
```python
class ZeroCapacityBuffer:
    def __init__(self):
        self.message = None
        
    def send(self, message):
        while self.message is not None:
            wait()  # Must wait for receiver
        self.message = message
```

#### Bounded Capacity
```python
class BoundedBuffer:
    def __init__(self, size):
        self.size = size
        self.queue = Queue(maxsize=size)
        
    def send(self, message):
        if self.queue.full():
            wait()
        self.queue.put(message)
```

#### Unbounded Capacity
```python
class UnboundedBuffer:
    def __init__(self):
        self.messages = []
        
    def send(self, message):
        self.messages.append(message)  # Never blocks
```

## Comparison Table

| Feature | Blocking | Non-Blocking |
|---------|----------|--------------|
| Send    | Waits for receiver | Returns immediately |
| Receive | Waits for message | Returns null if empty |

## Buffer Characteristics

| Buffer Type | Capacity | Sender Behavior | Use Case |
|-------------|----------|-----------------|-----------|
| Zero | 0 | Always blocks | Direct communication |
| Bounded | Fixed (n) | Blocks when full | Limited resources |
| Unbounded | Infinite | Never blocks | Resource-rich systems |

