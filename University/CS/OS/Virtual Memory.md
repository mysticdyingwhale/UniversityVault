# Virtual Memory
#cs 

Virtual Memory is when the OS builds an abstraction of a private, potentially large address space for multiple running processes (all sharing memory) on top of a single, physical memory.

The running program thinks it is loaded into memory at a particular address (say 0) and has a potentially very large address space (32 or 64 bit).

When a process tries to perform a load at address 0 (a virtual address), the OS, in tandem with hardware support, will have to make sure the load doesn't go to the physical address 0, but rather to the physical address where A is loaded into memory.


## Benefits of Virtual Memory

- Programmability 
	- Program thinks it has a lot of memory
	- Programs can use 'easy' addresses: compiler and linker don't have to worry about where program lives in physical memory
	- Multiple instances of a program can be loaded and not collide

- Protection
	- Processes cannot read/write each other memory
	- Enables isolation (which is essential)

- Effective use of resources
- Sharing

https://cs.nyu.edu/~mwalfish/classes/24sp/lectures/l11.txt
Translation of the virtual and physical addresses is done by the MMU (hardware). The OS sets up data structures that the hardware 'sees', associated per-process.

## Paging

Paging is the process of dividing memory (virtual + physical) into fixed-size chunks. These chunks are called pages.

Page Size: x86-64: 4096B = 4KB = $2^{12}$ bytes

https://cs.nyu.edu/~mwalfish/classes/24sp/lectures/l11.txt
### The Page Table

The page table is conceptually a map from the VPN (Virtual Page Number) to the PPN (Physical Page Number)

![[Pasted image 20240304164753.png|400]]





### Virtual Memory on `x86-64`

https://cs.nyu.edu/~mwalfish/classes/24sp/lectures/l12.txt
### Page Faults

https://cs.nyu.edu/~mwalfish/classes/24sp/lectures/l13.txt