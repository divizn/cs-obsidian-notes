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

