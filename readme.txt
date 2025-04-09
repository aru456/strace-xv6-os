XV6 Strace Implementation

This project extends the XV6 operating system by implementing a custom version of strace, a debugging tool used to trace system calls. The project supports features like syscall filtering, selective tracing, and output formatting for enhanced debugging.

Done by : Sai Aravind Yanamadala 


Features
Trace system calls for active processes and child processes.
System call filtering with -e to target specific calls (e.g., write, exec).
Log only successful (-s) or failed (-f) system calls.
Combine options (-e, -s, -f) for precise control.
Suppress command output to display only strace logs.
Structured log formatting for easier analysis.

Implementation Details
Files changed :
syscall.c
syscall.h
sysproc.c
proc.h
proc.c
defs.h
usys.S
sys_write.c
strace.c
Makefile


Commands
strace on/off: Enable or disable tracing.
strace run <command>: Execute a command with tracing enabled.
Example: strike run echo hello
strace dump: Output logs of system call events.
Options
-e: Focus on specific system calls.
-s: Log only successful system calls.
-f: Log only failed system calls.
Example1:
strace -e write
echo hello

Example2:
strace -s
echo hello

Example3:
strace -f
echo hello

Modified Files
syscall.c: Handles system call logging.
sysproc.c: Implements tracing system calls.
proc.h: Adds tracing fields to process structures.
strace.c: User-level interface for strace.
sys_write: Supports output suppression.


Installation and Setup
Clone the repository:git clone https://github.com/aravind-strace/xv6-strace
cd xv6-strace

Build the project:
make cleanmake
Run XV6:make qemu-nox

Usage
Commands
Enable tracing:strace on

Disable tracing:
Strace onstrace off

Execute a command with tracing:strace run <command>

Dump logs:
Strace onstrace dump
Test child processes:
strace on
strace_test

Options:
Filter specific system calls:command1 : strace -e <write>
Command2 : echo hello
Log only successful system callscommand1 : strace -s
Command2 : echo hello or invalid command

Log only failed system calls:command1: strace -f 
command2: invalid_command (echhhh)


You can also combine options as mentioned in the question.
