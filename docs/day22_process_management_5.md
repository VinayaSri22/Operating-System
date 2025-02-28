# Process Management in Unix/Linux Systems

## 1. Viewing Process Information (`ps -ef`)

### Command Explanation
```bash
ps -ef  # e: all processes, f: full format listing
```

### Sample Output Explained
```plaintext
UID   PID  PPID  C    STIME    TTY       TIME     CMD
root  1    0     0    Jan01    ?         00:00:01 /sbin/init
root  2    1     0    Jan01    ?         00:00:00 [kthreadd]
john  1234 1     0    10:00    pts/0     00:01:23 bash
john  1456 1234  0    10:05    pts/0     00:00:05 firefox
```

### Column Meanings
- `UID`: User ID who owns process
- `PID`: Process ID
- `PPID`: Parent Process ID
- `C`: CPU utilization
- `STIME`: Start time
- `TTY`: Terminal type
- `TIME`: CPU time used
- `CMD`: Command/Program name

## 2. Process Tree Example

```plaintext
init(1)─┬─sshd(854)───sshd(1234)───bash(1235)
        ├─firefox(1456)─┬─firefox(1457)
        │               └─firefox(1458)
        └─chrome(1500)───chrome(1501)
```

## 3. Kill Commands

### Basic Kill Commands
```bash
kill PID           # Normal termination signal (SIGTERM)
kill -9 PID        # Force kill (SIGKILL)
killall firefox    # Kill all processes named 'firefox'
```

### Parent-Child Process Kill Behavior
- When parent is killed, children become orphans
- Orphans are adopted by `init` process (PID 1)
- To kill parent and children:
```bash
pkill -TERM -P PPID  # Kill all children of PPID
```

## 4. Finding Parent Process Info

### From Child Process
```bash
# Get parent PID of current process
ps -o ppid= -p $$

# Get parent process info
ps -fp $PPID

# Using pstree to visualize
pstree -p PID
```

## 5. Useful Process Commands

### Process Tree Visualization
```bash
pstree          # Show process tree
pstree -p       # Show PIDs
pstree -u       # Show user names
```

### Process Information
```bash
ps aux          # Detailed process list
top             # Real-time process monitoring
htop            # Interactive process viewer
```

## Important Notes 🔑

1. **Signal Types**
   - SIGTERM (15): Graceful termination
   - SIGKILL (9): Forced termination
   - SIGHUP (1): Hangup signal

2. **Best Practices**
   - Always try SIGTERM first
   - Use SIGKILL as last resort
   - Check process ownership before killing

3. **Safety Tips**
   - Verify PID before killing
   - Don't kill system processes
   - Be careful with `kill -9`