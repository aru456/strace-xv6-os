# XV6 Strace Implementation

> **Note:** For source code and project files, please request access using this link: [Project Files on Google Drive](https://drive.google.com/drive/folders/1SsgSQtzfm3fPmHU-RCFkpP6EVy19QGq8?usp=sharing)

This project extends the XV6 operating system by implementing a custom version of strace, a debugging tool used to trace system calls. The project supports features like syscall filtering, selective tracing, and output formatting for enhanced debugging.

**Done by:** Sai Aravind Yanamadala 

## Features
- Trace system calls for active processes and child processes.
- System call filtering with `-e` to target specific calls (e.g., write, exec).
- Log only successful (`-s`) or failed (`-f`) system calls.
- Combine options (`-e`, `-s`, `-f`) for precise control.
- Suppress command output to display only strace logs.
- Structured log formatting for easier analysis.

## Implementation Details
### Files changed:
- `syscall.c`
- `syscall.h`
- `sysproc.c`
- `proc.h`
- `proc.c`
- `defs.h`
- `usys.S`
- `sys_write.c`
- `strace.c`
- `Makefile`

## Commands
- `strace on/off`: Enable or disable tracing.
- `strace run <command>`: Execute a command with tracing enabled.
  - Example: `strace run echo hello`
- `strace dump`: Output logs of system call events.

### Options
- `-e`: Focus on specific system calls.
- `-s`: Log only successful system calls.
- `-f`: Log only failed system calls.

#### Examples:
```
# Example 1: Filter specific system calls
strace -e write
echo hello

# Example 2: Log only successful system calls
strace -s
echo hello

# Example 3: Log only failed system calls
strace -f
echo hello
```

## Modified Files
- `syscall.c`: Handles system call logging.
- `sysproc.c`: Implements tracing system calls.
- `proc.h`: Adds tracing fields to process structures.
- `strace.c`: User-level interface for strace.
- `sys_write`: Supports output suppression.

## Installation and Setup
1. Clone the repository:
   ```
   git clone https://github.com/aravind-strace/xv6-strace
   cd xv6-strace
   ```

2. Build the project:
   ```
   make clean
   make
   ```

3. Run XV6:
   ```
   make qemu-nox
   ```

## Usage
### Basic Commands
- Enable tracing:
  ```
  strace on
  ```

- Disable tracing:
  ```
  strace off
  ```

- Execute a command with tracing:
  ```
  strace run <command>
  ```

- Dump logs:
  ```
  strace dump
  ```

- Test child processes:
  ```
  strace on
  strace_test
  ```

### Options Usage
- Filter specific system calls:
  ```
  strace -e write
  echo hello
  ```

- Log only successful system calls:
  ```
  strace -s
  echo hello  # or any invalid command
  ```

- Log only failed system calls:
  ```
  strace -f
  invalid_command  # e.g., echhhh
  ```

You can also combine options for more precise control over the tracing functionality.