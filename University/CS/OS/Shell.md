# Shell
#cs 

The shell is a program that creates [[Processes|processes]]. It is the humans interface to the computer. GUIs are another kind of shell.

#### How does the shell start programs?

Take the example of `$ ls`:
- It calls `fork()`, creating a copy of the shell. There are now two copies of shell running
- It then calls `exec()`, which loads the programs instructions into memory and begins executing them (invokes the loader)
- ![[Processes#How command line works]]

Shell will use [[Processes#System Calls|system calls]] `wait()` or `waitpid()` to wait for the end of a process.


## Shell Commands
### `ls` (list)

Lists all files/directories in named directory.

#### -R

Recursively lists all files, directories, subfiles and subdirectories in named directory

#### -a

Lists all files/dirs, including hidden files/dirs.

#### -l

Lists all files in long format

- Field 1: File permissions
	- -rwxrwxrwx
	- read write execute permissions for user, group, and others in order
- Field 2: Number of Links
- Field 3: Owner
- Field 4: Group
- Field 5: Size
- Field 6: Last modified data/time
- Field 7: File name

#### -1
Lists one file per line
### grep



### sort

### head






