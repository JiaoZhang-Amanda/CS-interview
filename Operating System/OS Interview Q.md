# OS Interview Question
OS should provide: processes and threads, file systems, network protocols with similar APIs, user interface with display, mouse, keyboard and access control based on file ownership and that file owers can control.
* [Processor Management](#fireProcessor-Management)
* [Memory](#fireMemory)
* [I/O Management](#fireIO-Management)
* [Synchronization & deadlock](#fireSynchronizationdeadlock)
* [kernel development(Linux)](#firekernel-developmentLinux)
* [Linux](#fireLinux)
## Threads and Processes
#### 1. What is a Thread? What is a process? What is process table?
* A **Thread** is a path of execution within a process. A process can contain multiple threads.
* A **process** is an instance of program in execution. For example a Web Browser is a process, a shell (or command prompt) is a process. The process holds:
    * a **address space**, set of addresses that threads of the process can usefully reference
    * a group of threads taht execute within that address space
    * a collection of references to **open files** and other "execution context"
* The **process table** is simply a data structure in the RAM of a computer. It holds information about the processes that are currently handled by the OS. This information includes general information about each process: process id, process owner, process priority, environment variables for each process, the parent process, pointers to the executable machine code of a process. A very important information in the process table is the state in that each process currently is. This information is essential for the OS, because it enables the so called multiprocessing, i.e. the possibility to virtually run several processes on only one processing unit (CPU).

#### 2. Process vs Thread?
* The thread is a subset of process. The process can contain multiple threads. 
* The threads within the same process run in a shared memory space, while processes run in separate memory spaces.
* Threads are not independent of one another like processess are, and as a result threads share with other threads their code section, data section, and OS resources. But, like process, a thread has its own program counter(PC), register set, and stack space.

#### 3. Types of Threads
* User threads: do programming assignments easily
* Kernel threads

#### 4. What are different states of process?
A process start in the *run* state
* *Ready*: waiting for permission to use the processor.
* *Running*: the process has all the resources it need for execution and it has been given permission by the operating system to use the processor. Only one process can be in the running state at any given time.
* *Waiting*: waiting for some external event to occur such as user input or a disk access.
* *Dead*

#### 5. What are the thread states?
**New**: A thread which is just instantiated is in the new state. When a start() method is invoked, the thread becomes the ready state. Then it is moved to the runnable state by the thread scheduler.
* **Runnable**: A thread which is ready to run. From running to runnable when the thread used up its execution quantum(scheduler switches). From waiting to runnable when a thread gets unblocked by the action of another thread or by an interrupt handler.(scheduler not involved)
* **Running**: A thread which is executing is in running state. the scheduler switched a threads's state from runnable to running
* **Blocked**: A blocked thread is waiting for a monitor lock is in this state. This thing can also happen when a thread performs an I/O operation and moves to the next state.
* **Waiting**: It is a thread that is waiting for another thread to do the specific action.
* **Timed_waiting**: It is a thread that is waiting for another thread to perform.
* **Terminated**: A thread that has exited is in this state.

#### 6. What is a zombie process?
A zombie process is a process whose execution is completed but it still has an entry in the process table. Zombie processes usually occur for child processes, as the parent process still needs to read its child’s exit status. Once this is done using the wait system call, the zombie process is eliminated from the process table. This is known as reaping the zombie process.

A zombie process is a subprocess that finished (normally or otherwise), but it's not yet reaped by its parent (i.e.: its parent didn't collect its exit code).

It can't be killed (because it's already dead, hence "zombie"), but it won't consume resources (CPU and memory). However, it is still using a scheduler process id; it's theoretically possible to starve a system of pids (therefore, preventing it to create new processes) launching dummy subprocesses and not reaping them.

If the parent calls exit() while the child is in the zombie state, the process 1 inherits all the children of this parent process(this is known as reparenting). Process 1 keep calling wait() to reap the zombies.

#### 7. What is PID 0 and PID 1 in Linux kernel?
* PID0 is usually the scheduler process and is often known as the swapper. No program on disk corresponds to this process, which is part of the kernel and is known as a system process.
* PID1 is for init process

#### 8. Can root kill init(PID1) process?
* By default, no, that's not allowed.
* In fact killing PID 1, if it were allowed, would cause disaster, because it’s the ancestor process of all the other processes, and there’d be nowhere to re-parent them to. If PID 1 calls exit() itself, the Linux kernel would panic, that is, immediately abort everything and print a stack trace, like Blue Screen of Death on Windows.

#### 9. How to Free up the memory when the process is not running or seems to be hung?
To kill the process using the process_id and free up the resources allowing other processes to run.

#### 10. Multi-tasking VS Multithreading
* **Multitasking** is when a single CPU performs several tasks (program, process, task, threads) at the same time. To perform multitasking, the CPU switches among theses tasks very frequently so that user can interact with each program simultaneously. In a multitasking operating system, several users can share the system simultaneously.
    * Two types: Processor based and thread based. Processor based multitasking is totally managed by the OS, however multitasking through multithreading can be controlled by the programmer to some extent.
    * It makes system more responsive and enables resource sharing and more economical.
* **Multithreading** allows multiple threads of a single task (program, process) to be processed by CPU at the same time. 
    * The main advantage is: Threads share the same address space, Thread remains lightweight and Cost of communication between threads is low.

#### 12. bootloader VS bootstraper
* **Bootloader** is a piece of code that runs before any operating system is running. Bootloader are used to boot other operating systems, usually each operating system has a set of bootloaders specific for it.
* **Bootstrap** loader is a program that resides in the computers EPROM, ROM, or othernon-volatile memory that automatically executed by the processor when turning on the computer. The bootstrap loader reads the hard drives boot sector to continue the process of loading the computers operating system.

#### 13. Booting Process
* The word “boot” is short for “bootstrap,” which is the name of the program that prompts the operating system at startup. 
* Booting is a process in which your computer gets initialized. This process includes initilizing all your hadware components in your computer and get them to work together and to load your default operating system which will make your computer operational.
* Booting occurs when you start a computer from the kernel. This usually happens when you start it for the first time. It may also occur when the computer malfunctions and you have to put it in safe mode or reboot it as though it were a new CPU.
* **Process**
    1) Power Up
    2) Power-On Self Test(POST): This test checks all connected hardware, including RAM and secondary storage devices to be sure it is all functioning properly. After POST has completed its job, the boot process searches the boot device list for a device with a BIOS on it.
    3) Find a Boot Device: The I/O system is essential to the operation of the computer because it defines the rules for communications between the CPU and the other devices attached to the computer via the motherboard. The I/O system, sometimes found in the "io.sys" file on the boot device, provides extensions to the BIOS located in ROM on the motherboard.
    4) Load the Operating System from the boot device
    5) Transfer Control: the boot process relinquishes control to the OS. The OS then proceeds to execute any pre-configured startup routines to define user configuration or application execution.
