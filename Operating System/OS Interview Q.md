## OS Interview Question

### Threads and Process
#### 1. What is a Thread? What is a process?
* A **Thread** is a path of execution within a process. A process can contain multiple threads.
* A **process** is an instance of program in execution. For example a Web Browser is a process, a shell (or command prompt) is a process.
#### 2. Process vs Thread?
* The thread is a subset of process. The process can contain multiple threads. 
* The threads within the same process run in a shared memory space, while processes run in separate memory spaces.
* Threads are not independent of one another like processess are, and as a resuly threads share with other threads their code section, data section, and OS resources. But, like process, a thread has its own program counter(PC), register set, and stack space.
#### 3. Types of Threads
* User level thread
* Kernel level thread
#### 4. What are different states of process?
* Ready: waiting for permission to use the processor.
* Running: the process has all the resources it need for execution and it has been given permission by the operating system to use the processor. Only one process can be in the running state at any given time.
* Waiting: waiting for some external event to occur such as user input or a disk access.
* Dead state
#### 5. What are the thread states?
**New**: A thread which is just instantiated is in the new state. When a start() method is invoked, the thread becomes the ready state. Then it is moved to the runnable state by the thread scheduler.
* **Runnable**: A thread which is ready to run
* **Running**: A thread which is executing is in running state.
* **Blocked**: A blocked thread is waiting for a monitor lock is in this state. This thing can also happen when a thread performs an I/O operation and moves to the next state.
* **Waiting**: It is a thread that is waiting for another thread to do the specific action.
* **Timed_waiting**: It is a thread that is waiting for another thread to perform.
* **Terminated**: A thread that has exited is in this state.
#### 6. What is a zombie process?
A zombie process is a process whose execution is completed but it still has an entry in the process table. Zombie processes usually occur for child processes, as the parent process still needs to read its child’s exit status. Once this is done using the wait system call, the zombie process is eliminated from the process table. This is known as reaping the zombie process.

A zombie process is a subprocess that finished (normally or otherwise), but it's not yet reaped by its parent (i.e.: its parent didn't collect its exit code).

It can't be killed (because it's already dead, hence "zombie"), but it won't consume resources (CPU and memory). However, it is still using a scheduler process id; it's theoretically possible to starve a system of pids (therefore, preventing it to create new processes) launching dummy subprocesses and not reaping them.
#### 7. What is PID 0 in Linux kernel?
* PID0 is usually the scheduler process and is often known as the swapper. No program on disk corresponds to this process, which is part of the kernel and is known as a system process.
* PID1 is for init process
#### 8. Can root kill init(PID1) process?
* By default, no, that's not allowed.
* In fact killing PID 1, if it were allowed, would cause disaster, because it’s the ancestor process of all the other processes, and there’d be be nowhere to re-parent them to. If PID 1 calls exit() itself, the Linux kernel would panic, that is, immediately abort everything and print a stack trace, like Blue Screen of Death on Windows.
_____
### Memory
Memory get's divided into two distinct areas:
* **The user space**, which is a set of locations where normal user processes run (i.e everything other than the kernel). The role of the kernel is to manage applications running in this space from messing with each other, and the machine.
* **The kernel space**, which is the location where the code of the kernel is stored, and executes under.
#### 2. What is Virtual Memory?
Virtual memory creates an illusion that each user has one or more contiguous address spaces, each beginning at address zero. The sizes of such virtual address spaces is generally very high.
The idea of virtual memory is to use disk space to extend the RAM. Running processes don’t need to care whether the memory is from RAM or disk. The illusion of such a large amount of memory is created by subdividing the virtual memory into smaller pieces, which can be loaded into physical memory whenever they are needed by a process.
_____
### deadlock
#### 1. What is deadlock? 
Deadlock is a situation when two or more processes wait for each other to finish and none of them ever finish.  Consider an example when two trains are coming toward each other on same track and there is only one track, none of the trains can move once they are in front of each other.  Similar situation occurs in operating systems when there are two or more processes hold some resources and wait for resources held by other(s).
#### 2. What are the necessary conditions for deadlock?
Mutual Exclusion: There is a resource that cannot be shared.
Hold and Wait: A process is holding at least one resource and waiting for another resource which is with some other process.
No Preemption: The operating system is not allowed to take a resource back from a process until process gives it back.
Circular Wait:  A set of processes are waiting for each other in circular form.

### Process control
### memory/resource management
### virtual memory

_____
### kernel development(Linux)
#### 1. What happens when we type a simple command on shell? 
* Shell interprets the command.
* Shell creates a child process and executes the command on the child process.
* Shell waits for the child process's completion.
-- fork(): creates a duplicate copy of the calling process as its child. called child process。
#### 2. System.log
A system log is a file containing events that are updated by the operating system components.It may contain information such as device drivers,events,operations or even device changes.
- A system log is used to
     * detect and solve the problems found in the computer
     * Storage and recovery of data about changes on data items by different transactions.
     * Warnings from the system logo can be used to predict system problems
#### 3. Types of records in a system log includes
* IMS in put message
* Condensed command type of record
* IMS ouput message
* RSR tracking
* IMS internally initiated action
* Application terminate
* Event logs record

#### 4. system.call
A system call is a mechanism that provides the interface between a process and the operating system. It is a programmatic method in which a computer program requests a service from the kernel of the OS.
- 5 different categories
    * Process control: end, abort, create, terminate, allocate and free memory.
    * File management: create, open, close, delete, read file etc.
    * Device management
    * Information maintenance
    * Communication
- Important System Calls 
    * **wait()** In some systems, a process needs to wait for another process to complete its execution. This type of situation occurs when a parent process creates a child process, and the execution of the parent process remains suspended until its child process executes. The suspension of the parent process automatically occurs with a wait() system call. When the child process ends execution, the control moves back to the parent process.
    * **fork()** Processes use this system call to create processes that are a copy of themselves. With the help of this system Call parent process creates a child process, and the execution of the parent process will be suspended till the child process executes.
    * **exec()** This system call runs when an executable file in the context of an already running process that replaces the older executable file. However, the original process identifier remains as a new process is not built, but stack, data, head, data, etc. are replaced by the new process.
    * **kill()** The kill() system call is used by OS to send a termination signal to a process that urges the process to exit. However, a kill system call does not necessarily mean killing the process and can have various meanings.
    * **exit()** The exit() system call is used to terminate program execution. Specially in the multi-threaded environment, this call defines that the thread execution is complete. The OS reclaims resources that were used by the process after the use of exit() system call.

Categories|Windows|Unix
--|--|--
Process control|CreateProcess() ExitProcess() WaitForSingleObject()|fork() exit() wait()
Device manipulation|SetConsoleMode() ReadConsole() WriteConsole()|loctl() read() write()
File manipulation|CreateFile() ReadFile() WriteFile() CloseHandle()|Open() Read() write() close!)
Information maintanence|GetCurrentProcessID() SetTimer() Sleep()|getpid() alarm() sleep()
Communication|CreatePipe() CreateFileMapping() MapViewOfFile()|Pipe() shm_open() mmap()
Protection|SetFileSecurity() InitlializeSecurityDescriptor() SetSecurityDescriptorGroup ()|Chmod() Umask() Chown()

### experience writing about debugging multithreaded programs

CLI是什么，how comfortable?
How comfortable with shell script
change permission
how computer recognize the permission: binary
怎么获得script第一个argument
$是什么
Linux， ssh 是啥
Linux OS 
linux commands, linux troubleshooting basics.

