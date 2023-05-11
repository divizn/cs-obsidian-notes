
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

![grade matrix](cs2005-gradematrix.png))


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
2. The Internet Standards are described in formal documents. What are these documents called?
3. What is the interface between a process and the network?
4. Complete the phrase: "The Transport layer provides logical communication between \_\_\_\_\_\_."
5. Is a "link state" routing algorithm centralised or decentralised?
6. Memory can be dynamically allocated to a process during runtime. What is it called?
7. Does a thread share its code section with other threads belonging to the same process?
8. In which part of its code can a process change shared variables?
9. Is Trojan Horse an example of program threat?
10. For the screenshot of Wireshark examining HTTP behaviour; what are the IP addresses and port number of the client host? ![wireshark](wireshark-exam-q.png)

#### Question 2: Short Essay

###### Example questions:

1. Discuss how two processes communicate over a network. Include in your answer the role of Sockets, Ports, IP Addresses, and what is required from Transport Services available to Applications.

2. Define Multiplexing and Demultiplexing in the Transport Layer. Discuss how Transport Layer segments are sent and received in connectionless and connection-oriented protocols


#### Question 3: Short Essay

###### Example questions:

1. What are system programs? What is their purpose and how are they different form application programmes? Discuss **FIVE** categories of system programs.

2. What are the main states of a Java Thread? Discuss the lifecycle of a Java Thread and how it shares runtime with other Threads.


#### Question 4: Short Essay

###### Example questions:

1. Discuss **THREE** types of Program Threats. Give an example for each one.

2. What are accidental or malicious security violations? Discuss **FOUR** types and **THREE** levels at which security measures could be taken.



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
- Encryption algorithms essential property
- Symmetric encryption and example algorithms
- Asymmetric encryption and example algorithms