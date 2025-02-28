# User Operating System Interface 

## 1. Command Line Interface (CLI)
- Text-based interface for OS interaction
- Commands typed directly into terminal/console
- Efficient for power users and automation
- Requires knowledge of command syntax

## 2. Graphical User Interface (GUI)
- Visual interface with icons, windows, menus
- Mouse/touch-based interaction
- User-friendly and intuitive
- Requires more system resources

## Command Interpreter (Shell)

A command interpreter is a program that reads and executes commands from the user or from files.

### Key Functions

1. **Command Processing**
- Reads commands from user
- Interprets the command syntax
- Executes appropriate programs

2. **Types of Command Interpreters**
- UNIX Shell (sh, bash, zsh)
- Windows Command Prompt (cmd.exe)
- Windows PowerShell

### Example Commands

```bash
# UNIX/Linux Shell Commands
ls -l           # List files
pwd             # Print working directory
echo "Hello"    # Display text
```

```batch
# Windows CMD Commands
dir             # List files
cd              # Show current directory
echo Hello      # Display text
```

```powershell
# PowerShell Commands
Get-ChildItem   # List files
Get-Location    # Show current directory
Write-Host      # Display text
```

### Common Shell Operations
```bash
# I/O Redirection
command > output.txt    # Output redirection
command < input.txt     # Input redirection

# Pipe Operations
command1 | command2     # Pipe output of command1 to command2

# Background Processing
command &              # Run command in background
```