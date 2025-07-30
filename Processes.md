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




