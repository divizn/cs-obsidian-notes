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
	- The server receives request messages and sends response messages

## HTTP connections

- There are **two** types of HTTP connections:
	- **Non-persistent HTTP**
		- At most, one object is sent over a TCP connection and then the connection is closed
		- Requires multiple connections to download multiple objects
	- **Persistent HTTP**
		- Multiple objects can be sent over single TCP connection therefore not requiring multiple connections to download multiple objects

### Non-persistent HTTP

- Example: Transferring a web page from server to client. The page consists of a base HTML file and 10 JPEG images and all 11 objects reside on the same server

1. Client: Initiates connection
2. Server: Accepts and notifies client
3. Client: Request - HTML file
4. Server: Response - sends file and closes TCP connection
5. Client: Process HTML and finds 10 referenced jpeg objects
6. Repeat for **all** 10 objects

#### Response time

- **Round-trip time (RTT)** is the time it takes for a small packet to travel from client to server and then back to the client (including delays; packet-propagation delays, packet-queueing delays in intermediate routers and switches, and packet-processing delays)
- HTTP response time:
	- TCP connection: 1 RRT
	- File request + response: 1 RRT
	- File transmission time
- Non-persistent HTTP response time is 2RTT + file transmission time (roughly)

### Persistent HTTP

- The server leaves the connection open after sending the response message
- Subsequent HTTP messages between the same client/server are sent over the open connection
- The client sends requests as soon as it encounters a referenced object
- It can take as little as one RTT for **all** the referenced objects

### HTTP request message

![](format-http.png)


### HTTP response message

![response](format-http2.png)


## HTTP User-server state: cookies

- HTTP is **stateless**
- But often, it is useful that the server keeps session state information (e.g. identify users so you can restrict user access or serve content as a function of the user's identity)
- HTTP uses **cookies** for this purpose
- An **HTTP cookie** has four components:
	1. A cookie header line in the HTTP response message;
	2. A cookie header line in the HTTP request message;
	3. A cookie file kept on the user's end system and managed by the user's browser (stored in browser);
	4. a beck-end database at the Web site

## Web caches (proxy server)

- A web cache satisfies HTTP requests on behalf of an origin web server.
- It is both a client (to the original server) and a server (to the client)
- Web caching reduces response time and network traffic (access link to the internet)
- A web cache stores a copy of a requested object in its local storage and sends a copy to the client browser
- To avoid **stale** data, HTTP uses **conditional GET** manifested by the `If-Modified-Since:` and `Last-Modified:` header lines


# Electronic mail

- The e-mail has **3 major components**:
	- **User agents** - compose edit, read and save outgoing and incoming messages stored on servers
	- **Mail servers** - have a **mailbox** (incoming messages); a **message queue** (outgoing messages); and an **SMTP implementation**
	- **Simple Mail Transfer Protocol (SMTP)** - protocol between mail servers to send email messages
		- Client - sending emails
		- Server - receiving emails

## SMTP

- **SMTP** uses **TCP** for reliable email transfer
- Usually at port 25
- Normally the sending server connects directly to the receiving server (direct transfer)
- SMTP has **3 phases** of transfer
	- Handshaking (greeting)
	- Transfer of messages
	- Closure
- Command/Response Interaction
	- Commands: ASCII text
	- Response: status code and phrase
- Message *must* be in 7-bit ASCII

![](sample-smtp.png)

- Mail message format
	- Header lines, e.g.
		- To:
		- From:
		- Subject
	- **these are different from SMTP MAIL FROM, RCPT TO - these are commands**
	- Body: the "message" separated by a blank line (CRLF, LF)

![](smtp-visual.png)

## Mail access protocols

- SMTP is a **push protocol** - The receiver user agent cannot request to obtain emails from the receivers server using SMTP. 
- Obtaining the message is a pull operation
- **Mail access protocols** transfer messages from the receiver's mail server to the recipients user agent
- **Post Office Protocol version 3 (POP3)** - 3 phases:
	- **Authorisation** - User agent sends a username and a password
	- **Transaction** - User agent retrieves messages; can mark messages for deletion, remove deletion marks, and obtain mail statistics
	- **Update** - after the client has issued the `quit` command (ending the POP3 session), the mail server deletes the messages that were marked for deletion
- **Internet Mail Access Protocol (IMAP)** - more features, including manipulation of stored messages on a server
- **HTTP** - used by Gmail (revolutionised email), Hotmail, Yahoo, etc.


# Transport layer services and protocols

- Transport layer protocols provide **logical communication between application processes** running on different hosts and are implemented in the **end systems** but **not in the network routers**
- On the **sending side**, the transport layer **converts the application layer messages into transport layer packets (aka segments)** **breaking the messages into smaller chunks and adding a transport layer header**. 
- The transport layer then passes the segment to the network layer, where **the segment is encapsulated within a network layer packet (aka datagram)** and sent to the destination.
- On the **receiving side**, the network layer **extracts the transport layer segment from the datagram and passes it up to the transport layer**. The transport layer then processes the received segment, **making the data in the segment available to the receiving application**
- Note: the network routes act only on the network layer fields of the datagram, they don't examine the fields of the transport layer segment encapsulated within the datagram


# Transport layer and network layer

-  Relationship between the transport layer and the network layer:
	- The transport layer provides **logical communication between processes** 
	- The network layer provides **logical communication between hosts**
	- The transport layer *relies* on the network layer and enhances the network layer services
	- The IP service model is a best effort delivery service
- There are more than one transport protocols available (TCP and UDP)

## Transport layer services to application

- Process-level addressing
	- Used to differentiate between processes
	- Network layer addressing identifies hosts
- **Multiplexing (mux)** and **Demultiplexing (demux)**