```
# Troubleshooting a PC that doesn't boots up. 
1) Check Your Monitor
Check to make sure your monitor is plugged in
2) Listen for the Message at the Beep
if the computer is having trouble starting up, it may make a series of beeps (kind of like Morse code) that tell you what's wrong.
3) Reseat the Hardware Inside
4) Explore the BIOS
If your computer turns on and you see the POST screen but can't boot into Windows, certain settings may be causing a problem. 
5) Scan for Viruses Using a Live CD
6) Boot into Safe Mode
If you're getting the Blue Screen of Death at startup, it could be a result of a bad application, driver issue, or other hardware quirk causing problems on boot.
7) Check Your Hard Drive for Corruption
8) Test the Drive in Another PC and Pray
```
#### 14. 6 Stages of Linux Boot Process
1. BIOS
BIOS stands for Basic Input/Output System. Performs some system integrity checks, Searches, loads, and executes the boot loader program. In simple terms BIOS loads and executes the MBR boot loader.
2. MBR(Master Boot Record)
It is located in the 1st sector of the bootable disk.  in simple terms MBR loads and executes the GRUB boot loader.
3. GRUB(Grand Unified Bootloader.)
If you have multiple kernel images installed on your system, you can choose which one to be executed. In simple terms GRUB just loads and executes Kernel and initrd images.
4. Kernel
* Mounts the root file system as specified in the “root=” in grub.conf. Kernel executes the /sbin/init program
* Since init was the 1st program to be executed by Linux Kernel, it has the process id (PID) of 1. Do a ‘ps -ef | grep init’ and check the pid.
* initrd stands for Initial RAM Disk. initrd is used by kernel as temporary root file system until kernel is booted and the real root file system is mounted. It also contains necessary drivers compiled inside, which helps it to access the hard drive partitions, and other hardware.
5. Init
* Looks at the /etc/inittab file to decide the Linux run level.
* Following are the available run levels: 0 – halt 1 – Single user mode 2 – Multiuser, without NFS 3 – Full multiuser mode 4 – unused 5 – X11 6 – reboot
* Init identifies the default initlevel from /etc/inittab and uses that to load all appropriate program. Typically you would set the default run level to either 3 or 5.
6. Runlevel programs
When the Linux system is booting up, you might see various services getting started. For example, it might say “starting sendmail …. OK”. Those are the runlevel programs, executed from the run level directory as defined by your run level.

