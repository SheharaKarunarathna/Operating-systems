# Intro
## Inturreptions of a Computer system
1. Interrupt transfers to the ISR (interrupt service routine) to handle the interrupt through the interrupt vector
   This interrupt vector stores all the addresses of interrupt routines so it know what code should run for the each interrupt
2. Interrupt architecture must save the address of the interrupted instruction

  Before jumping to the ISR, the CPU saves the address of the instruction it was executing.
  After handling the interrupt, the CPU resumes exactly where it left off, so nothing is lost.
3. Exceptions and Traps

These are the interrupts happen because of the software not the hardware. 
```
Ex- * zero division of a program
    * system calls
```
