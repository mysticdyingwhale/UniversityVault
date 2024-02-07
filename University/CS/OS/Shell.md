#cs 

# Shell

The shell is a program that creates [[Processes|processes]]. It is the humans interface to the computer. GUIs are another kind of shell.

#### How does the shell start programs?

Take the example of `$ ls`:
- It calls `fork()`, creating a copy of the shell. There are now two copies of shell running
- It then calls `exec()`, which loads the programs instructions into memory and begins executing them (invokes the loader)
- ![[Processes#How command line works]]

Shell will use [[Processes#System Calls|system calls]] `wait()` or `waitpid()` to wait for the end of a process.