## :fire:Processor Management
Scheduling & Interrupt management
### Context Switching 
Context Switching involves storing the context or state of a process so that it can be reloaded when required and execution can be resumed from the same point as earlier.
* Three major triggers:
    * **Multitasking**: In a multitasking environment, a process is switched out of the CPU so another process can be run. The state of the old process is saved and the state of the new process is loaded. On a pre-emptive system, processes may be switched out by the scheduler.
    * **Interrupt Handling**: The hardware switches a part of the context when an interrupt occurs. This happens automatically. Only some of the context is changed to minimize the time required to handle the interrupt.
    * **User and Kernel Mode Switching**: A context switch may take place when a transition between the user mode and kernel mode is required in the operating system.
* **Steps**
    * Save the context of the process that is currently running on the CPU. Update the process control block and other important fields.
    * Move the process control block of the above process into the relevant queue such as the ready queue, I/O queue etc.
    * Select a new process for execution.
    * Update the process control block of the selected process. This includes updating the process state to running.
    * Update the memory management data structures as required.
    * Restore the context of the process that was previously running when it is loaded again on the processor. This is done by loading the previous values of the process control block and registers.
    
#### 1. Scheduling Alg.
Maximize CPU utilization and throughput, minimize wait time and response time.
* First-Come, First-Served (FCFS) Scheduling: non-preemptive, non-interactive scheduling algorithm
* Shortest-Job-Next (SJN) Scheduling: preemptive, non-interactive scheduling algorithm. With lowest exection time. A long job might have to wait indefinitely
* Shortest Remaining Time: preemptive version of the SJN algorithm. A long job might have to wait indefinitely
* Round Robin(RR) Scheduling: preemptive process scheduling algorithm. Each process is given a quantum amount of time or time slice
* Stride Scheduling: time-sliced, priority-based, preemptive.
* Rate-Monotonic Scheduling: periodic chores, preemptive, priority scheduling
* Multiple-Level Queues Scheduling

#### 2. Traps & Interrupts & Signals
* Traps: application programs call upon on the OS via traps. Invoke the kernel from user code. Types:
    * errors: divide by 0, segmentation fault, bus error, etc.
    * page fault
    * system call: user code can access the kernel in a controlled manner.
    * Interrupts: generated by the hardware and are delived to the kernel. External devices call upon the OS via interrupts. Most hardware interrupts are I/O completion interrupt executes interrupt service routine(ISR). The software interrupts are generated programmatically.
    * Signals, generated by the kernel and are delivered to the user process. e.g. Crtl+C
* An interrupt is asynchronous events with respect to the executing entity(threas or OS), a trap occures synchronously.
* Interrupts are handled independently of any user program, while a trap is handled as part of the program that responding to a trap directly affects that program.
* Interrupt: In systems programming, an interrupt is a signal to the processor.
* **hardware interrupt** is a signal which can tell the CPU that something happen in hardware device, and should be immediately responded. Unlike the software interrupts, hardware interrupts are asynchronous and can occur in the middle of instruction execution, requiring additional care in programming. The act of initiating a hardware interrupt is referred to as an interrupt request (IRQ).
* **Software interrupt** is an instruction which cause a **context switch** to an **interrupt handler** similar to a hardware interrupt. Usually it is an interrupt generated within a processor by executing a special instruction in the instruction set which causes an interrupt when it is executed. Another type of software interrupt is triggered by an exceptional condition in the processor itself. This type of interrupt is often called a **trap** or **exception**.

#### 3. What is ISR? What is return type of ISR?
* An ISR(Interrupt Service Routine) is an interrupt handler, a callback subroutine which is called when a interrupt is encountered.
* ISR does not return anything. An ISR returns nothing because there is no caller in the code to read the returned values.

