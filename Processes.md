# Processes of Operating systems
## What is a Process?
```A process is a program in execution.```
It is more than just the program code (called the text section); it includes:

1. Program code (what to execute)
2. Program counter (current instruction being executed)
3. Registers
4. Stack (function calls, parameters)
5. Heap (dynamically allocated memory)
6. Data section (global/static variables)

A process is like a container that holds everything needed to run a program.

```
📌 Example:
If you open a browser and open two tabs with two different websites:

The browser program is the same.
But the OS runs two different processes (each with its own memory and state).
```
**A program can have multiple processes**
## States of a process
1. New
```
The process is being created.
OS sets up necessary resources.
```

2. Ready
```
The process is waiting to be assigned to a CPU.
It is ready to run, but the CPU is busy with others
```
3. Running
```
The process is currently being executed on the CPU.
Only one process per CPU core can be in this state.
```
4. Waiting / Blocked
```
The process is waiting for an event (like I/O completion).
It cannot proceed until the event happens.
```
5. Terminated / Exit
```
The process has finished execution (successfully or by error).
OS cleans up its resources.
```

## 📦 Contents of a Process Control Block (PCB)

| 🔢 **Field**                 | 📄 **Description**                                      |
|-----------------------------|---------------------------------------------------------|
| **Process ID (PID)**        | Unique number to identify the process                  |
| **Process State**           | Current state (e.g., Ready, Running, Waiting)          |
| **Program Counter**         | Address of the next instruction to execute             |
| **CPU Registers**           | Contents of all registers (e.g., ACC, PC, SP) — saved/restored during context switches |
| **Memory Management Info**  | Page tables, segment tables, base/limit registers      |
| **Accounting Info**         | CPU usage, job priority, time limits, etc.             |
| **I/O Status Info**         | List of I/O devices allocated, files opened            |
| **Parent/Child Info**       | Parent and child process IDs (optional)                |


## Threads

a thread is a lightweight sub-process:
  It shares the process's code, data, and resources, but executes independently.
```
Processes are heavyweight: fully independent, with their own memory space.
Threads are lightweight: run within the same process, share memory, and can communicate easily.
```
## Context switching

Steps in a Context Switch
1. Save the current process's state to its PCB.
2. Select the next process from the ready queue.
3. Load the next process's state from its PCB.
4. Update the CPU's registers and program counter.

**What is Saved During a Context Switch?**

The context of a process includes:
```
Program Counter (PC)
CPU registers
Stack Pointer
Process State
Memory Management Info
All stored in the Process Control Block (PCB)
```
