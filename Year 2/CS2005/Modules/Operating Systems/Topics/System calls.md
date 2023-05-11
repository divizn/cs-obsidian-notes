# What happens when a System Program makes a syscall

- Typically, the OS associates a number with each system call
	- **system-call interface** maintains a table indexed according to these numbers
- The syscall interface invokes the intended syscall in the OS kernel and returns status of the syscall and any return values
- The caller doesn't need to know anything about how the syscall is implemented
	- Just needs to obey API and understand what OS will do as a result call
	- Most details of OS interface hidden from programmer by API
		- Managed by run-time support library (set of functions built into libraries included with compiler)
- Parameters passing
	- Use registers, table/memory block or the stack

![syscall diagram](syscall-diag.png)
![std-c example](c-syscall.png)
![windows unix example](syscall3.png)

# Types of System Calls

### Process control 

- Create process
- Terminate process
- End process
- Abort process
- Load process
- Execute process
- etc.

### File management

- Create file
- Delete file
- Open file
- Close file
- etc.

### Device management

- Request device
- Release device
- Read and write to device
- etc.

### Information maintenance

- Get time or date
- Set time or date
- Get system data
- Set system data
- etc.

### Communications

- Create connection
- Delete connection
- Send and receive messages