#### 3.1 What’s interrupt latency? How to reduce it?
* Interrupt latency is the time required for an ISR responds to an interrupt.
* Interrupt latency can be minimized by writing short ISR routine and by not delaying interrupts for more time.

#### 3.2 Can we use printf inside ISR?
printf() should work inside the CAN ISR however this will introduce many areas for potential problems. printf() is not reentrant so unless interrupts are disabled while calling it, it cannot be called from main code or from any other interrupt that does not have the same priority as the CAN ISR.

#### 3.3 Can we put breakpoint inside ISR?
The interrupt is firing, waking the micro, and the micro is executing the ISR code. However, no breakpoints will operate in the ISR.

#### 4. Shared Memory 
The shared memory in the shared memory model is the memory that can be simultaneously accessed by multiple processes. This is done so that the processes can communicate with each other. All POSIX systems, as well as Windows operating systems use shared memory.
* Advantage of Shared Memory Model
<br>Memory communication is faster on the shared memory model as compared to the message passing model on the same machine.
* Disadvantage of Shared Memory Model
    * All the processes that use the shared memory model need to make sure that they are not writing to the same memory location.
    * Shared memory model may create problems such as synchronization and memory protection that need to be addressed.
## :fire:Memory
Vitual memory & Real memory. Memory get's divided into two distinct areas:
* **The user space**, which is a set of locations where normal user processes run (i.e everything other than the kernel). The role of the kernel is to manage applications running in this space from messing with each other, and the machine.
* **The kernel space**, which is the location where the code of the kernel is stored, and executes under.

#### 1. Memory Management
* **Process Address Space**
    * **Symbolic addresses**: The addresses used in a source code. The variable names, constants, and instruction labels are the basic elements of the symbolic address space.
    * **Relative addresses**:  a compiler converts symbolic addresses into relative addresses.
    * **Physical addresses**: The loader generates these addresses at the time when a program is loaded into main memory.
* **Memory Allocation**
    * Low Memory − Operating system resides in this memory.
    * High Memory − User processes are held in high memory.
* **Fragmentation**
As processes are loaded and removed from memory, the free memory space is broken into little pieces. It happens after sometimes that processes cannot be allocated to memory blocks considering their small size and memory blocks remains unused. This problem is known as Fragmentation.
    * External fragmentation: Total memory space is enough to satisfy a request or to reside a process in it, but it is not contiguous, so it cannot be used.
    * Internal fragmentation: Memory block assigned to process is bigger. Some portion of memory is left unused, as it cannot be used by another process.
* **Paging**: Paging is a memory management technique in which process address space is broken into blocks of the same size called pages. Paging technique plays an important role in implementing virtual memory.
    * **Page Fault** – A page fault happens when a running program accesses a memory page that is mapped into the virtual address space, but not loaded in physical memory.
* **Segmentation**: Segmentation is a memory management technique in which each job is divided into several segments of different sizes, one for each module that contains pieces that perform related functions. Each segment is actually a different logical address space of the program.

#### 2. What is Virtual Memory?
* Virtual memory creates an illusion that each user has one or more contiguous address spaces, each beginning at address zero. The sizes of such virtual address spaces is generally very high.
* The idea of virtual memory is to use disk space to extend the RAM. Running processes don’t need to care whether the memory is from RAM or disk. The illusion of such a large amount of memory is created by subdividing the virtual memory into smaller pieces, which can be loaded into physical memory whenever they are needed by a process.
* Segmentation: divvide the address space into variable-size segmnets
* **Paging**: divide the address space into fixed-size pages

#### 3. What is kernel paging?
paging is a memory management scheme by which a computer stores and retrieves data from secondary storage for use in main memory. Paging divides the linear address space into fixed-size pages. Pages can be mapped into the physical address space or external storage.

#### 4. Memory Map
* The kernel uses a memory map to keep track of the mapping fro virtual pages to file pages and keep track of the mapping from virtual pages to physical pages
* mmap()

#### 5. Copy-on-write(COW)
* A process gets a private copy of the page after a thread in the process performs a write to that page for the first time.
* Use private mapping and COW for data and bss regins

