# Network applications

- E-mail
- Web
- P2P file sharing
- Text messaging
- Voice over IP
- Video conferencing
- Multiplayer network games
- Streaming stored video
- Social networking
- Search

## Creating a network app

- Write programs that
	- Run on (different) end systems
	- Communicate over network
		- e.g. web server software communicates with browser software
- No need to write software for network-core devices
	- Network-core devices do not run user applications
	- Applications on end systems allow for rapid app development


# Application architectures

- Main structures of applications
	- Client-server
	- Peer-to-peer (P2P)


## Client-server architecture

- Server:
	- "Always-on" **host**
	- **Permanent** IP address
	- Data centres for scaling
- Clients:
	- Communicate with server
	- may be intermittently connected (not always-on)
	- May have **dynamic** IP address
	- Do **not** communicate *directly* with each-other


## P2P architecture

- No "always-on" server
- Arbitrary end systems directly communicate
- Peers request service from other peers, provide service in return to other peers
	- Self scalability - new peers bring new service capacity, as well as new service demands
- Peers are intermittently connected and change IP addresses
	- Complex management


# Processes communicating

- Process: program running within a host
	- Within same host, two processes communicate using inter-process communication (defined by OS)
	- Processes in different hosts communicate by exchanging **messages**
- Process types:
	- Client process - process that initiates communication
	- Server process - process that waits to be contacted
- Applications with P2P architectures have client and server processes


# Sockets

- Process sends/receives messages to/from its **socket**
- Socket analogous to a door
	- Sending process shoves message out of door
	- Sending process relies on transport infrastructure on other side of door to deliver message to socket at receiving process

![](socket-diag.png)


## Addressing processes

- To receive messages, process must have an **identifier**
- Identifier includes both **IP address** and **port numbers** associated with process on host
- Host device has a unique 32-bit IP address
- Example of port numbers:
	- HTTP server: Usually on port 80
	- Mail server: Port 25
- To send HTTP message to a web server:
	- IP address: x.x.x.x
	- Port number: 80
- Does IP address of host on which process runs suffice for identifying the process?
	- No, many processes can be run on same host, which is why we need the **port** to identify where on that host

## App-layer protocol defines

- Types of messages exchanged
	- e.g. request, response
- Open protocols:
	- Defined in RFCs
	- Allows for interoperability
	- e.g. HTTP, SMTP, SSH
- Proprietary protocols:
	- e.g. Skype
- Message syntax
	- What fields in messages & how fields are defined
- Message semantics
	- Meaning of information in fields
- Rules for when and how processes send and respond to messages


# Transport service

## What transport service does an app need? 

- **Data integrity**
	- Some apps (e.g. file transfer, web transactions) require 100% reliable data transfer
	- Other aps (e.g. audio) can tolerate some loss
- **Timing**
	- Some apps (e.g. internet telephony, interactive games) require low delay to be effective/responsive
- **Throughput**
	- Some apps (e.g. multimedia) require minimum amount of throughput to be effective
	- Other apps ("elastic apps") make use of whatever throughput they get
- **Security**
	- Encryption, data integrity

## Internet transport protocols services

- **TCP** service:
	- **Reliable transport** between sending and receiving process
	- Flow control: sender won't overwhelm receiver
	- Congestion control: throttle sender when network overloaded
	- Does not provide: timing, minimum throughput guarantee, security
	- Connection-oriented: setup required between client and server processes
	- Was made as a kind-of "replacement" for UDP
- **UDP** service:
	- **Unreliable data transfer** between sending and receiving process
	- Does not provide: reliability, flow control, congestion control, timing, throughput guarantee, security, or connection setup
	- Was made before **TCP**


## Securing TCP

- TCP & UDP
	- No encryption
	- Cleartext passwords sent into socket, traverse internet in cleartext (not safe)
- TLS/SSL
	- Provides an **encrypted** TCP connection
	- Data integrity
	- Endpoint authentication

- SSL is at the app layer
	- Apps use SSL libraries, that "talk" to TCP
	- SSL socket API
		- Cleartext passwords sent into socket, traverse Internet encrypted (safer)


# Web and HTTP

- **Hypertext transfer protocol (HTTP)**, web's application layer protocol defined in RFC and uses port 80
- A web page consists of objects (e.g. HTML, CSS, PNG image, Java applet, audio file,...)
- The base HTML file includes several referenced objects; each object is addressable by a URL
	- e.g. www.someschool.edu/someDept/pic.gif
		- someschool - host name
		- edu - domain name (on dns)
		- /someDept/pic.gif - path

## HTTP overview

- HTTP is a **client/server** protocol
	- The **client** - typically a browser - requests, receives and displays web objects (HTML, JS, CSS)
	- The **web server** - sends objects in response to request. The HTTP server is **stateless** (doesn't keep track of state)
- HTTP uses **TCP** as its transport protocol
	- The HTTP client first initiates a TCP connection with the server
	- Once the connection is established, the browser and the server processes access TCP through their socket interfaces
	- The client sends HTTP request messages and receives HTTP response messages
	- 