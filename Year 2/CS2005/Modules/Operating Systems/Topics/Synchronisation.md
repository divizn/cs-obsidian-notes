
# The money problem

- Imagine that you share a bank account with your friend. Your starting balance is £10 and you both deposit £1 at the same time (concurrently)
- How much money do you have in your account?
- 2 occurrences:
![](money-prob-1.png)
![](money-prob-2.png)

- Cooperating processes can share data
	- Through access to files or messages
	- Directly i.e. shared logical address space (i.e. memory)
	- Threads share code, data, files
- Processes (and threads) can execute concurrently
	- May be interrupted at any time, partially completing execution
- Concurrent access to shared data may result in data inconsistency
- Maintaining data consistency requires mechanisms to ensure the orderly execution of cooperating processes

# Producer-Consumer Problem (Bounded Buffer)

- Producer produces information consumed by consumer
- They share a data structure (e.g. a buffer) that has a maximum size (e.g. a bound) $->$ bounded buffer problem
![bounded buffer simple diagram](bounded-buffer.png)

## Bounded Buffer - Producer

- Buffer is a circular list with max size `BUFFER_SIZE`
- "`in`" keeps track of the position in the list
- "`counter`" keeps track of how many things in the list
- If the buffer is full (`counter = BUFFER_SIZE`) then do nothing (busy waiting)
- Producer produces something (say a character) and puts it in position `buffer[in]`
- When you do this, then move the pointer to the next position
	- `in = (in + 1) % BUFFER_SIZE;`
	- i.e. if `in` is 3 and `BUFFER_SIZE` is 6, the above would be $4$ $=$ $(3 + 1$) % $6$ (convenient way of limiting `in`)
- Add one to the counter to keep track on how many things are in the buffer (`counter++`)

### Producer Algorithm

```ts
while (true) {/* produce an item */}
	while (counter == BUFFER_SIZE)
		/* full - do nothing */
	/* not full */
	buffer[in] = next produced
	in = (in + 1) % BUFFER_SIZE
	counter ++
```


## Bounded Buffer - Consumer

- Buffer is a circular list with max size `BUFFER_SIZE`
- "`out`" keeps track of the position in the list
- "`counter`" keeps track of how many things in the list
- If the buffer is empty, (`counter = 0`) then do nothing (waiting)
- Consumer consumes something (whatever is in the buffer) from position `buffer[out]`
- When you do this, then move the pointer to the next position:
	- `out = (out + 1) % BUFFER_SIZE`
	- i.e. if `out` is 0 and `BUFFER_SIZE` is 6, the above would be $1 =$ $(0 + 1)$ % $6$
- Subtract one from the counter to keep track on how many things are in the buffer (`counter--`)

### Consumer Algorithm

```ts
while (true) {
	while (counter == 0)
		/* empty - do nothing */
	next consumed = buffer[out]
	out = (out + 1) % BUFFER_SIZE
	counter--
	/* consume the item in next consumed */
}
```

## The problem

- Running both processes (producer and consumer) in parallel or concurrently can increase efficiency i.e. producer may populate the buffer in a faster rate than consumer consumes items
However
- Both processes can update the `counter` variable
- Problem occurs if both processes can manipulate the variable `counter` concurrently in an uncontrolled manner.
- **Race condition**
	- When several processes access and manipulate the same data concurrently and the outcome of the execution depends on the particular order in which the access takes place.
	- We need to ensure that only one process at a time can be manipulating the variable `counter` 
- Processes need to be synchronised.


# The Critical-Section Problem

- Consider a system of $n$ processes ($P0, P1, ..., Pn-1$)
- Each process has a **critical section** segment of code
	- Process may be changing common variables, updating tables, writing files, etc.
	- When one process is executing in its critical section, no other process is allowed to execute in its critical section
- **Critical-section problem** is to design an approach to solve this

## Critical Section in a process

- In a process, a critical section needs to have:
	-  **Entry section** - The section to request permission to enter the critical section
	- **Exit section** - The section to notify that the process is exiting the critical section

This looks like this:

```ts
do {
	// some code
	request permission for entry section
	if permission is granted then {
		critical section
		exit section
		}
	// remainder code
} while (true)
```


## Properties of Critical Section Solutions

- **Mutual exclusion**
	- If process $Pi$ is executing in its critical section, then no other processes can be executing in their critical sections
- **Progress**
	- If no process is executing in its critical and there exist some processes that wish to enter their critical sections, then
		- only those processes that are not executing in their remainder sections can participate in deciding which will enter its critical section next
		- this selection cannot be postponed indefinitely
- **Bounded waiting** 
	- A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted


## Peterson's Solution

- Good algorithmic description of solving the critical section problem
- Restricted to two processes that alternate between their critical and remainder sections
- The two processes share two data items:
	- `int turn` - indicates whose turn it is to enter its' critical section
	- `boolean flag[2]` - indicates if a process is ready to enter its' critical section
- For example, if process $Pi$ wishes to enter its' critical section, it sets its flag to true `flag[i] = true`
- Does this satisfy the critical section requirements?
	- **Mutual exclusion** - If both CS, then `flag[0] == flag[1] = true` AND `turn = 1` **AND**  `turn = 0 = true`  **NOT POSSIBLE** - so it is met
	- **Progress** - $P0$ sets turn to `1` and vice versa
	- **Bounded waiting** - Process never waits more than one turn


## Critical Section with Mutual Exclusion (Mutex) Locks

- Hardware-based solutions to the critical-section problem are complicated and generally inaccessible to application programmers
- OS designers build software tools to solve the critical section problem
- Simplest is mutex lock
- Protect a critical section by first `acquire()` a lock then `release()` the lock
	- Boolean variable indicating if lock is available or not
- Calls to these methods must be **atomic**
	- Usually implemented via hardware atomic instructions
- This solution requires **busy waiting**
	- This lock therefore called a **spinlock**

## Semaphores

- Synchronisation tool that provides more sophisticated ways (than Mutex locks) for process to synchronise their activities
- Semaphore $S$ is an integer variable that, apart from initialisation, is accessed only through two standard atomic operations - `wait()` and `signal()`
![](wait-signal.png)
- **Counting semaphore** - integer value can range over an unrestricted domain
- **Binary semaphore** - integer value can range only between 0 and 1
	- Behaves similarly to mutex locks

- **Example** - Process $P_1$ and $P_2$ with statements $S_1$ and $S_2$
	- We want $S_2$ to run after $S_1$ is complete
	- $P_1$ and $P_2$ share a semaphore `synch` initialised to 0
	- It can be implemented in $P_1$ and $P_2$ with the following statements
		- ![](example-semaphores.png)
	- To avoid ***busy waiting*** when `semaphore <=0`, the semaphore can **block** the process when not available (to free up CPU time) and **wake it up** when available
```python
wait(semaphore S) {
	S -> value--;
	if (S->value < 0) {
		add this process to S->list;
		block();
		}
}
```

### Deadlocks and Starvation

- Semaphores with waiting queues may result to a **deadlock**
- **Deadlock** - two or more processes are waiting indefinitely for an event that can be caused only by one of the waiting processes
- Let $S$ and $Q$ be two semaphores initialised to `1`
![](deadlocks-starvations.png)
- **Starvation** - indefinite blocking - a process may never be removed from the semaphore queue in which it is suspended
- **Priority inversion** - scheduling problem when lower-priority process holds a lock needed by higher-priority process - solved via priority-inheritance protocol
![](philospher-example.png)

## Monitors

- A high-level abstraction that provides a convenient and effective mechanism for process synchronisation
- Abstract data type, internal variables only accessible by code within the procedure
- Only one process may be active within the monitor at a time
- But the monitor construct is not sufficiently powerful to model some synchronisation schemes but can add detail


# Key Questions/Takeaway

1. What can go wrong when two or more processes access the same data?
	- The Critical Section Problem
2. What is the general solution to this?
	- Peterson's Solution
3. What different approaches can you use to implement this in software?
	- Mutex locks, semaphores, monitors
4. Can you give 2 examples of classic synchronisation problems?
	- Bounded buffer, dining philosophers