#### 6. Explain your experience with RAID and disk redundancy.
RAID (redundant array of independent disks) is a way of storing the same data in different places on multiple hard disks or solid-state drives to protect data in the case of a drive failure. There are different RAID levels, however, and not all have the goal of providing redundancy.
```
# what is the difference raid 1 and raid 5?
On most situations you will be using one of the following four levels of RAIDs.

~ RAID 0: Minimum 2 disks, Excellent performance , No redundancy
~ RAID 1: Minimum 2 disks. Good performance. Excellent redundancy
~ RAID 5: Minimum 3 disks. Good performance. Good redundancy 
~ RAID 10 (also known as RAID 1+0): Minimum 4 disks. Excellent performance and redundancy
```
#### 7. Buffer and Cache
* Both cache and buffer are temporary storage areas
* The buffer is mainly found in RAM and acts as an area where the CPU can store data temporarily
* Cache, on the other hand, is a high-speed storage area that can be part of the main memory or some other separate storage area like a hard disk.
* Cache is a high-speed storage area while a buffer is a normal storage area on ram for temporary storage.
* Cache is made from static ram which is faster than the slower dynamic ram used for a buffer.
* The buffer is mostly used for input/output processes while the cache is used during reading and writing processes from the disk.
* Cache can also be a section of the disk while a buffer is only a section of the ram.
* A buffer can be used in keyboards to edit typing mistakes while the cache cannot.

#### TLB(Translation lookaside buffer)
* A memory cache that is used to reduce the time taken to access a user memory location. It is a part of the chip's memory-management unit (MMU). 
* The TLB stores the recent translations of virtual memory to physical memory and can be called an address-translation cache.

#### 8. Page replacement algorithm
* **First In First Out (FIFO)**: in this algorithm, a queue is maintained.
* **Optimal Page replacement**: this algorithms replaces the page which will not be referred for so long in future.
* **Least Recently Used**: this algorithm replaces the page which has not been referred for a long time. LRU resulted to be the best algorithm for page replacement to implement, but it has some disadvantages. In the used algorithm, LRU maintains a linked list of all pages in the memory, in which, the most recently used page is placed at the front, and the least recently used page is placed at the rear.

```
# How I'm able to run a 7GB game with my 4 GB RAM? Why the game gets slow in such cases?
Most minimum requirements for a game are the minimum recommended for acceptable performance. If your computer does not have enough free ram then it will start using the page file (disk) for extra ram. This can cause the game to slow down drastically.
```
## :fire:I/O Management
Human interface device & Network protocols & File system & Logical I/O management & Physical device drivers
#### 1. Files
* Abstraction of persisitent data storage, meaning fetching and storing data outside a process.
* **Naming files**: name space is outside the processes. User process uses the handler the OS returns to read/write the file.
* Fils **API**: open(), read(), write(), close()
* system calls on files are synchronous. Will not return until the operation is considered completed.
* standard file descriptors: 0 is stdin which map/connect to the keyboard by default, 1 is stdout which map/connect to the display by default, 2 is stderr which map/connect to the display by default.
* For each process, the kernel maintains an array of pointers to "file objects" A **file object** represents an opened file and a **file descriptor** is an index to this array.
* When fork() is called the child process gets a copy of the parents;s file descriptor table.

#### 2. Directories
* A directory is a file, maps a file name to an inode(index node) number. An inode maps an inode number to disk address. Directories are lists of names assigned to inodes. A directory contains an entry for itself, its parent, and each of its children.
* What is inside an iNode?
    * The inode (index node) is a data structure in a Unix-style file system that describes a file-system object such as a file or a directory. Each inode stores the attributes and disk block locations of the object's data. File-system object attributes may include metadata (times of last change, access, modification), as well as owner and permission data.
    * The inode is a disc block that contains information like the number of hard links to it the atime, mtime, and ctime fields,owner and group ID, the access mask, the file type, file size, etc. It also contains a few adresses of data blocks.
* Directory Hierarchy
    * **Hard Link**: refer to a file(not a dictory) in one directory that appears in another. Using link() system call of ln in shell command.
    * **Soft Links / Symbolic Links**: a special kind of file containing the name of another file or directory. Using syslink() / ln -s shell command.
