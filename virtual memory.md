Virtual memory is a feature of many operating systems that create an abstraction of the memory resource for each process. This abstraction removes the need for each process to handle memory management for the whole computer. In that way, a process can think of its own memory as all the memory without worrying about managing memory of other processes. It also allows the process to have memory isolation, removing the risk of corrupting or reading other processes data. Finally, virtual memory solves the space problem. If every process is given a fixed amount of memory, only a certain amount of processes could be run before running out of it. Virtual memory makes space flexible. When a process requires memory, the OS assigns [[memory pages]] that could, in theory, come from any part of the real memory, and creates a mapping between them. When a process tries to read or update memory, the OS translates each address from the virtual memory into the address of the real memory using the mapping. 

## Process Virtual Memory Layout

![[process_virtual_memory.png]]

The layout is organized according to limits and go in the order described above. LImits can modify this layout to make space for more or less data on each segment. Additionally ASLR (Address Space Layout Randomization) can move the stack, the memory map region and the heap independently while keeping the order on the address space. Finally, PiE (Position independent Executable) allows .text, .data, and .bss to move as a block to a new random address.

# Mapping

The mapping of the virtual memory is done using ***one way*** address translation. Which means that if you were to get a real memory address, you cannot compute the virtual memory address from it. The actual mapping is enabled by the [[page table]]

# SIGSEGV

Whenever you try to access a page that isn't mapped, like when trying to access an address outside of the range of your virtual memory assigned, you trigger a page fault. If the access if valid, the kernel assigns a new page, otherwise it triggers a segfault.

# Implications

Since pages may come from non contiguos memory, it is important for the low level programmer to keep in mind the size of the data and how it may be layed out in memory. A perfect example of this is creating a buffer of pagesize + 1. The kernel would need to load 2 pages of memory for every full write or read to the buffer even if in virtual memory, the addresses look contiguous. 