# System Programs 

A system program is a specialized software that provides a convenient environment for program development and execution by offering an interface between the computer system and its users.

## Categories of System Programs

### 1. File Management
- **File operations:**
  - Create, delete, copy, rename, print
  - List directory contents
  - Search for files
```bash
dir                  # Windows
ls                   # Unix/Linux
copy source dest     # Windows
cp source dest       # Unix/Linux
```

### 2. Status Information
- **System monitoring:**
  - Date, time, disk space
  - Memory usage, CPU utilization
  - Number of users
```powershell
systeminfo           # Windows
top                  # Unix/Linux
```

### 3. File Modification
- **Text editors and processing:**
  - Create and modify text files
  - Search and transform content
```bash
notepad file.txt    # Windows
vim file.txt        # Unix/Linux
```

### 4. Programming Language Support
- **Language processing tools:**
  - Compilers
  - Assemblers
  - Debuggers
  - Interpreters
```bash
gcc program.c       # C compiler
javac Program.java  # Java compiler
```

### 5. Program Loading and Execution
- **Program loaders:**
  - Absolute loaders
  - Relocatable loaders
  - Linking loaders
- **Debugging systems**

### 6. Communications
- **Network connectivity:**
  - File transfer
  - Remote login
  - Email
```powershell
ping hostname       # Test connectivity
ftp hostname        # File transfer
ssh username@host   # Secure shell
```

## Key Points
- System programs provide convenient environment for program development
- Interface between system and users
- Most users view OS through system programs rather than system calls