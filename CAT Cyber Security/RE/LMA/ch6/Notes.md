## Launching and Attaching to a process

The debugger is attached to an already running process; when attached the process is suspended giving a chance to check resources or set breakpoints. However. We lose the ability to check program's initial operations.

We can compensate that with `launching` the process through the debugger itself, the process will be launched with current user *privileges* and the debugger will stop  the execution at `entry point`.

## Controlling Process Execution

The debugger allows us to control the behaviour of the process, we can control the flow of execution or interrupt it with breakpoints.

### Execution Control Options
- Continue(Run): runs until a breakpoint or an exception occurs.
- Step Into: Executes a single instruction, but when facing a function it will jump to the first address of the function.
- Step Over: same as `Step Into` but runs the function and continue to next instruction after function call; hence, *over* a function.
- Execute 'Till Return (Run Untill Return): self explanatory. *wish I knew this when I was doing binary bomb lab*.
- Execute Till Cursor (Run Untill Selection): Runs the instructions and stops on cursor/selection location.

## Breakpoints

`Breakpoints` allows to interrupt the execution of a program in a specific location.

### Types of Breakpoints
- Software Breakpoints: Replaces the instruction in the selected address to a `breakpoint` instruction like `int 3`, the advantage of using a `software breakpoint` is that we can set an infinite number of breakpoints. However, malware can detect the instruction `int 3` and change the behaviour accordingly.
- Hardware Breakpoints: Place by CPU through registers from `DR0 - DR7`, only `DR0 - DR3` are usable giving a total of 4 user-set breakpoints.
- Memory Breakpoints: Interrupts execution flow when the memory is accessed(read or write).
- Condition Breakpoints: Interruptions start depending on a condition.

## Tracing Program Execution 
Tracing is a feature that allows *logging* events occurred during execution.


## Launching a new process
When launching a new process the debugger stops at three main breakpoints(more can added from settings):
- System Breakpoint
- TLS Callback
- Entry Breakpoint
 
Breaking at `TLS` is useful because some malware may utilise it to run code before the main function starts through `entry point`.


### Populating reference window
In the CPU tab, right click -> Search For -> Current Module

## Controlling Process Execution Using x64dbg 
- Run -> F9
- Step Into -> F7
- Step Over -> F8
- Run Untill Selection -> F4

## 32-bit vs 64-bit Stack
in 32-bit programs stack grows and shrinks with pushing and popping items, while 64-bit uses pre-allocated space.

## Tracing Execution
- Trace Into, the debugger traces the program by setting *step into* breakpoint until a condition is satisfied.
- Same as Trace Into but with a *step over* breakpoint.