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
	- Since threads share the resources of the process to which they belong, it is more economical to create and context-switch threads (e.g. in Solaris, creating a process is about thirty times slower than it is creating a thread. Context switching is about five times slower) - this is because a process has multiple threads to create whereas a thread only has one process, so it's less intensive to make a thread
- **Scalability**
	- The benefits of multithreading can be even greater in a multiprocessor architecture, where threads may be running in parallel on different processing cores
	- A single-threaded process can run on only one processor, regardless of how many are available


# Single-threaded process vs multithreaded process

![](threads.png)

# Extra: Multicore Programming

- Continuous need for more computing performance led **single-CPU** systems to evolve into **multi-CPU** systems. 
- Then, rather than increasing CPUs, we placed **multiple cores** on a single chip
- Each core appears as a **separate processor** to the operating system
- We call these systems **multicore** or **multiprocessor** systems
- **Multithreaded programming** provides a mechanism for more efficient use of **CPU cores and improved concurrency**
- On a **single-core** system, **concurrency** merely means that the execution of the threads will be interleaved over time, because the processing core is capable of executing only **one thread at a time**
- On a **multicore** system, **concurrency** means that the **threads can run in parallel** because the system can assign a separate thread to each core

# Extra: Speedup - Amdahl's Law


- Identifies potential performance gains from adding additional computing cores to an application that has both serial and parallel components.
- If $S$ is the serial portion of the code on a system with $N$ processing cores, the formula is:
$$speedup \le {1 \over S + {(1 - S)\over N}}$$
- If an application is 75% parallel and 25% serial on a system with 2 cores, we get a speedup of 1.6 times. As $N$ approaches infinity, the speedup converges to $1 / S$
- The fundamental principle behind Amdahl's Law is that:
**The serial portion of an application can have a disproportionate effect on the performance we gain by adding additional computing cores**
- But does it take into account the hardware performance enhancements used in the design of contemporary multicore systems?

# Extra: Multicore Programming Challenges

- **Identifying tasks**
	- Divide applications into separate, concurrent tasks ideally independent (i.e. can run in parallel)
- **Balance**
	- Load balancing - some tasks are "heavy", some are "light". 1 to 1 mapping of tasks to processors might not be ideal (i.e. cluster some together)
- **Data splitting (decomposition)
	- Data also needs to be split up. More sharing, more coordination, less speed
- **Data dependency**
	- If there are dependencies between data used by tasks, then these tasks must be synchronised to prevent errors
- **Testing and debugging**
	- Difficult to debug things running parallel



# Thread Programming in Java

## Creating (invoking) a thread

### Two ways to do this:

#### Extending the Thread class
- More functionality - inbuilt methods like `yield()`, `interrupt()`, etc.
```java
// Thread creation by extending the Thread Class
class MyThread extends Thread {
	public void run() {
	System.out.println("Thread is running!");
	}
}
```

#### By implementing the Runnable interface
- Class can extend other base classes
```java
// Thread creation by implementing the Runnable Interface
class MyThread implements Runnable {
	public void run() {
	System.out.println("Thread is running!")
	}
}
```

### More on the Thread Class

- The class should override the run() method
- The functionality that is expected by the Thread to be executed is written in the run() method
- `void start()`: creates a new thread and makes it runnable
- `void run()`: the new thread begins its life inside this method

```java
public class MyThread extends Thread {
	// override run method and put thread code here
	public void run() { 
	System.out.println("Thread is running...");
	}
	
	public static void main(String[] args) {
	MyThread obj = new MyThread();
	obj.start(); // instantiate thread object
	}
}
```

