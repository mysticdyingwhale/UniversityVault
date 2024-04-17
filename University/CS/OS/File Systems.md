# File Systems
#cs 

### What does it do?

- Provides persistence (don't go away)
- Gives a way to 'name' a set of bytes on the disk (files)
- Gives a way to map from human-friendly names to "names" (directories)
- Can be implemented on the disk, over networks, in memory, in NVRAM (non-volatile RAM), on tape, or with paper


### Files

- From user POV:
	- A bunch of named bytes on the disk
- From FS (filesystem) POV:
	- A collection of disk blocks

Main job of a file system is to map the name and offset to disk blocks

- {File, offset} -> disk address
- Operations are
	- `create(file)`
	- `delete(file)`
	- `read()`
	- `write()`


Our goal is for operations to have as few disk accesses as possible with minimal space overhead (usage)

- Cache space is never enough, meaning that the amount of data that can be retrieved in a single fetch is never enough. We want minimal space overhead because we don't want to waste 

We have seen translation/indirection before:

- Virtual address $\rightarrow$ physical address (mapped via page table)
- Offset $\rightarrow$ disk block address (mapped via inode)
- File name $\rightarrow$ file number (mapped via directory)
	- in UNIX, file number is inode


### Implementing Files

We want to meet the goal of having as few disk accesses as possible with minimal space overhead.

For now, we assume file metadata is known to the system.

Access Patterns:

- Sequential
	- File data processed in sequential order
	- Most common mode
	- Ex: editor writes out new file, compiler reads in file, etc.
- Random Access:
	- Address any block in file directly without passing through the rest of the blocks
	- Ex: Large data set, demand paging, databases
- Keyed Access:
	- Search for block with particular values
	- Ex: Associative database, index

Helpful Observations:

- All blocks in file tend to be used together, sequentially
- All files in directory tend to be used together
- All names in directory tend to be used together
- Most files are small
- Much of the disk is allocated to large files
- Many I/O operations are made to large files

We want good sequential and good random access. The candidates are:

- Contiguous Allocation
	- Extent based
	- When creating a file, make user pre-specify its length and allocate the space at once
	- File metadata contains location and size
	- (+)Simple
	- (+)Fast access, both sequential and random
	- (-)Fragmentation occurs
- Linked Files
	- Keep a linked list of free blocks
	- Metadata contains a pointer to the file's first block
	- Each block holds a pointer to the next one
	- (+)No fragmentation
	- (+)Sequential access easy (and likely fast)
	- (-)Random access is a disaster
	- (-)Pointers take up room in blocks; messes up alignment of data
- Indexed Files
	- ![[Pasted image 20240416182203.png|400]]
	- Each file has an array holding all of its block pointers
		- Like a [[Virtual Memory#Page Tables|page table]], so it shares similar issues
	- Allocate array on file creation
	- Allocate blocks on demand (free list)
	- (+)Sequential and Random Access easy
	- (-)Need to store the array
	- large possible file size --> lots of unused entries in the block array
	- large actual block size --> huge contiguous disk chunk needed

We can solve this problem the same way we did for page tables:

![[Pasted image 20240416183425.png|500]]


We're no longer wasting disk blocks, but (just like the issues with page table walking), we require extra disk accesses to look up the blocks.

This motivates the classic UNIX filesystem.

inode contains:
- Permissions
- times for file access, file modification, and inode-change
- link count (# directories containing file)
- ptrs
	- ptr 1  --> data block
		ptr 2  --> data block
		ptr 3  --> data block
		.....
		ptr 11  --> indirect block 
				      ptr --> 
				      ptr --> 
				      ptr --> 
				      ptr -->
				      ptr -->
		ptr 12 --> indirect block
		ptr 13 --> double indirect block
		ptr 14 --> triple indirect block


Just a tree. 
- Intentionally imbalanced (uneven depth) to optimize for short files. 
- Each level of this tree requires a disk seek


Positives: 
- Simple, easy to build, fast to access small files
- Max file length can be very large, multiple layers of indirection

Negatives:
  - Worst case # accesses pretty bad
  - Worst case overhead (such as 11 block file) pretty bad
  - Because you allocate blocks by taking them off unordered free list, metadata and data get strewn across disk


Notes about inodes:

- stored in a fixed-size array
- Size of array fixed when disk is initialized; can't be changed
- Multiple inodes in a disk block
- Lives in known location
	- originally at one side of disk
	- now lives in pieces across disk (helps keep metadata close to data)
- The index of an inode in the inode array is called an **i-number**
	- The OS refers to files by i-number
- When a file is opened, the inode brought in memory
- Written back when modified and file closed or time elapses

### Directories
