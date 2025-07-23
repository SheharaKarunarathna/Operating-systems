# Intro
## Inturreptions of a Computer system
### Interrupts allow the OS to respond to events (hardware or software) immediately and efficiently, by temporarily pausing the current process, running a handler, and then resuming. This forms the core of how modern OSes work.

1. Interrupt transfers to the ISR (interrupt service routine) to handle the interrupt through the interrupt vector
   This interrupt vector stores all the addresses of interrupt routines so it know what code should run for the each interrupt
2. Interrupt architecture must save the address of the interrupted instruction

  ``` Before jumping to the ISR, the CPU saves the address of the instruction it was executing.
  After handling the interrupt, the CPU resumes exactly where it left off, so nothing is lost.
   ```
3. Exceptions and Traps

These are the interrupts happen because of the software not the hardware. 
```
Ex-  zero division of a program
     system calls
```
### Interrupt handling process
1. Interrupt occurs
2. CPU pauses current execution
3. Find the correct handler (Checks the interrupt vector table to find the correct ISR)
4. Execute the ISR
5. Resume previous program

### Some examples for interruptions
1. Keyboard input
2. Mouse moment
3. Disk I/O completion interrupt
4. Timer interrupt
   
## Storage structure

1. Main memory –only large storage media that the CPU can access directly
```
• Random access
• Typically volatile
• Typicallyrandom-accessmemoryin the form of Dynamic Random-access Memory (DRAM)
```

2. Secondary storage –extension of main memory that provides large nonvolatile storage capacity

3. Hard Disk Drives (HDD) –rigid metal or glass platters covered with magnetic recording material
```
• Disk surface is logically divided intotracks, which are subdivided into sectors
• The disk controller determines the logical interaction between the device and the computer
```
4. Non-volatile memory(NVM)devices–faster than hard disks, nonvolatile
```
• Various technologies
• Becoming more popular as capacity and performance increases, price drops
``` 