* **Active Directory (AD)** is a Microsoft product that consists of several services that run on Windows Server to manage permissions and access to networked resources. Active Directory stores data as objects. An object is a single element, such as a user, group, application or device, such as a printer.
```
# Which directory are third party software stored? 
/opt. According to the Filesystem Hierarchy Standard, /opt is for "the installation of add-on application software packages". /usr/local is "for use by the system administrator when installing software locally".

#If I'm unable to copy a file from my system and paste it, what can be the possible reasons and how will I troubleshoot?
1. The hard disk is set into read only mode by mistake or corrupted file system. 
2. The target disk is corrupted. The "Access is denied" error message might appear.
3. The file or folder ownership has changed.
4. You don't have the appropriate permissions.
5. The files are encrypted.
```
#### 3. Terminals
* outout buffer
* input buffer

#### 4. Network Communication
* device: Network Interface Card(NIC)
* data arrives in a packet

## :fire:Synchronization & deadlock
Process Synchronization: The shared resources can be used by all the processes but the processes should make sure that at a particular time, only one process should be using that shared resource.
#### 1. What is deadlock? 
Deadlock is a situation when two or more processes wait for each other to finish and none of them ever finish.  Consider an example when two trains are coming toward each other on same track and there is only one track, none of the trains can move once they are in front of each other.  Similar situation occurs in operating systems when there are two or more processes hold some resources and wait for resources held by other(s).

Inappropriate use of mutexes can lead to deadlock. When you have multiple locks.

#### 2. What are the necessary conditions for deadlock?
* Mutual Exclusion: There is a resource that cannot be shared.
* Hold and Wait: threads wait for resources to be freed up, without releasing resources that they hold.
* No Preemption: resources can not be invoked from a thread.
* Circular Wait:  A set of processes are waiting for each other in circular form.

#### 3. Deadlock prevention
All four of the conditions are necessary for deadlock to occur, it follows that deadlock might be prevented by denying any one of the conditions. Restrict use of mutexes.
* Mutual Exclusion: Not always possible to prevent deadlock by preventing mutual exclusion (making all resources shareable) as certain resources are cannot be shared safely.
* Hold and Wait: We will see two approaches, but both have their disadvantages.
    * A resource can get all required resources before it start execution. This will avoid deadlock, but will result in reduced throughputs as resources are held by processes even when they are not needed. They could have been used by other processes during this time.
    * Second approach is to request for a resource only when it is not holding any other resource. This may result in a starvation as all required resources might not be available freely always.
* No preemption: We will see two approaches here. 
    * If a process request for a resource which is held by another waiting resource, then the resource may be preempted from the other waiting resource. In the second approach, if a process request for a resource which are not readily available, all other resources that it holds are preempted.  
    * The challenge here is that the resources can be preempted only if we can save the current state can be saved and processes could be restarted later from the saved state.
* Circular wait: To avoid circular wait, resources may be ordered and we can ensure that each process can request resources only in an increasing order of these numbers. The algorithm may itself increase complexity and may also lead to poor resource utilization.

#### 4. What is race condition in OS?
* A race condition is a situation that may occur inside a critical section. This happens when the result of multiple thread execution in critical section differs according to the order in which the threads execute.
* Race conditions in critical sections can be avoided if the critical section is treated as an atomic instruction. Also, proper thread synchronization using locks or atomic variables can prevent race conditions.
* **Critical Section**: The critical section in a code segment where the shared variables can be accessed. Atomic action is required in a critical section. All the other processes have to wait to execute in their critical sections.

#### 5. What is Condition variables?
* A Condition variables is a queue of threads waiting for some sort of notification.
* Condition variables are variables that represent certain conditions and can only be used in monitors. 
* Associated with each condition variable, there is a queue of threads and two operations: **condition signal** and **condition wait**. When a thread calls condition wait, the caller is put into the queue of that condition variable. When a thread calls condition signal, if there are threads waiting in that condition variable's queue, one of them is released. Otherwise, the condition signal is lost.

#### 6. Mutex VS Semaphore
* To apply process synchronization: It ensures that only one thread is executing a key piece of code at a time, which in turns limits access to a data structure. It ensures that the both threads have a full and proper view of that memory irrespective of any CPU reordering. 
* The Mutex is a **locking mechanism** that makes sure only one thread can acquire the Mutex at a time and enter the **critical section**. This thread only releases the Mutex when it exits the critical section.
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
#### 7. What is spin lock?
A spinlock is a lock which causes a thread trying to acquire it to simply wait in a loop ("spin") while repeatedly checking if the lock is available. Since the thread remains active but is not performing a useful task, the use of such a lock is a kind of busy waiting.

