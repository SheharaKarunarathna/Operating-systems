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
## Process Control Block (PCB)

The Process Control Block (PCB) is a data structure maintained by the Operating System (OS) for every process.
It stores all the information needed to manage a process.

### 📦 Contents of a Process Control Block (PCB)

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
## Process creation

Parent process create children processes, which, in turn create other processes, forming a tree of processes
Generally, process identified and managed via a process identifier (pid)

Resource sharing options
```
• Parent and children share all resources
• Children share subset of parent’s resources
• Parent and child share no resources
▪ Execution options
• Parent and children execute concurrently
• Parent waits until children terminate
```
This processes behave like a tree hierarchy

 Parent and Child Processes
In systems like UNIX:
```
fork() → Creates a new (child) process.
exec() → Replaces the process memory with a new program.
Parent and child can execute concurrently or the parent can wait for the child.
```
## Process transition 

Process executes last statement and then asks the operating system to delete it using the exit() system call.
• Returns status data from child to parent (via wait())
• Process’ resources are deallocated by operating system

Parent may terminate the execution of children processes using abort() system call

Parent may terminate the execution of children processes using the abort() system call. Some reasons for doing so:
  • Child has exceeded allocated resources
  • Task assigned to child is no longer required
  • The parent is exiting, and the operating systems does not allow a child to continue if its parent terminates

Some systems terminate all the children when we terminate a process.
The parent process may wait for the termination of the child process using wait(). But The call returns status information and the pid of the terminated process
pid = wait(&status); 

```
If no parent waiting (did not invoke wait()) process is a zombie
If parent terminated without invoking wait(), process is an orphan
```

## Example for multiprocesses program
```
Program -  Google chrome
Processes-  Each tab
Threads-  Lightweight processes run in each tab.
```
### fork() system call 
This is used to create a new process by duplicating its parent process

## Inter Process Communication (IPC)

There are two types of processes:
1. Independent processes
2. Cooperative processes

Reasons for cooperative processes
* Information sharing
* Computation speedup
* Modularity
* Convenience

Two models of inter process communication (IPC)
1. Shared memory
2. Message passing


### Shared memory method

Fastest among IPC methods because processes access the shared data directly in memory rather than sending messages.

### Message passing

Unless using a shared memory this passes messages directly between processes

**What Is Message Passing?**
Message passing is a communication method where:
* Processes exchange data via messages.
* No shared memory is required.
* Used in distributed systems and when processes are isolated.

There are direct communication and indirect communication in message passing 
In indirect communication we make a mailbox and communicate through that mailbox.
The keywords we have are send() and recieve().

### Producer-Consumer Problem is a classic example of IPC 

What is the Producer-Consumer Problem?
* Producer: Generates data and puts it into a buffer.
* Consumer: Takes data out of the buffer and processes it.
* Buffer: Shared memory area or queue between the two processes.

The challenges are:
1. Race Conditions
If both producer and consumer access the buffer at the same time, they may interfere with each other, leading to corrupted data.

2. Overwriting (Buffer Overflow)
If the producer adds data when the buffer is full, it may overwrite data not yet consumed.

3. Underflow (Reading Empty Buffer)
If the consumer tries to consume when the buffer is empty, it may read invalid data.

4. Data Inconsistency
Improper access without locks may lead to inconsistent states (e.g., two producers writing to the same slot).

### Bounded buffer solution for the producer consumer problem
The Bounded Buffer is a specific solution to the Producer-Consumer problem where the shared buffer has a fixed size (bounded). It ensures that:<br>
* The producer waits if the buffer is full.<br>
* The consumer waits if the buffer is empty.
```
Because the buffer has a limited capacity, say size N. You can't insert more than N items, and you can't consume if it's empty.
```
### Difference between Pipes and Buffers
```
1. Pipe

A pipe is an IPC mechanism provided by the OS for communication between processes.
It connects a producer and a consumer so that data flows from one process to another.
Can be anonymous (between related processes) or named (FIFO) (between unrelated processes).

Operates in FIFO order.
Acts like a channel, not just storage.

2. Buffer

A buffer is a temporary memory area used to hold data.
Can exist inside a pipe, in a file system, or in user space.

Its main purpose is to store data temporarily to handle speed differences between producer and consumer.It does not provide a communication mechanism on its own — just storage.
```
