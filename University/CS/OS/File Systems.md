# File Systems
#cs 

## What does it do?

- Provides persistence (don't go away)
- Gives a way to 'name' a set of bytes on the disk (files)
- Gives a way to map from human-friendly names to "names" (directories)
- Can be implemented on the disk, over networks, in memory, in NVRAM (non-volatile RAM), on tape, or with paper

## Files

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


## Implementing Files

We want to meet the goal of having as few disk accesses as possible with minimal space overhead.

For now, we assume file metadata is known to the system.

Access Patterns:

- Sequential:
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

### Contiguous Allocation

- Extent based
- When creating a file, make user pre-specify its length and allocate the space at once
- File metadata contains location and size
- (+)Simple
- (+)Fast access, both sequential and random
- (-)Fragmentation occurs

### Linked Files

- Keep a linked list of free blocks
- Metadata contains a pointer to the file's first block
- Each block holds a pointer to the next one
- (+)No fragmentation
- (+)Sequential access easy (and likely fast)
- (-)Random access is a disaster
- (-)Pointers take up room in blocks; messes up alignment of data
  
### Indexed Files

![[Pasted image 20240416182203.png|400]]
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
- pointers
	- `ptr` 1  --> data block
		`ptr` 2  --> data block
		``ptr`` 3  --> data block
		.....
		`ptr` 11  --> indirect block 
				      `ptr` --> 
				      `ptr` --> 
				      `ptr` --> 
				      `ptr` -->
				      `ptr` -->
		`ptr` 12 --> indirect block
		`ptr` 13 --> double indirect block
		`ptr` 14 --> triple indirect block


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
- Stored in a fixed-size array
- Size of array fixed when disk is initialized; can't be changed
- Multiple inodes in a disk block
- Lives in known location
	- originally at one side of disk
	- now lives in pieces across disk (helps keep metadata close to data)
- The index of an inode in the inode array is called an **i-number**
	- The OS refers to files by i-number
- When a file is opened, the inode brought in memory
- Written back when modified and file closed or time elapses

## Directories

Directories solve the problem of wanting to access data easily as opposed to having users remember where on the disk their files are.

Directories are used to map names to file blocks.

Approach 1:
- Single directory for the entire system
- Put directory at known location on disk
- Directory contains `<name,inumber>` pairs
- If one user uses a name, nobody else can

Approach 2:
- Single directory for each user
- Still clumsy, and `ls` on 10,000 files is a real pain

Approach 3:
- Allow directory to map names to files or other directories
- Filesystem forms a tree
- Large name spaces tend to be hierarchical 


### Hierarchical UNIX

Structure:
```
				"/"
bin     dvdrom  dev       sbin           tmp    usr
ls, grep	             tcpdump
```

- Directories stored on disk just like regular files.
- Here, the data in a directory file; this data can be in the data blocks of the directory or in the inode of the directory

      [<name, inode#>]
	       <bin, 1021>
	       <dev, 1001>
	       <sbin, 2011>
	       ....

- i-node for directory contains  a special flag bit
	- Only special users can write directory files
- Key point: i-number might reference another directory
	- turns FS into a hierarchical tree
- Root dir always inode number 2 (0,1 reserved)

Special names: "/", ".", ".."

Links:
- Hard links: multiple directories point to the same inode; inode contains `refcount`
- Soft links: synonym for a name; creates new inode rather than just directory entry

## Performance 

Unix Filesystem was simple, but it was slow.
- Blocks were too small
- inode had too many layers of mapping indirection and low transfer rate.
- Free blocks were stored in a linked list on the disk
- Poor clustering of related objects
	- Consecutive files were not close together
	- Inodes far from data blocks 
	- Inodes for a given directory not close together
	- Results in poor enumeration performance

FFS (fast file system):
- Fixes these problems to a degree
- Made block size bigger
- Cluster related objects "cylinder groups"
`[superblock | bookkeeping info | inodes | bitmap | data blocks (512 bytes each) ]`
- Try to put inodes and data blocks in the same cylinder group
- Try to put all inodes and data blocks of files in the same directory in the same cylinder group
- New directories placed in cylinder group with greater than average number of free inodes
- As files are allocated, use a heuristic.
	- Spill to next cylinder group after 40KB of file (point where indirect block is required for 4096 byte blocks) and at every megabyte thereafter
- Bitmaps
	- Track free blocks
	- Easier to find contiguous blocks
	- Can keep the entire thing in memory
	- 2TB disk / 4KB disk blocks  = 500,000,000 entries = 60MB
- Reserve space
	- But don't tell users
- Atomic 'rename'
- Symbolic links
- Big file cache
	- kernel maintains a buffer cache in memory
- No rotation delay if you're reading the whole track, so try to read the whole track
- Try to work with big chunks (write in big chunks, read ahead in big chunks)
	- If too small
		- writes: may not get data to disk often enough
		- reads: may waste read bandwidth



## Crash Recovery

There are a lot of data structures used to implement the file system: bitmap of free blocks, directories, inodes, indirect blocks, data blocks etc..

We want these data structures to be consistent; we want invariants to hold. 

 We also want to ensure that the data on the disk remains consistent. The issue lies in crashes or power failures. 

What makes the problem worse is:
- write back caching
	- meaning that the OS delays writing back modified disk blocks
- non-ordered disk writes
	- meaning that the modified disk blocks can go to the disk in an unspecified order. 


We will cover three approaches to crash recovery in file systems
### Ad-hoc

Goal: metadata consistency, not data consistency (too expensive to provide data consistency)

Approach: arrange to send file system updates to the disk in such a way that, if there is a crash, FSCK can clean up inconsistencies.

Example:
- Write data to a file
- Update/write inode 
- Mark inode as allocated in bitmap
- Mark data blocks as allocated in bitmap 
- Update directory



Disadvantages:
- Need to get ad-hoc reasoning exactly right
- Poor performance 
	- multiple updates to same block require that they be issued separately
- Slow recovery, must scan entire disk


### Copy on Write

Goal: Provide both metadata and data consistency by using more space. 

Since disks have gotten larger space is not a premium anymore. 

Approach: never modify a block, instead always make a new copy.

![[Pasted image 20240512175823.png|700]]

The file system has a root block (uberblock). This is the **only** block that is ever modified 
- The FS allocates to a new block, writes the new version of the data onto the block
- Necessitates writing a new version of the inode to point to the new block
- In turn necessitates changing  inode number, meaning that parents + any directories hard-linking to the file have to change -> those directories inodes have to change, up to the uberblock
	- This works by the inode storing a list of all its hard links
- The change is committed when and only when the uberblock is modified on disk.
- Same thing happens when creating a file or when a user appends to a file (creating another block and thus changing the inode etc..)

To enable this, the uberblock is designed to fit in a sector to allow for atomic updates.

Benefits:
- Most changes can be committed in any order, as long as it is before the uberblock is updated
	- Performance benefits
- On-disk structure and data is always consistent. Do not need to use FSCK or run recovery after crash
	- Most use checksums to handle cases where data is corrupted
- Filesystem incorporates versioning similar to Git
	- Requires not throwing away old versions of blocks after writing new ones

Disadvantages:
- Significant write amplification: any write requires changes to several disk blocks
- Significant space overheads: FS needs enough space to copy metadata blocks in order to make changes
- Generally necessitates use of garbage collection daemon to reclaim blocks from old versions of the FS
### Journaling

Copy-on-write showed that crash consistency is achievable when modifications **do not** modify or destroy the current copy

The golden rule of atomicity is "never modify, only copy"

The issue is that copy-on-write carries significant write and space overheads. We want to do better without violating this golden rule. 

The core idea:
- Treat file system operations as transactions. After a crash, failure recovery ensures that:
	- Committed file system operations are reflected in on-disk data structures
	- Uncommitted file system operations are not visible after crash recovery

Core mechanism:
- Record enough information to finish applying committed operations (redo operations) and/or roll back uncommitted operations (undo operations). 
- The information is stored in a redo log or an undo log.


#### Redo Logging

Used by Ext3 and Ext4 on Linux. Log is a fixed length ring buffer placed at the beginning of the disk.

Basic Operations
1. FS computes what would change due to an operation
2. FS computes where in the log it can write this transaction, and begins writing a transaction record there. Record contains a unique transaction ID
3. FS writes record/records detailing all changes it computed in step 1. Must wait for these log changes and TxnBegin (transaction begin) record to finish being written to disk
4. FS then writes a TxnEnd (transaction end) record, containing the same transaction ID as before. 
5. Once TxnEnd is written, FS asynchronously performs actual file system changes  (checkpointing). 

Crash Recovery:
1. FS starts by scanning from the beginning of the log
2. Every time it finds a TxnBegin entry it searches for it's corresponding TxnEnd entry
3. If matching entries are found (indicating transaction was completed) FS applies the changes
4. Recovery completed when entire log is scanned

Advantage: 
- Transaction can commit without all in-place updates being completed. Updating the journal is sufficient.
Disadvantage:
- A transactions dirty blocks need to be kept in the buffer-cache until the transaction commits and all of the associated journal entries have been flushed to the disk, increasing memory pressure

#### Undo Logging

Not used in isolation by any file system

Key Idea: log contains information on how to rollback any changes made  to data. 

Normal operations:
1. Write a `TxBegin` entry to the log
2. For each operation, write instructions for how to undo any updates made to a block.  
	- These instructions might include the original data in the block. 
	- In-place changes to the block can be made right after these instructions have been persisted.
3.  Wait for in-place changes (what we refer to as checkpointing) to finish for all blocks
4. Write a `TxEnd` entry into the block, thereby committing the transaction.
	- This implies that if a transaction is committed then all changes have been written to the actual data structures of the file system


During crash recovery:

1. Scan the log to find all uncommitted transactions, these are the ones where a `TxnBegin` entry is present but not a `TxEnd` entry.
2.  For each such transaction check to see whether the undo entry is valid.  This is usually done through the use of a checksum
	- A crash might occur before the undo entry has been successfully written
		- The actual changes corresponding to this entry would have not been written to disk, so ignoring the entry is safe
	- Trying to undo using a partially complete entry might result in data corruption
		- Using this entry would be **unsafe**.
3. Apply all valid undo entries found, in order to restore the disk to a consistent state.

For undo logs, logs are generally scanned from the end of the log:

Advantage:
- Changes can be checkpointed to disk as soon as the undo log has been updated. This is beneficial when the amount of buffer cache is low
Disadvantage:
- A transaction is not committed until all dirty blocks have been flushed to their in-place targets

#### Combining Undo + Redo Logging

Done by NTFS. 

Goals:

- Allow dirty buffers to be flushed as soon as their associated journal entries are written. Reduces memory pressure when necessary.
- Transactions commit as soon as logging is done, so the system has greater flexibility when scheduling disk writes

The filesystem writes an Undo Log and a Redo Log for each of the changes computed, and during crash recovery it does a redo pass then an undo pass.

Redo Pass:
- Goes through the log finding all committed transactions and uses the redo entries to apply the committed changes
Undo Pass
- Scans through the log backwards, finds all uncommitted transactions and uses their associated undo entries to undo any in-place updates

Tries to get the best of both undo and redo. 


## RPC, Client Server

Truly-transparent RPC not possible because server is remote
- Server can crash


## NFS


![[Pasted image 20240417161100.png|500]]

### Caching

Writes must put their data on disk (or persistently) before the server responds to the client. 