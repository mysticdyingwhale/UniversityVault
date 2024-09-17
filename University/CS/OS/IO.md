# I/O
#cs 

I/O devices are just input and output devices like keyboards, mice, and speakers.

## I/O Architecture

![[Pasted image 20240511174758.png|400]]


## CPU/Device Interaction


Mechanics of Communication
- Explicit I/O instructions
	- `boot.c`
	- `keyboard_readc()`
	- `console_show_cursor()`
- Memory mapped I/O
	- `console_putc()`
	- Note the same as virtual memory, talking about physical address
		- Abstraction hardware provides to OS
- Interrupts
- Via physical memory

Polling vs Interrupts
- **Polling:** Checking back periodically
	- Wastes CPU cycles if device is not busy and higher latency
- **Interrupts:** Device Interrupts the CPU when its status changes (data is ready/fully written)
	- If interrupt rate is high then the computer spends a lot of time handling interrupts
		- Expensive since interrupts generate a [[Context-Switching, User-level Threading|context switch]] 

DMA vs Programmed I/O
- **Programmed I/O:** What we've seen so far
	- CPU writes data directly to device and reads data directly from device
- **DMA:** Device directly reads from (or writes to) memory
	- Initial CPU <-> device coordination is required
	- Tells device where the buffers are then pokes the device by writing to register
	- Device uses DMA to read or write the buffers and the CPU can poll to see if the DMA completed

## Device Drivers

Device drivers in general solve a software engineering problem. 
![[Pasted image 20240511202718.png|400]]


A driver exposes a well-defined interface to the kernel so that the kernel can call comparatively simple read/write calls or whatever else it may need to do.

This abstracts away non-standard/complex hardware details so that the kernel doesn't have to understand them. When you write a driver you are implementing this interface, and also calling functions that the kernel itself exposes.

Device drivers also create software engineering problems:

 - Each device driver is per-OS and per-device
 - Often written by device manufacturer, who are more competent at hardware development than software development
 - Under conventional kernel architectures, bugs in device drivers bring down the entire machine

Sketchy drivers aside, sketchy devices are also a concern

- A buggy network card can scribble all over memory
- Plug in a USB stick that pretends to be a keyboard, it starts issuing commands
- Plug in a USB stick, if it carries malware your computer is now infected


## Synchronous vs Asynchronous I/O

Synchronicity of I/O is a question of interface presented to user-level processes.

Synchronous I/O: system calls block until they're handled

Asynchronous I/O: 
- I/O doesn't block. 
- For example:
	- If a call like `read()`**would** block then it instead returns immediately but sets a flag indicating that it **would have** blocked
	- Process discovers that data is ready either by making another query or by registering to be notified by a signal
- Standard POSIX interface for files is blocking
- + Blocking interface leads to more readable code, when considering the code that invokes that interface
- - Blocking interfaces still block, which means that the code above the interface cannot suddenly switch to doing something else. 
	- If we want concurrency it has to be handled by a layer underneath the blocking interface.

NOTE: kernel never blocks when issuing I/O. We're discussing the interface presented to user-level processes.



## `mmap()`

Recall some syscalls:

`fd = open(pathname,mode)`
`write(fd,buf,sz)`
`read(fd,buf,sz)`

A file descriptor (`fd`) indexes into a table maintained by the kernel on behalf of the process

`void* mmap(void* addr, size_t len, int prot, int flags, int fd, off_t offset);`

Map the specified open file (`fd`) into a region of my virtual memory (close to `addr`, or at a kernel-select place if `addr` is 0), and return a pointer to it.

![[Pasted image 20240512120459.png|400]]

Usage examples:
- Enables copying a file to `stdout` without transferring data to user space
- Reading big files. Map the whole thing, rely on the paging mechanism to bring the needed pieces into memory as necessary
- Shared data structures, when flag is `MAP_SHARED`
- File based data structures
	- load data from a file, update it, write it back
	- Implemented entirely with loads and stores

How is `mmap()` implemented? 
- Through virtual memory
- `VA` is `addr`, `PA` is the physical address storing the given page in the kernel's buffer cache

NOTE:
- Have to deal with eviction from buffer cache, so kernel will need a data structure that maps from: `Phys page --> {list of (proc,va) pairs}`
- Kernel needs this data structure anyways
	- When a page is evicted from RAM the kernel needs to be able to invalidate the given virtual address in the page table(s) of the process(es) that have the page mapped
