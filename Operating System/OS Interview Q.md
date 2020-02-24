## OS Interview Question

### Threads and Process
#### 1. What is a Thread? What is a process? What is process table?
* A **Thread** is a path of execution within a process. A process can contain multiple threads.
* A **process** is an instance of program in execution. For example a Web Browser is a process, a shell (or command prompt) is a process.
* The **process table** is simply a data structure in the RAM of a computer. It holds information about the processes that are currently handled by the OS. This information includes general information about each process: process id, process owner, process priority, environment variables for each process, the parent process, pointers to the executable machine code of a process. A very important information in the process table is the state in that each process currently is. This information is essential for the OS, because it enables the so called multiprocessing, i.e. the possibility to virtually run several processes on only one processing unit (CPU).

#### 2. Process vs Thread?
* The thread is a subset of process. The process can contain multiple threads. 
* The threads within the same process run in a shared memory space, while processes run in separate memory spaces.
* Threads are not independent of one another like processess are, and as a result threads share with other threads their code section, data section, and OS resources. But, like process, a thread has its own program counter(PC), register set, and stack space.

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
* In fact killing PID 1, if it were allowed, would cause disaster, because it’s the ancestor process of all the other processes, and there’d be nowhere to re-parent them to. If PID 1 calls exit() itself, the Linux kernel would panic, that is, immediately abort everything and print a stack trace, like Blue Screen of Death on Windows.

#### 9. How to Free up the memory when the process is not running or seems to be hung?
To kill the process using the process_id and free up the resources allowing other processes to run.

#### 10. Multi-tasking
* two or more tasks can be executed simultaneously.
* Two types: Processor based and thread based. Processor based multitasking is totally managed by the OS, however multitasking through multithreading can be controlled by the programmer to some extent.
* It makes system more responsive and enables resource sharing and more economical.

#### 11. Scheduling Alg.
* First-Come, First-Served (FCFS) Scheduling: non-preemptive, pre-emptive scheduling algorithm
* Shortest-Job-Next (SJN) Scheduling: non-preemptive, pre-emptive scheduling algorithm. With lowest exection time
* Priority Scheduling: priority value(0max - 99least)
* Shortest Remaining Time: preemptive version of the SJN algorithm.
* Round Robin(RR) Scheduling: preemptive process scheduling algorithm. Each process is given  aquantum amount of time
* Multiple-Level Queues Scheduling
_____
### Memory
Memory get's divided into two distinct areas:
* **The user space**, which is a set of locations where normal user processes run (i.e everything other than the kernel). The role of the kernel is to manage applications running in this space from messing with each other, and the machine.
* **The kernel space**, which is the location where the code of the kernel is stored, and executes under.

#### 2. What is Virtual Memory?
* Virtual memory creates an illusion that each user has one or more contiguous address spaces, each beginning at address zero. The sizes of such virtual address spaces is generally very high.
* The idea of virtual memory is to use disk space to extend the RAM. Running processes don’t need to care whether the memory is from RAM or disk. The illusion of such a large amount of memory is created by subdividing the virtual memory into smaller pieces, which can be loaded into physical memory whenever they are needed by a process.
_____
### synchronization & deadlock
Process Synchronization: The shared resources can be used by all the processes but the processes should make sure that at a particular time, only one process should be using that shared resource.
#### 1. What is deadlock? 
Deadlock is a situation when two or more processes wait for each other to finish and none of them ever finish.  Consider an example when two trains are coming toward each other on same track and there is only one track, none of the trains can move once they are in front of each other.  Similar situation occurs in operating systems when there are two or more processes hold some resources and wait for resources held by other(s).

inappropriate use of mutexes can lead to deadlock.

#### 2. What are the necessary conditions for deadlock?
* Mutual Exclusion: There is a resource that cannot be shared.
* Hold and Wait: A process is holding at least one resource and waiting for another resource which is with some other process.
* No Preemption: The operating system is not allowed to take a resource back from a process until process gives it back.
* Circular Wait:  A set of processes are waiting for each other in circular form.

#### 3. Deadlock prevention
All four of the conditions are necessary for deadlock to occur, it follows that deadlock might be prevented by denying any one of the conditions.
* Mutual Exclusion: Not always possible to prevent deadlock by preventing mutual exclusion (making all resources shareable) as certain resources are cannot be shared safely.
* Hold and Wait: We will see two approaches, but both have their disadvantages.
    * A resource can get all required resources before it start execution. This will avoid deadlock, but will result in reduced throughputs as resources are held by processes even when they are not needed. They could have been used by other processes during this time.
    * Second approach is to request for a resource only when it is not holing any other resource. This may result in a starvation as all required resources might not be available freely always.
* No preemption: We will see two approaches here. 
    * If a process request for a resource which is held by another waiting resource, then the resource may be preempted from the other waiting resource. In the second approach, if a process request for a resource which are not readily available, all other resources that it holds are preempted.  
    * The challenge here is that the resources can be preempted only if we can save the current state can be saved and processes could be restarted later from the saved state.
