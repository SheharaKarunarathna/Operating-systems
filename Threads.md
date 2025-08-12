# Threads
**Concurrency → Multiple tasks start, run, and complete in overlapping time (may not run at the exact same instant(Multiple tasks start, run, and complete in overlapping time (may not run at the exact same instant.  
).<br>Parallelism → Multiple tasks run at the exact same time on different processors or cores.(Multiple tasks run at the exact same time on different processors or cores.)**
Example 
```
On a quad-core CPU, data parallelism could be each core processing a quarter of an image for filtering, while task parallelism could be one core compressing files, another encoding video, another running a database query, and another rendering graphics.
```
## Amdahl's law
Formula
```
𝑆max = 1/[(1−𝑃)+𝑃/𝑁]
```
​P = fraction of the program that can be parallelized  
N = number of processors/cores  
1−P = fraction that must run sequentially  

### User Threads

* Managed entirely by a user-level thread library in user space.
* The OS kernel is not aware of them.
* Faster to create/switch but if one thread blocks, all threads in that process block.
Example: Java green threads, POSIX pthread in user mode.

### Kernel Threads
* Managed directly by the operating system kernel.
* The OS knows and schedules each thread independently.
* More overhead but better CPU utilization — one thread can block without stopping others.
Example: Windows threads, Linux kernel threads.

## Thread mapping

1. Many-to-One

* Many user threads mapped to one kernel thread.

* Simple, but if one thread blocks, all block; can’t use multiple cores.
* Example: Early Java green threads.

2. One-to-One

* Each user thread maps to one kernel thread.
* Allows true parallelism, but thread creation has more overhead.
Example: Windows threads, Linux pthread (default).

3. Many-to-Many

* Many user threads mapped to many kernel threads (number of kernel threads ≤ number of user threads).
* Combines flexibility of user threads with benefits of kernel scheduling.
Example: Older Solaris threads, Windows ThreadPool.


 
