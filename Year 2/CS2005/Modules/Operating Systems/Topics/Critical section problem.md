
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

