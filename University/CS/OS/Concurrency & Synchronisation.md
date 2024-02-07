#cs 

# Concurrency


## Threads

Threads are used due to parallelism, essentially allowing a process to be run on multiple CPUs (cores) to make them run faster on modern hardware. 

The process of parallelisation involves taking a single-threaded process and making it multi-threaded.

It is also useful to avoid blocking program process due to slow I/O. While one thread in the process waits (blocked waiting for I/O), the CPU scheduler can switch to other threads that are ready to run. 

Threading enables overlap of I/O with other activities within a single program, much like muliprogramming did for processes across programs.
## Managing Concurrency

#### Critical Sections

Critical sections protect from concurrent execution:
- **Mutual exclusion** 
- Progress
- Bounded waiting

Protecting critical sections:
- `lock()/unlock()`
- `enter()/leave()`
- `acquire()/release()`

