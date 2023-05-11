- An operating system provides the **environment within which programs are executed**
- It provides certain services **to programs** and **to the users of those programs**. The specific services provided differ from one operating system to another, but there are common classes.
![os services](os-services-diag.png)
![other diagm](os2-diag.png)

## Services

### User-Interface

- Almost all operating systems have a **User Inteface (UI)**.
- They come in different types:
	- Command-line Interface (CLI)
	- Batch Interface
	- Graphical User Interface (GUI)

### Program execution

- The system must be able to load a program into memory and run that program.
- The program must be able to end its execution, either normally or abnormally (indicating error).


### I/O operations

- A running program may require I/O, which may involve a file or an I/O device (screen, keyboard, etc.).
- Users cannot usually control I/O devices directly, therefore the operating system must provide a means to do I/O.


### File-system manipulation

- Programs need to read and write files and directories.
- They need to create and delete them by name, search for a given file, and list file information
- Some operating systems include permissions management to allow or deny access to file or directories based on file ownership


### Communications

- There's many circumstances in which one process needs to exchange information with another. Such communication may occur between processes that are executing on the same computer, or between processes that are executing on different computer systems tied together by a computer network.
- Communications may be implemented via **shared memory**
	- two or more processes read and write to a shared section of memory
	- **message passing** -  packets of information in predefined formats are moved between processes by the operating system.


### Error detection

- The operating system needs to detect and correct errors *constantly*. 
- Errors may occur: 
	- in the CPU and memory hardware (such as a memory error or a power failure)
	- in I/O devices (such as a parity error on disk, a connection failure on a network, or lack of paper in the printer)
	- in the user program (such as an arithmetic overflow, an attempt to access an illegal memory location, or a too-great use of CPU time).
- Correction may involve halting the system, or terminating a process - (usually, when kernel level processes error, the OS crashes (halts (blue screen on windows)), this is because at the kernel level, it is assumed that all programs are important for the OS to function. So if one errors, the OS could stop functioning properly, hence the blue screen. With user level processes, they are usually just terminated.


### Resource allocation

- When there are multiple users or multiple jobs running at the same time, resources must be allocated to each of them
- The OS manages many different types of resources
	- Some (such as CPU cycles, main memory, and file storage) may have special allocation code
	- whereas others (such as I/O devices) may have much more general request and release code


### Accounting

- We want to keep track of which users use how much and what kinds of computer resources
-  Resource monitoring and usage tracking.
-  Measurement and reporting of system resource utilization.
-  Gathering statistics on CPU usage, memory usage, disk I/O, and network traffic.
-  Allocation and monitoring of system resources among users or processes.
-  Billing and chargeback mechanisms for resource consumption.


### Protection and security

- The owners of information stored in a multiuser or networked computer system may want to control use of that information
- When several separate processes execute concurrently, it should not be possible for one process to interfere with the others or with the OS itself.
- **Protection** involves ensuring that all access to system resources is controlled
- **Security** involves securing the system from outsiders, i.e. requiring the users to authenticate themselves