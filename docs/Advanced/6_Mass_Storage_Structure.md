# Mass Storage Structure Guide

## 1. Basic Concepts

### What is Mass Storage?
Mass storage refers to various techniques and devices used to store large amounts of data. These devices form the secondary storage tier in computer memory hierarchy.

### Storage Hierarchy
```ascii
                 ▲ Speed
                 │ Cost/GB
            ┌────────────┐
            │  Primary   │ (RAM, Cache)
            │  Storage   │ 
            ├────────────┤
            │ Secondary  │ (SSD, HDD)
            │  Storage   │
            ├────────────┤
            │ Tertiary   │ (Tape, Optical)
            │  Storage   │
            └────────────┘
                 │ Capacity
                 ▼ 
```

## 2. Magnetic Disks

### Structure and Components
```ascii
Disk Components
--------------
    ┌─── Read/Write Head
    ↓
    □ 
    │     ┌─── Track
    │     ↓
 ───┼──[═════]───
    │    Platter
    └── Actuator Arm
```

### Disk Parameters
- **Platter**: The circular disk where data is stored
- **Track**: Concentric circles on platter
- **Sector**: Smallest addressable unit
- **Cylinder**: Same track on all platters
- **Seek Time**: Time to move head to track
- **Rotational Latency**: Time for sector to rotate to head

## 3. Disk Scheduling

### Purpose
To minimize:
- Seek Time
- Rotational Latency
- Total Service Time

### Common Algorithms

1. **FCFS (First Come First Served)**
```ascii
Head Movement Pattern
     ↓ Current Position
0 ---●------------------- 199
     ↓    ↓    ↓    ↓
    98   183   37   122
```

2. **SSTF (Shortest Seek Time First)**
```ascii
Before:          After:
0 ---●---x--x--- 199    0 ---●→x→x---- 199
     ↓   2  1              ↓   1  2
    Head pos    (Numbers show order of service)
```

3. **SCAN (Elevator)**
```ascii
     Head Movement
        ↓
0 ←────●────→ 199
     Continuous back and forth
```

4. **C-SCAN (Circular SCAN)**
```ascii
        Retrace
0 ←─────●────→ 199
     ↑_________↓
```

## 4. RAID (Redundant Array of Independent Disks)

### RAID Levels
```ascii
RAID 0 (Striping)
Disk1  Disk2  Disk3
[A1]   [A2]   [A3]
[B1]   [B2]   [B3]

RAID 1 (Mirroring)
Disk1  Disk2
[A]    [A]
[B]    [B]

RAID 5 (Distributed Parity)
D1    D2    D3
[A1]  [A2]  [Ap]
[B1]  [Bp]  [B2]
[Cp]  [C1]  [C2]
```

### RAID Benefits
1. **Improved Reliability**
   - Data redundancy
   - Fault tolerance
   - Hot-swapping capability

2. **Better Performance**
   - Parallel operations
   - Load balancing
   - Improved throughput

## 5. Tertiary Storage

### Types
1. **Optical Storage**
   - CD-ROM
   - DVD
   - Blu-ray

2. **Magnetic Tape**
   - Sequential access
   - High capacity
   - Low cost per GB

### Characteristics
```ascii
Access Pattern
-------------
Tape:      |←───Sequential───→|
Disk:      |←Random Access →|
Memory:    |Instant Access|
```

## 6. Storage Area Network (SAN)

```ascii
SAN Architecture
---------------
┌────────┐     ┌────────┐
│Server 1├────→│Storage │
├────────┤     │Network │
│Server 2├────→│        │
├────────┤     │        │
│Server 3├────→│        │
└────────┘     └────────┘
```

## 7. Bad Blocks Management

### Methods
1. **Sector Sparing**
   - Reserve good sectors
   - Remap bad sectors

2. **Sector Slipping**
   - Shift sectors to skip bad ones
   - Maintain sequential access

```ascii
Bad Block Handling
-----------------
Original: [1][2][X][4][5]
Slipped:  [1][2][4][5][-]
Spared:   [1][2][S][4][5]
```

## 8. Storage Management Best Practices

1. **Performance Optimization**
   - Choose appropriate RAID levels
   - Implement effective scheduling
   - Regular defragmentation

2. **Reliability Measures**
   - Regular backups
   - SMART monitoring
   - Redundancy implementation

3. **Capacity Planning**
   - Growth monitoring
   - Space allocation
   - Storage tiering

