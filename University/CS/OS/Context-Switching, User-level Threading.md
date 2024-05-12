# Context-Switching, User-level Threading
#cs 



## User-level Threading

What is a kernel-managed (kernel-level) thread?
- Same as a process, except two threads in the same process have the same value for `%cr3`
- Kernel threads are always preemptive

We can also have user-level threads, where the kernel is completely ignorant of the existence of threading 
![[Pasted image 20240512121932.png|500]]

In this case, the threading package is the layer of software that maintains the array of TCBs (Thread Control Blocks)

Other responsibilities of the threading package:
- Make a new stack for each thread
- [[Scheduling]]

User-level threading can be preemptive and non-preemptive 

## Context Switches in User Space


A context switch is really just two things:
- Switching the view of memory (`%cr3`)
- Switching the registers

The first isn't relevant for user-level threading.


Thread switch function: 

`void swtch(tcb *current, tcb *next);`


Example use of `swtch()`

A thread is going about its business and decides that it’s executed for long enough. 

So it calls `yield()`.

```C
void yield()
{
	tcb* next = pick_next_thread();
	tcb* current = get_current_thread();
	swtch(next, current);
}
```

Kernels also need `swtch()`, to switch the **kernel** stack


### Cooperative Multithreading

Also called non-preemptive multithreading.

Means that a context switch takes place only at well-defined points:
- When the thread calls `yield()`
- When the thread would block I/O


### Preemptive Multithreading in user-level

We build a user-level threading package that does context switches at any time using signals:
- Deliver a periodic timer interrupt or signal to a thread scheduler. 
- When it gets interrupt, swap out thread, run another one

This makes programming with user-level threads more complex. 

It has all the complexity of programming with kernel-level threads but few of the advantages (except performance from fewer syscalls).

In practice systems aren't usually built this way, but it is sometimes what you want (if you're simulating some OS-like thing inside a process for example)

Signals are instructive, and are used for many things. What a signal is really doing is abstracting a key hardware feature: interrupts.