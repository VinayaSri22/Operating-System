# File Systems and Storage Management Guide

## 1. Basic Concepts

### File Definition
A file is a named collection of related information stored on secondary storage.

```ascii
File Structure
-------------
┌─────────────────────┐
│     File Header     │
├─────────────────────┤
│                     │
│    File Content     │
│                     │
└─────────────────────┘
```

### File Attributes
```markdown
- Name: Human-readable identifier
- Type: Format/usage identifier
- Size: Current file size
- Location: Physical location pointer
- Protection: Access control info
- Time stamps: Creation, access, modification
- Owner: User identification
```

## 2. File Operations

### Basic Operations
```python
# Common File Operations
class FileOperations:
    def create(filename):
        # Creates new file
        pass
    
    def delete(filename):
        # Removes file
        pass
    
    def open(filename):
        # Opens for processing
        pass
    
    def close(filename):
        # Terminates processing
        pass
    
    def read(position, length):
        # Reads file content
        pass
    
    def write(position, data):
        # Writes to file
        pass
```

## 3. Directory Structures

### Hierarchy Types

```ascii
1. Single-Level Directory
------------------------
Root
├── file1
├── file2
└── file3

2. Two-Level Directory
---------------------
Root
├── user1/
│   ├── file1
│   └── file2
└── user2/
    ├── file3
    └── file4

3. Tree-Structure
----------------
/
├── bin/
│   ├── cmd1
│   └── cmd2
├── home/
│   ├── user1/
│   │   └── docs/
│   └── user2/
└── etc/
```

## 4. File System Implementation

### Disk Structure
```ascii
Disk Organization
----------------
┌──────┬──────┬──────┐
│Block1│Block2│Block3│...
└──────┴──────┴──────┘
```

### File Allocation Methods

1. **Contiguous Allocation**
```ascii
File A    File B    File C
┌────┬────┬────┐
│1234│5678│9ABC│
└────┴────┴────┘
```

2. **Linked Allocation**
```ascii
File Blocks
┌────┐    ┌────┐    ┌────┐
│Data│--->│Data│--->│Data│
└────┘    └────┘    └────┘
```

3. **Indexed Allocation**
```ascii
Index Block    Data Blocks
┌────┐        ┌────┐
│Ptr1├------->│Data│
├────┤        └────┘
│Ptr2├---┐    ┌────┐
├────┤   └--->│Data│
│Ptr3├-┐      └────┘
└────┘ │      ┌────┐
       └----->│Data│
              └────┘
```

## 5. File Sharing and Protection

### Access Control Matrix
```markdown
         File1  File2  File3
User1     rw     r      -
User2     r      rw     rw
User3     -      r      r
```

### Protection Bits
```ascii
File Permission Bits
-------------------
Owner   Group   Others
r w x   r w x   r w x
```

## 6. Remote File Systems

### Client-Server Model
```ascii
Client-Server Architecture
------------------------
Client        Server
┌────┐        ┌────┐
│App ├──────→ │File│
└────┘        │Sys │
  ▲           └────┘
  │             ▲
  └─────Response┘
```

### Network File System (NFS)
```python
# Basic NFS Operations
class NFSOperations:
    def mount(remote_path, local_path):
        # Mount remote filesystem
        pass
    
    def unmount(local_path):
        # Unmount filesystem
        pass
```

## 7. Consistency and Recovery

### File System Consistency
```markdown
- **Crash Consistency**: File system must remain consistent after system failure
- **Transaction Support**: All-or-nothing operations
- **Journaling**: Log-based recovery system
```

### Journaling Example
```ascii
Journal Structure
---------------
┌────────┬────────┬────────┐
│TxStart │Changes │TxCommit│
└────────┴────────┴────────┘
```

## 8. Modern Features

### Extended Attributes
```markdown
- Compression
- Encryption
- Versioning
- Snapshots
- Quotas
```

### Performance Optimizations
```ascii
Cache Structure
--------------
Memory      Disk
┌────┐      ┌────┐
│Cache├─────>│File│
└────┘      └────┘
```

## 9. Security Considerations

### Access Control Lists (ACL)
```python
class ACL:
    def __init__(self):
        self.permissions = {
            'user1': {'read': True, 'write': True},
            'user2': {'read': True, 'write': False}
        }
```

### Security Features
```markdown
1. File Encryption
2. Access Logging
3. Audit Trails
4. Mandatory Access Control
5. Role-Based Access Control
```