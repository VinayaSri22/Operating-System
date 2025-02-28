# Message Passing Systems (Part 2) Notes

## Direct Communication

### Characteristics
- Processes must explicitly name communication partners
- One link per process pair
- Bi-directional communication link

### Types
1. **Symmetric Addressing**
   - Both sender and receiver specify each other
   - Example:
```python
# Symmetric Addressing
def send(recipient_process, message)
def receive(sender_process, message)
```

2. **Asymmetric Addressing**
   - Only sender names the recipient
   - Receiver can accept from any source
```python
# Asymmetric Addressing
def send(recipient_process, message)
def receive(sender_id, message)  # sender_id assigned automatically
```

### Limitations
- Hard-coded process naming
- Lack of modularity
- Process identity changes require code updates

## Indirect Communication (Mailbox)

### Properties
1. Shared mailbox required for communication
2. Multiple processes can share one link
3. Multiple links possible between process pairs

### Implementation Example
```python
class Mailbox:
    def __init__(self, mailbox_id):
        self.id = mailbox_id
        self.messages = []

    def send(self, message):
        self.messages.append(message)

    def receive(self):
        if self.messages:
            return self.messages.pop(0)
        return None
```

### Advantages
- Better modularity
- Dynamic process management
- Flexible communication patterns

### Disadvantages
- Additional overhead
- Potential bottlenecks
- Complex synchronization needs