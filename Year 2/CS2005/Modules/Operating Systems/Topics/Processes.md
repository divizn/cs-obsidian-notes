# Process management overview

- A process is essentially a program **while** being executed
- It needs certain resources (i.e. CPU time, memory, files, and I/O devices) to accomplish its task.
- Resources are allocated to the process either when its created, or, while its executing (runtime)

- It is the unit of work in most systems - systems consist of a collection of processes i.e. OS processes execute system code, and user processes execute user code. All these processes may execute concurrently
- Traditionally, a process contained only a single thread of control as it ran. Now, most modern operating systems support processes that have multiple threads
- The OS is responsible for several important aspects of process and thread management such as:
	- The creation and deletion of both user and system processes
	- The scheduling of processes
	- The provision of mechanisms for synchronisation, communication, and deadlock handling
- You can see the processes running on your computer through a process manager (e.g. Task Manager on Windows or neo-fetch (?) for Linux)


# Process concept

##### What is a process?
- Jobs, user programs. OS programs, tasks, unit of work, etc.
- Essentially a program that is being executed on an OS
	- A program converted into an executable (file) becomes a process when it is run and loaded into memory


# What is a process made of?

![what is a process made of diagram](process-diagram.png)


# Process state

- As a process executes, it changes state:
	- **New** - The process is being created
	- **Running** - Instructions are being executed
	- **Waiting** - The process is waiting for some event to occur (such as an I/O completion or reception of a signal)
	- **Ready** - The process is waiting to be assigned to a processor
	- **Terminated** - The process has finished execution
- Only one process can be **Running** at any time
- Many processes can be **Ready** and **Waiting**


# Process Control Block (PCB)

- Each process is represented in the OS by a Process Control Block (PCB)
- It is made up of:
![pcb](pcb.png)
![pcbstate](pcb-state-diag.png)
![cpu example](cpu-example.png)


# Process scheduling

- The process scheduler is responsible for choosing and running processes
- OS has to decide which processes run, and how long they get
- The process scheduler needs a job queue, a ready queue, a device queue and others

- **Job queue** - consists of all processes in the system
- **Ready queue** - processes that are residing in main memory and are ready and waiting to execute
- **Device queue** - a process wishes to make an I/O request to a shared device (e.g. a disk, screen, kb, printer, etc.) but the device might be busy dealing with another I/O request so the device queue is a list of the processes waiting to use the device

- Queues are generally stored as a linked list 
	- a ready-queue header contains pointers to the first and final PCBs in the list. Each PCB includes a pointer field that points to the next PCB in the ready queue


# Schedulers

- **Short-term scheduler** (or CPU scheduler)
	- Selects which process should be executed next and allocates CPU
	- Sometimes the only scheduler in a system
	- Short-term scheduler is invoked frequently (milliseconds) - must be fast
- **Long-term scheduler** (or job scheduler)
	- Selects which processes should be brought into the ready queue
	- Long-term scheduler is invoked infrequently (seconds, minutes) - might be slow
	- Long-term scheduler controls the degree of multiprogramming
	- Strives for good process mix
- Processes can be described as either:
	- I/O bound process -spends more time doing I/O than computations, many short CPU bursts
	- CPU-bound process - spends more time doing computations; few very long CPU bursts