## :fire:kernel development(Linux)
"kernel" means the portion of the OS that runs in privileged mode.
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
- Log parsing in Linux
    * Location of log files in common Linux System(/var/log)
    * We are interested in /var/log/messages.
    * messages log file contain general system messages.
    * syslog/rsyslog generally routed all general system messages to log file or the logs which are not configured to be routed to any log file.
- Linux log files are normally stored in the folder **/var/log**. The folder contains a large number of files offering detailed information for each application.

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
    * **`wait(`)** In some systems, a process needs to wait for another process to complete its execution. This type of situation occurs when a parent process creates a child process, and the execution of the parent process remains suspended until its child process executes. The suspension of the parent process automatically occurs with a wait() system call. When the child process ends execution, the control moves back to the parent process. Return PID of one of the dead child process. It is a blocking call.
    * **`fork()`** Processes use this system call to create processes that are a copy of themselves. With the help of this system Call parent process creates a child process, and the execution of the parent process will be suspended till the child process executes. Return twice, one in parent retrun PID of the child process, the other in the child return 0.
    * **`exec()`** This system call runs when an executable file in the context of an already running process that replaces the older executable file. However, the original process identifier remains as a new process is not built, but stack, data, head, data, etc. are replaced by the new process.
    * **`kill()`** The kill() system call is used by OS to send a termination signal to a process that urges the process to exit. However, a kill system call does not necessarily mean killing the process and can have various meanings.
    * **`exit()`** The exit() system call is used to terminate program execution. Specially in the multi-threaded environment, this call defines that the thread execution is complete. The OS reclaims resources that were used by the process after the use of exit() system call. No return.
    * **`pipe()`**  creat a pip object in ther kernel and return the two file descriptors that refer to pipe. A pipe has no name and cannot passed to another process.

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

## :fire:Linux
#### CLI?
A **command-line interface (CLI)** processes commands to a computer program in the form of lines of text. The program which handles the interface is called a command-line interpreter or command-line processor. Operating systems implement a command-line interface in a shell for interactive access to operating system functions or services.

#### SSH?
* ssh stands for **“Secure Shell”**. It is a protocol used to securely connect to a remote server/system. 
* ssh is secure in the sense that it transfers the data in encrypted form between the host and the client. It transfers inputs from the client to the host and relays back the output. ssh runs at TCP/IP port 22.
* Remotely Manage a Linux Server
```
ssh user_name@host(IP/Domain_name)
```
#### Linux Commands
* Change permission? **chmod** 
`[user](read, write, execute)[group](read, write, execute)[others](read, write, execute)`
the nine bits that specify read, write, and execute (or search) permissions for the owner, group and world, there are three other bits that have special characteristics.
* lists the current running processes: `ps`
```
ps -A 显示所有进程信息
ps -u root 显示指定用户信息
ps -ef|grep ssh 查找特定进程
ps aux 列出目前所有的正在内存当中的程序
# How do you open files of a specific process?
    ps aux | grep {program-name} :to obtain process id
    ls -l /proc/XXX/fd  :To list opne files for firefox process
```
* lists directory contents: **ls**
```
$ ls       # 仅列出当前目录可见文件
$ ls -l    # 列出当前目录可见文件详细信息
$ ls -hl   # 列出详细信息并以可读大小显示文件大小
$ ls -al   # 列出所有文件（包括隐藏）的详细信息
```
* displays manual pages: **man**
* concatenates files: **cat**
* changes file timestamps: `touch`
* prints the working directory: `pwd`
* changes directory: `cd`
* removes files and directories: `rm`
* copies files and directories: `cp`
* makes directories: `mkdir`
* Killing the process: kill – Kill a process by ID; killall – Kill a process by name
* Check open ports in Linux:
    * **ss**: display all open TCP and UDP ports in Linux.
    * **netstat**: list all ports in Linux
    * **lsof**: list open files and ports on Linux based system.
    * **nmap**: check TCP and UDP ports
