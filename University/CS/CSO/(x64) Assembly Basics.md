#cs 

## Basics

- x86-64, also known as AMD64, is an extension of the x86 instruction set.
- It supports 64-bit computing, allowing for larger memory addresses and data processing.
- Commonly used in modern computers and operating systems.

![[Pasted image 20231124020241.png]]

PC: Program Counter:
- Address of next instruction
- Called %rip
Register file:
- Heavily used program data
Condition Codes:
- Status info about most recent arithmetic/logical operation
- Conditional Branching
Memory:
- Byte addressable array
- Code and user data
- Stack to support procedures


### Data Types

- Integer data: 1, 2, 4, or 8 bytes
	- Data values
	- Addresses (untyped pointers)
- Floating point data: 4, 8, 10 bytes
	- Don't worry about it for this course
- Code:
	- Byte sequences encoding series of instructions
- No aggregate types (arrays, data structures), just contiguously allocated bytes in memory

### Operations

- Arithmetic functions on registers or memory data
- Transfer data between memory and registers
	- Load data from memory into register
	- Store register data into memory
- Transfer control
	- Unconditional jumps to/from procedures
	- Conditional branches


### Registers


- A register is a volatile memory store used for storing data temporarily within the CPU
- x64 uses 16 64-bit general purpose registers, the lower bytes of which can be accessed independently as 32-bit, 16-bit, or 8-bit registers.
- The syntax of a register is `%` followed by its name

![[Pasted image 20231121201053.png]]

- The CPU reads data from other memory stores, performs calculations in its registers, and writes the results back to memory. 
- The other memory areas only allow reading and writing. 
- All computation is done within the registers.


`%rip` - Special purpose register that always holds the memory address of the next instruction to execute in the programs code segment. CPU increments `%rip` automatically after each instruction.

- **RAX**: Used for return value
- **RBX**: General Purpose
- **RCX**: General Purpose
- **RDX**: General Purpose
- **RSI**: Source Index. Used for string and memory array copying.
- **RDI**: Destination Index. Similar to RSI, used for string and memory array copying.
- **RBP**: Base Pointer. Holds the base address of the current stack frame.
- **RSP**: Stack Pointer. Points to the top of the current stack frame.
- **R8-R15**: Additional general-purpose registers in 64-bit mode, which can be used for various purposes.



### Instructions

#### Moving data

Key:
- **q** - Quadword (8 bytes)
- **l** - Long (4 bytes)
- **w** - Word (2 bytes)
- **b** - Byte (1 byte)


- mov**q** Source, Dest
	- Copy a quadword 64-bit from source to destination
	- movl , movw, and movb do the same but for smaller sizes
	- Copies data at the address of the source to the destination
- lea**q** Source, Dest
	- Copy an "effective address" from one place to another
	- Copies the value of the source into the destination


In C:
`*dest = t;`

In Assembly:
`movq %rax, (%rbx)`
`t`: register `%rax`
`dest`: register `%rbx`
`*dest`: memory M\[`%rbx`]

Operand types:
- Immediate
	- constant integer data
	- prefix $
	- $0x400, $-530
- Registers
	- General purpose registers
	- %rax, %rbx, %rdi
- Memory
	- 8 consecutive bytes of memory
	- Indexed by register with various address modes
	- EG: (%rax)


![[Pasted image 20231125151409.png]]


For [[(x64) Arrays and Structs|arrays]]:

Syntax: `displacement(base_register, index_register, scale_factor)`

EG: 
```perl
#%rbx = int arr[]
#%rcx = 2
movq $3 , (%rbx, %rcx, 8) #arr[2] = 3;
```


#### Arithmetic Operations

Assembly arithmetic operations will modify the Dest register

![[Pasted image 20231126170309.png]]

And for one operand instructions:

![[Pasted image 20231126170358.png]]


### Flags

The `RFLAGS` register is the status register that contains the current state of an x64 CPU. 

`RFLAGS` are set implicitly by certain instructions (Arithmetic Instructions like `add`, `inc`, and `sal`)

`RFLAGS` contains:
- ZF - Zero Flag
	- Set if result is 0
- SF - Sign Flag
	- Set if result is negative
- CF - Carry Flag
	- Set if overflow occurs for unsigned-integer arithmetic
- OF - Overflow Flag
	- Set if overflow occurs for signed-integer arithmetic



### Other Labels

`jmp` - Change `%rip` address to the address specified by the label (works like goto)

Conditional Jump:
![[Pasted image 20231128012525.png]]

Based on the flags of the previous comparison, the jump will occur if the flags are in the state specified by the condition. 