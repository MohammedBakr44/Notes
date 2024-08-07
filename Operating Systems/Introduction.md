
> An *operating system* acts as an intermediary between the user of a computer and the computer hardware.

> An *operating system* is software that manages computer hardware. It also provides a basis for application programs.

> OS is the one program running all times on the computer -- usually called the kernel.

> For a computer to start running, it needs to have an initial program to run. This initial program, or bootstrap program, tends to be simple. Typically, it is stored in *Read-Only Memory* (ROM) or Electrically *Erasable Programmable Read-Only Memory* (EEPROM), known by the general term **Firmware**, within the computer hardware.

### Interrupt
> The occurrence of an event is usually signalled by an interrupt from either the hardware or the software.

- Hardware may trigger an interrupt at any time by sending a signal to the CPU, usually by the way of the system bus.
- Software may trigger an interrupt by executing a special operation called a **System Call**

*8th edition text, explained better in 10th edition*

> When the CPU is interrupted, it stops what it is doing and immediately transfers execution to the location that contains the *starting address* of the service routine for the interrupt.

>The interrupt architecture must store the address of the interrupted instruction.

1- Old designs store the interrupt address in a fixed location.

2- Modern designs store the *return address* on the system stack.

3- If the interrupt routine needs to modify the processor state, it must explicitly save the current state and then restore that state before returning. 

*10th edition text*

> Interrupts must be handled quickly, as they occur very frequently. A table of pointers to interrupts can be used to provide the necessary speed(random access), the table of pointers is stored in low memory(the first hundred or so locations). These locations hold the addresses of the interrupt service routines(stored in what's  called interrupt vector), is indexed by a unique number, given with the interrupt request, to provide the address of the interrupt service routine for the interrupting device.

**When an interrupt is called, the address is stored in the interrupt vector to be accessed later**



