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
