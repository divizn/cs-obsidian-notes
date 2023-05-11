
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
- Processes need to be synchronised