* Display Inode: **stat**/**ls**
```
$ stat fileName-Here
$ stat /etc/passwd
$ ls -li filename
$ ls -li /etc/resolv.conf  (-i option displays the index number (inode) )
```
* **fcntl**: manipulate file descriptor
* **netstat**
<br> Print **network connections, routing tables, interface statistics, masquerade connections, and multicast memberships**
* **iostat**
<br>Monitoring system input/output device loading by observing the time the devices are active in relation to their average transfer rates.
<br>Report Central Processing Unit (CPU) statistics and input/output statistics for devices, partitions and network filesystems (NFS)
* **vmstat**
<br>Report virtual memory statistics
<br>Reports information about processes, memory, paging, block IO, traps, and cpu activity.
* **crontab**
<br>Files used to schedule the execution of programs
* **free**
<br>Display information about the memory and swap in kibibyte. 1 kibibyte (KiB) is 1024 bytes. To get a detailed report on the system’s memory usage.
* **proc/meminfo**
<br>The /proc filesystem is pseudo filesystem. It does not exist on a disk. Instead, the kernel creates it in memory. It is used to provide information about the system
<br>The ‘/proc/meminfo‘ is used by to report the amount of free and used memory (both physical and swap) on the system as well as the shared memory and buffers used by the kernel.
* **fstab**: 
<br>Static information about the filesystems
<br>The file fstab contains descriptive information about the filesystems
the system can mount.  fstab is only read by programs, and not
written
* **strace**
<br> trace system calls and signals

#### Linux networking commands
*  `ipconfig`: configure network interface parameters. Mostly we use this command to check the IP address assigned to the system.
* `traceroute`: print the route packets take to network host
*  `dig`: a flexible tool for interrogating DNS name servers
* `telnet`: connect destination host:port via a telnet protocol if connection establishes means connectivity between two hosts is working fine. 
* `nslookup` is a program to query Internet domain name servers.
* `Netstat` command allows you a simple way to review each of your network connections and open sockets. Netstat with head output is very helpful while performing web server troubleshooting.
* `scp` allows you to secure copy files to and from another host in the network.
* `w` prints a summary of the current activity on the system, including what each user is doing, and their processes.
* `nmap` is a one of the powerful commands, which checks the opened port on the server.
* enable or disable the network interface by using `ifup`/`ifdown` commands with ethernet interface parameter.

### Linux Configurations
* **Access files**: e.g. /etc/host.conf , tells the network domain server how to look up hostnames. (Normally /etc/hosts, then name server; it can be changed through netconf.)
#### linux troubleshooting basics.
* **Booting and login/logout**: e.g. /etc/redhat-release, includes one line stating the Red Hat release number and name. Used by rc.local.
* **File system**: e.g. the file mtab specified in the following table reads the /proc/mount file, which contains the currently mounted filesystems.
* **System administration**: e.g. etc/passwd, see “man passwd”. Holds some user account info including passwords (when not “shadowed”).
* **Networking**: /etc/gateway, optionally used by the routed daemon.
* **System commands**: System commands are meant exclusively to control the system, and make everything work properly.
* **Daemons**: A daemon is a program running in non-interactive mode. Typically, daemon tasks are related to the networking area: they wait for connections, so that they can provide services through them.
* **User programs**: In Linux (and UNIX in general), there are countless “user” programs. A most common user program config file is /etc/lynx.cfg.
* **Changing configuration files**
* **The kernel**: /proc/sys/kernel/ directory
* **Daemons and system programs**: Common ones are in.ftpd (ftp server daemon), in.telnetd (telnet server daemon), and syslogd (system logging daemon).
* **User programs**
* **User configuration files: . (dot) files and rc files**

#### Shell Script
```
# How to read command line arguments in a bash script?
First Argument: $1, Second Argument: $2, Third Argument: $3
# What is $ sign?
```
#### Linux server troubleshooting steps
* Check the hardware: make sure all the cables are plugged in correctly.
* Define the exact problem
    * check to see if an application is running: `$ sudo ps -ef | grep apache2` or `$ sudo netstat -plunt | grep apache2` whether Apache web server is running
* Top: to check load average, swap, and which processes are using resources. Top shows all of a Linux server's currently running processes.
* What's up with disk space? use **df** to view a full summary of available and used disk space.
    * `$ sudo df -h` presents data about your hard drives in a human-readable format.
    * `$ sudo df -i` displays the number of used inodes and their percentage for the file system.
* Check the logs: check the server logs. These are usually in /var/log in a subdirectory specific to the service.
