# Types of System Calls

## 1. Process Control
System calls for managing processes and program execution.

```c
// Process Control System Calls Examples
pid_t pid = fork();        // Create new process
exit(0);                   // Terminate process
exec("program");           // Execute a program
wait(&status);            // Wait for child process
sleep(1000);              // Suspend process
```

## 2. File Manipulation
System calls for file operations.

```c
// File Management System Calls Examples
int fd = open("file.txt", O_RDWR);    // Open file
write(fd, buffer, size);              // Write to file
read(fd, buffer, size);               // Read from file
close(fd);                            // Close file
mkdir("directory");                   // Create directory
```

## 3. Device Manipulation
System calls for managing devices.

```c
// Device Management System Calls Examples
ioctl(fd, command, args);     // Control device
read(device_fd, buffer, n);   // Read from device
write(device_fd, buffer, n);  // Write to device
mount(device, path, flags);   // Mount device
unmount(device);              // Unmount device
```

## 4. Information Maintenance
System calls for managing system information.

```c
// Information Management System Calls Examples
time(&current_time);          // Get system time
getpid();                     // Get process ID
chmod("file.txt", mode);      // Change permissions
chown("file.txt", owner);     // Change ownership
uname(&system_info);          // Get system info
```

## 5. Communications
System calls for inter-process communication.

```c
// Communication System Calls Examples
pipe(fd);                     // Create pipe
socket(domain, type, proto);  // Create socket
connect(sockfd, addr, len);   // Connect to server
send(sockfd, msg, len, 0);    // Send data
recv(sockfd, buffer, len, 0); // Receive data
```

## Summary Table

| Type | Purpose | Examples |
|------|---------|----------|
| Process Control | Manage processes | fork(), exit(), exec() |
| File Manipulation | Handle files | open(), read(), write() |
| Device Manipulation | Control devices | ioctl(), read(), write() |
| Information Maintenance | System info | getpid(), time(), chmod() |
| Communications | Process communication | pipe(), socket(), send() |

## Key Points
- System calls provide interface between user programs and OS
- Different OS may have different implementations
- System calls are typically wrapped in API functions
- All system calls involve switching to kernel mode
- Error handling is crucial when using system calls