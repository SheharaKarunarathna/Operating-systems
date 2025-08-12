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
 
