
# Contents

[Exam](#exam)
[Topics](#topics)
[Modules](#modules)


# Exam

- 3 hours
- 4 questions
- All questions marked as PASS+/PASS/MARGINAL/FAIL
- Need PASS in all to pass (marginal in all for bare minimum)
- **All 4 questions have equal weight**


#### Grade matrix

![grade matrix](cs2005-gradematrix.png)


### Structure

- 1 short answer question with **15** parts
	- Must attempt all parts
- 3 short essay questions

#### Short answer question

- Covers **ALL** topics and labs
- Few words or a phrase
- No diagrams


#### Short essay questions

- Roughly 1 to 1.5 pages (approx. 500-800 words) each
- Diagrams not necessary

-  Question 2 covers all **Networks** topics 
	- Application layer (incl. Distributed Systems)
	- Transport layer
	- Network layer
- Question 3 covers all **Operating Systems** topics
	- Operating Systems Structures
	- Processes
	- Threads
	- Synchronisation
- Question 4 covers all **Security** topics
	- Security problem (threats and attacks)
	- Encryption


### Approach

#### Short answer
- Think specific, key terms
- Manage time wisely
	- PASS+/PASS/MARGINAL/FAIL depends on how many **parts** of the question you have answered correctly

#### Short essay
- Essay structure is key (think about how you **answer the question**)
- Don't brain dump (e.g. spot a keyword and write everything you know about it rather than answering the question)



### Revision hints and tips

#### Question 1: Short Answer

###### Example questions:

1. Which two of the OSI model's layers are NOT included in the TCP/IP stack?
	- Presentation and session
2. The Internet Standards are described in formal documents. What are these documents called?
	 - RFC (Request for comments)
3. What is the interface between a process and the network?
	- Socket
4. Complete the phrase: "The Transport layer provides logical communication between \_\_\_\_\_\_."
	- Application processes
5. Is a "link state" routing algorithm centralised or decentralised?
6. Memory can be dynamically allocated to a process during runtime. What is it called?
	- Heap
7. Does a thread share its code section with other threads belonging to the same process?
	- Yes
8. In which part of its code can a process change shared variables?
	- Critical section
9. Is Trojan Horse an example of program threat?
	- Yes
10. For the screenshot of Wireshark examining HTTP behaviour; what are the IP addresses and port number of the client host? ![wireshark](wireshark-exam-q.png)
		- Client IP address - 10.0.2.4
		- Client port number - 55754

#### Question 2: Short Essay

###### Example questions:

1. Discuss how two processes communicate over a network. Include in your answer the role of Sockets, Ports, IP Addresses, and what is required from Transport Services available to Applications.
	-  Process send and receive messages from their sockets
	- Ports and identifiers are what is used to identify processes
	- Transport services use this to provide logical communication between application processe

2. Define Multiplexing and Demultiplexing in the Transport Layer. Discuss how Transport Layer segments are sent and received in connectionless and connection-oriented protocols
	- Multiplexing -  the job of gathering data chunks from different sockets, encapsulating each data chunk with header information to create segments, and passing the segments to the network layer
	- Demultiplexing - the job of delivering the received segments to the correct socket

#### Question 3: Short Essay

###### Example questions:

1. What are system programs? What is their purpose and how are they different from application programs? Discuss **FIVE** categories of system programs.
	- System programs (also known as system utilities) are programs used by the system to perform  tasks (usually utilities made by the OS and used by other programs). 
	- Different to application programs which are programs used by the user to perform tasks e.g. stuff like Microsoft Word
	- Some are just simple interfaces for system calls
	- Some are complex e.g. device drivers
	- Categories 
		1. File Management - these program manipulate files (create, delete, rename) - example is Dolphin File Manager or Windows Explorer
		2. File Modification - These programs are used to modify contents of a file - example could be a text editor like VSCode
		3. Communication - Provide the mechanism for creating connections across processes, users and systems. Allows for stuff like browsing the internet and sending emails
		4. Status information - Programs that show the status information of the system e.g. CPU usage like in Task Manger
		5. Program loading and execution - Programs that load the file into memory to be executed e.g. loaders

2. What are the main states of a Java Thread? Discuss the lifecycle of a Java Thread and how it shares runtime with other Threads.


#### Question 4: Short Essay

###### Example questions:

1. Discuss **THREE** types of Program Threats. Give an example for each one.
	- Trojan Horse - A program pretending to be something else e.g. a fake login system that contains malicious code
	- Trapdoor - A defect in a program that allows malicious actors to exploit the flaw e.g. security risk in a website that leaks database credential
	- Logic bomb - Malicious code that runs at a certain date/time e.g. something that runs every 2 days to get information from someone's computer

2. What are accidental or malicious security violations? Discuss **FOUR** types and **THREE** levels at which security measures could be taken.
	- Security violations are attacks on a system that are usually done with malicious intent however can be done accidental
	- Types:
		1. Breach of confidentiality - Involves gaining unauthorised access to information e.g. credit cards
		2. Theft of service - Unauthorised access of resources e.g. stealing a proprietary program
		3. Denial of service - Preventing legitimate use of the system by overloading the server with illegitimate traffic using bots
		4. Breach of integrity - Involves manipulating data and changing it from what it used to be e.g. changing the content of a website
	- Levels:
	1. Human - Avoid social engineering, phishing and dumpster diving in an attempt to find information that could cause a security risk
	2. Operating system - Protection mechanics and debugging, make sure your OS is up-to-date with latest security features
	3. Network - Intercepted communication and DOS - avoid by throttling connection which could prevent bots from overwhelming server and avoid accessing private information on an open/public network as packet sniffers could be watching



# Topics


## Networks revision topics

- Internet components & services (hosts, protocols, RFCs, IETF, …)
- Protocol layers (OSI, TCP/IP)
- Main principles of network applications (client-server, P2P, message exchange, IP addresses, sockets, port numbers, data integrity, throughput, …)
- Web services (HTTP, messages, request, response, headers, …)
- Electronic mail over the Internet (user agent, mail server, SMTP, POP3, IMAP, HTTP, …)
- How processes communicate (messages, sockets, port numbers, IP addresses, …)
- Transport services (mux/demux, reliable data transfer, flow control, congestion control, …)
- TCP, UDP
- Segment structure (port #, seq, ack numbers, receive window, …)
- Forwarding/routing
- Routing algorithms
- Router components
- IPv4 & IPv6 datagram
- IPv4 addressing 
- Fragmentation / reassembly


## Operating Systems revision topics

- Operating systems services
- Operating systems interfaces (users, programs)
- System calls
- System programs
- What is a process (structure, PCB, …)?
- Process states and lifecycle
- Process scheduling (schedulers, queues, …)
- Concurrency / parallelism
- What is a thread?
- Threads states and lifecycle (in Java)
- Critical section problem
- Critical section problem solution requirements
- Bounded buffer (producer-consumer) problem
- Race condition
- Mutex locks, semaphores, monitors
- Deadlock / starvation


## Security revision topics

- Security violations
- Security measures
- Program threats and examples 
- System and network threats and examples
- Cryptography terms
- Encryption 
- Symmetric encryption and asymmetric encryption and example algorithms



# Modules

[Networks](Networks.md)
[Operating Systems](Operating%20Systems.md)
[Security](Security.md)
