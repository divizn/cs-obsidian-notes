# Concurrent and parallel execution

- **Sequential execution**
	- One task or subtask (job, process) at a time
	- Needs to complete its execution for another task to start
- **Concurrent execution**
	- Multiple tasks or subtasks **appear to run in parallel**
	- Takes advantage of the CPU time-slicing feature of the operating system
	- Recall processes states - runs part of a task then go to waiting state. While in waiting state another task is running and so on
- **Parallel execution**
	- Multiple tasks or subtasks **actually run at the same time**
	- Requires two or more CPUs/cores

- Concurrency and parallelism are ***not*** the same thing - but they both need synchronisation

![](seq-ex-example.png)
![](conc-ex-example.png)
![](para-ex-example.png)
![](para-conc-ex-example.png)

# Concurrency vs Parallelism

| Concurrency                                                               | Parallelism                                                  |
| ------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Two or more tasks can start, run and complete in overlapping time periods | Two or more tasks run at the same time (multiple CPUs/cores) |
| Composition of independently executing processes                          | Simultaneous execution of (possibly related) computations    |
| Dealing with lots of things at once                                       | Doing lots of things at once                                                             |

- An application is **neither parallel, nor concurrent**
	- Meaning that it processes all tasks one at a time, **sequentially**
- An application is **concurrent** but **not parallel**
	- Meaning that it processes more than one task at the same time, but not two tasks are executing at the same instant
- An application is **parallel** but **not concurrent**
	- Meaning that it processes more than one task at the same time and they are executing at the same instant (multi-core CPU or multiple CPUS)
- An application is both **parallel and concurrent**
	- Meaning that it processes multiple tasks, concurrently, at the same time (multi-core CPU or multiple CPUs)


# What is a thread?

- A thread is a basic unit of CPU utilisation
- It consists of:
	- Thread ID
	- Program Counter
	- Register Set
	- Stack
- It shares with other threads belonging to the same process, its code section, data section, and other operating system resources (e.g. files, etc.)
- A traditional (or **heavyweight**) process has a single thread of control
- If a process has multiple threads of control, it can perform more than one task at a time

###### Examples

- A web browser might have one thread that displays images or text, and another thread that retrieves data from the network
- A word processor may have a thread for displaying graphics, another for responding to keystrokes from the user, and another for performing spelling and grammar checking in the background

# Benefits of threads

- **Responsiveness**
	- Multithreading an interactive application allows a program to continue running even if part of its blocked and/or is performing a lengthy operation
- **Resource sharing**
	- Processes can only share resources through techniques such as shared memory and message passing
	- Threads share the memory and the resources of the process to which they belong by default
	- The benefit of sharing code and data is that it allows an application to have several different threads of activity within the same address space
- **Economy**
	- Allocating memory and resources for process creation is costly
	- Since threads share the resources of the process to which they belong, it is more economical to create and context-switch threads (e.g. in Solaris, creating a process is about thirty times slower than it is creating a thread. Context switching is about five times slower)


# Single-threaded process vs multithreaded process

![](threads.png)
