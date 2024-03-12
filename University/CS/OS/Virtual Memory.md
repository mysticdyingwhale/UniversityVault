# Virtual Memory
#cs 

Virtual Memory is when the OS builds an abstraction of a private, potentially large address space for multiple running processes (all sharing memory) on top of a single, physical memory.

The running program thinks it is loaded into memory at a particular address (say 0) and has a potentially very large address space (32 or 64 bit).

When a process tries to perform a load at address 0 (a virtual address), the OS, in tandem with hardware support, will have to make sure the load doesn't go to the physical address 0, but rather to the physical address where A is loaded into memory.

![[Pasted image 20240312170947.png|400]]
## Benefits of Virtual Memory

- Programmability 
	- Program thinks it has a lot of memory
	- Programs can use 'easy' addresses: compiler and linker don't have to worry about where program lives in physical memory
	- Multiple instances of a program can be loaded and not collide

- Protection
	- Processes cannot read/write each other memory
	- Enables isolation (which is essential)
- Effective use of resources
	- Don't have to worry that the sum of the memory consumed by all active processes is larger than physical memory.
- Sharing
	- Two processes have a different way to refer to the same physical memory cells


Translation of the virtual and physical addresses is done by the MMU (memory management unit, hardware). 

The OS sets up data structures that the hardware 'sees', associated per-process.

## Paging

Paging is the process of dividing memory (virtual + physical) into fixed-size chunks. 

These chunks are called pages.

They have a size called a page size.

Page Size: x86-64: 4096B = 4KB = $2^{12}$ bytes

Each process has a separate mapping, and each page is separately mapped.

We allow the OS to gain control on certain operations:
- Read-only pages trap to OS on write
- Invalid pages trap to OS on read or write
- OS can change mapping and resume application

Pages have numbers:
```C
page 0:   [0,4095]
page 1:   [4096, 8191]
page 2:   [8192, 12277]
page 3:   [12777, 16384]
page 2^{20}-1 [ ......, 2^{32} - 1]
```

Both virtual and physical pages have numbers, so to be clear use terms like VPN and PPN. 

#### VM math

A virtual address is 32-bits, which means that the virtual address space is $2^{32}$ bits = 4GB.

VPN is 20 bits, which means there are $2^{20}$ virtual pages. The offset is 12 bits, which means page size is $2^{12}$ bits = 4KB.

### The Page Table

The page table is conceptually a map from the VPN (Virtual Page Number) to the PPN (Physical Page Number)

![[Pasted image 20240304164753.png|400]]

- Top bits index into page table. Contents at that index are the PPN.
- Bottom bits are the offset, not changed by mapping.
- Physical Address = PPN + Offset

Each page table entry expresses a mapping about a contiguous group of addresses.

Think of it like:
- There is in the sky a 2^36 sized array that maps the virtual address to a physical page
- table\[36-bit virtual page number] = 20-bit physical page number

#### Multi-level Page Tables

The key idea is to represent the page table as a tree:
- Root node has pointers to other nodes
- Children point to pages
- We map addresses by: 
	- Using the root for uppermost address bits
	- Next level for the next address bits, etc.

The tree is sparse, meaning that many of the child nodes are not filled in. 

We only fill in the parts that are 'in use'

Example:
- Say we want to map 2MB of physical memory at virtual memory of $0,...,2^{21}-1$
- 48 bits: 
	- 9 9 9 9
	- ...
	- bottom one, points to physical pages
- Enormous address space, but few physical resources used, just 512 + 4 physical pages.
- The bottom-most level is a page table. 
- The rest of the structure tells the architecture how to find the page table.

If asked "what piece of address space is described by a given page table entry?":
- Look at how many bits are on the 'left'
#### Alternatives and Tradeoffs

There are some tradeoffs between:

- Large and small page sizes:
	- Large page sizes means wasting actual memory
	- Small page sizes means lots of page table entries 
		- May or may not get consumed

- Many levels of mapping and few:
	- More levels means less space spent on page structures when address space is sparse (which they nearly always are) 
		- more costly for hardware to walk the page tables
	- Fewer levels means we need to allocate larger pages (which cost more space)
		- the hardware has fewer levels of mapping

### Virtual Memory on `x86-64`

x86 architecture is 64-bits. Registers and addresses are 64-bits wide. 

#### Virtual Addresses

On x86-64 machines, either 57 or 48 bits matter. 

Not all 64-bit patterns correspond to meaningful virtual addresses.

Bit patterns that are valid addresses are called **canonical addresses**.

Assuming a 48-bit address:
	Low canonical addresses range from:
		`0x0000'0000'0000'0000` 
	to:
		`0x0000'7FFF'FFFF'FFFF`.
    High canonical addresses range from:
        `0xFFFF'8000'0000'0000`
    to:
        `0xFFFF'FFFF'FFFF'FFFF`.

#### Physical Addresses

- 52 bits.
- Means a single machine can address up to 4 PB of physical memory.

- If the machine only has 16 GB (say), then physical addresses will (roughly speaking) only have 34 bits that matter
- Thus the top 18 (=52-34) bits of physical addresses will generally be zero

#### Mapping

We have to map 48-bit number (virtual address) to 52-bit number (physical address), at the granularity of ranges of 2^{12}

### Page Table Structures
### Page Faults

https://cs.nyu.edu/~mwalfish/classes/24sp/lectures/l13.txt