* Circular wait: To avoid circular wait, resources may be ordered and we can ensure that each process can request resources only in an increasing order of these numbers. The algorithm may itself increase complexity and may also lead to poor resource utilization.

#### 4. Mutex VS Semaphore
* To apply process synchronization: It ensures that only one thread is executing a key piece of code at a time, which in turns limits access to a data structure. It ensures that the both threads have a full and proper view of that memory irrespective of any CPU reordering. 
* The Mutex is a **locking mechanism** that makes sure only one thread can acquire the Mutex at a time and enter the critical section. This thread only releases the Mutex when it exits the critical section.
* A semaphore is a **signalling mechanism** and a thread that is waiting on a semaphore can be signaled by another thread. This is different than a mutex as the mutex can be signaled only by the thread that called the wait function.
* A binary semaphore can be used as a Mutex but a Mutex can never be used as a semaphore.
* A semaphore uses two atomic operations, wait and signal for process synchronization. The wait operation decrements the value of its argument S, if it is positive. If S is negative or zero, then no operation is performed.
```
wait(S){
    while (S<=0);
    S--;
}
```
```
signal(S){
    S++;
}
```
_____
### kernel development(Linux)
#### 1. What happens when we type a simple command on shell? 
* Shell interprets the command.
* Shell creates a child process and executes the command on the child process.
* Shell waits for the child process's completion.
-- `fork()`: creates a duplicate copy of the calling process as its child. called child process

#### 2. System.log
A system log is a file containing events that are updated by the operating system components.It may contain information such as device drivers, events, operations or even device changes.
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
    * **Process control**: end, abort, create, terminate, allocate and free memory.
    * **File management**: create, open, close, delete, read file etc.
    * **Device management**
    * **Information maintenance**
    * **Communication**
- Important System Calls 
    * **`wait(`)** In some systems, a process needs to wait for another process to complete its execution. This type of situation occurs when a parent process creates a child process, and the execution of the parent process remains suspended until its child process executes. The suspension of the parent process automatically occurs with a wait() system call. When the child process ends execution, the control moves back to the parent process.
    * **`fork()`** Processes use this system call to create processes that are a copy of themselves. With the help of this system Call parent process creates a child process, and the execution of the parent process will be suspended till the child process executes.
    * **`exec()`** This system call runs when an executable file in the context of an already running process that replaces the older executable file. However, the original process identifier remains as a new process is not built, but stack, data, head, data, etc. are replaced by the new process.
    * **`kill()`** The kill() system call is used by OS to send a termination signal to a process that urges the process to exit. However, a kill system call does not necessarily mean killing the process and can have various meanings.
    * **`exit()`** The exit() system call is used to terminate program execution. Specially in the multi-threaded environment, this call defines that the thread execution is complete. The OS reclaims resources that were used by the process after the use of exit() system call.

Categories|Windows|Unix
--|--|--
Process control|CreateProcess() ExitProcess() WaitForSingleObject()|fork() exit() wait()
Device manipulation|SetConsoleMode() ReadConsole() WriteConsole()|loctl() read() write()
File manipulation|CreateFile() ReadFile() WriteFile() CloseHandle()|Open() Read() write() close!)
Information maintanence|GetCurrentProcessID() SetTimer() Sleep()|getpid() alarm() sleep()
Communication|CreatePipe() CreateFileMapping() MapViewOfFile()|Pipe() shm_open() mmap()
Protection|SetFileSecurity() InitlializeSecurityDescriptor() SetSecurityDescriptorGroup ()|Chmod() Umask() Chown()

### 5. Debugging multithreaded programs
GDB provides these facilities for debugging multi-thread programs:
* automatic notification of new threads
* `thread threadno`, a command to switch among threads
* `info threads`, a command to inquire about existing threads
* `thread apply [threadno] [all] args`, a command to apply a command to a list of threads
* thread-specific breakpoints
____
#### What is CLI?
A **command-line interface (CLI)** processes commands to a computer program in the form of lines of text. The program which handles the interface is called a command-line interpreter or command-line processor. Operating systems implement a command-line interface in a shell for interactive access to operating system functions or services.

#### ssh command in Linux?
ssh stands for **“Secure Shell”**. It is a protocol used to securely connect to a remote server/system. ssh is secure in the sense that it transfers the data in encrypted form between the host and the client. It transfers inputs from the client to the host and relays back the output. ssh runs at TCP/IP port 22.
```
ssh user_name@host(IP/Domain_name)
```
#### linux commands
* change permission? ```$ chmod nnn filename```
#### linux troubleshooting basics.
#### shell script
* How to read command line arguments in a bash script?
First Argument: $1, Second Argument: $2, Third Argument: $3
* What is $ sign?
