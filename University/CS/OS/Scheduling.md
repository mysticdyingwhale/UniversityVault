# Scheduling
#cs 

### Sheduling
#### Scheduling Decisions

The OS has to decide which process (or thread) to run.

Scheduling decisions happen when a process/thread:
- Switches from running to waiting
- Switches from running to ready
- Switches from waiting to ready
- Exits

#### Preemptive scheduling vs non-preemptive scheduling


Preemptive scheduling is used when a process: 
- switches from the running state to the ready state
- switches from the waiting state to the ready state

Resources are allocated to the process for a limited amount of time and then taken away

The process is placed back in the ready queue if that process still has CPU burst time remaining. 

That process stays in the ready queue till it gets its next chance to execute.


Non-preemptive scheduling is used when:
- A process terminates
- A process switches from running to waiting state.

**Preempting**: When we **preempt** a job, we run it partially then place it back on the queue to allow other jobs to run. 

**Burst Time:** Execution time. The amount of CPU time the process requires to complete execution.

#### Metrics and Criteria

- Turnaround time: time for each process/thread to complete 
- Waiting/response/output time: time spent waiting for something to happen
- System throughput: # of completed processes / time
- Fairness: Often conflicts with efficiency

#### Context switching 

Context switching has a cost:
- CPU time in kernel (save and restore registers, switch address spaces)
- Indirect costs (TLB shootdowns, processor cache, OS caches)

### Scheduling Disciplines

- Assume first that the process/threads do no I/O (unrealistic, we relax it later)
  
- FCFS (first come first served)/FIFO
	- run job until its done
	- Example:
		- P1 needs 24s, P2 needs 3s, P3 needs 3s
		- $\frac{\text{3 processes}}{24+3+3} = \frac{\text{3 processes}}{30s} = 0.1 \text{proc/sec}$ throughput
		- $\frac{24+27+30}{3}= 27s$ avg time taken
	- Very high average turnaround
	  
- SJF (Shortest Job First) / STCF (Shortest Time to Completion First)
	- SJF: Choose job with shortest upcoming CPU burst
	- STCF: preemptive version of SJF
		- We preempt 
	  
- RR (Round Robin) 
	- Also called Time Slicing
	- Add a timer
	- Instead of running jobs to completion, run for a time slice (scheduling quantum)
	- Scheduling Quantum:
		- What if jobs are the same length?
		- Example
			- 2 jobs of 50 time units each, quantum is 1
			- Average time taken: 99.5 quanta
			- With FCFS: 75 quanta
	- After each quantum

### Incorporating I/O


### Priority Scheme


### MLFQ

The multi-level feedback queue

### Lottery and Stride Scheduling

### Linux : CFS (Completely Fair Scheduler)

Implements fair-share scheduling using a form of stride scheduling, a deterministic fair-share scheduler.

The goal is simple: to fairly divide a CPU evenly among all competing processes. 

It does so through a simple counting-based technique known as virtual runtime (`vruntime`).

In the most basic case, each process’s `vruntime` increases at the same rate, in proportion with physical (real) time. 

When a scheduling decision occurs, CFS will pick the process with the lowest `vruntime` to run next.
#### Stride Scheduling

Each job in the system has a stride, which is inverse in proportion to the number of tickets it has. 

We call this value the stride of each process; every time a process runs, we will increment a counter for it (called its pass value) by its stride to track its global progress.

