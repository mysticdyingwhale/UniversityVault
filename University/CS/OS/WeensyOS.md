# WeensyOS
#cs 




### Context Switches in WeensyOS

- on interrupt, hardware saves "trapframe":
	- `%rip/%rsp/%eflags` and lots of other things
	- saves all of that on the *kernel's stack* at a well-known place in kernel memory
- `%rdi` set equal to stack pointer
- `%rdi` shows up, in C code, as the argument to `exception()`
- exception does a brute force struct copy into process-specific memory in kernel space
- now all of the process's registers just live in the PCB / struct proc.
- kernel does its thing.
- kernel gets ready to choose another process
- remember, that process had the same thing happen
- so all of *the new process's* registers are sitting in the same kind of memory mentioned above.
- now, `exception_return (&p->p_registers)`
- note: `%rdi `holds address of saved registers
- set the stack pointer equal to that address
- that means that `popq` will do the "right" thing
- pop the saved registers into the CPU's
- add 16 to skip past saved codes (error code if pg fault handler and int code in all cases).
- now stack pointer is pointing to the trapframe at the time of the trap
- that trapframe includes `%rip` and trap-time `%rsp`
- `iretq `brings us back into user space with the` %rip,%rsp` at the time of the trap