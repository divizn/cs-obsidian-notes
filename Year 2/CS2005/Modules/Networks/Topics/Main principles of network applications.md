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


# Processes communciating

- Process: program running within a host
	- Within same host, two processes communicate using inter-process communication (defined by OS)
	- Processes in different hosts communicate by exchanging **messages**
- Process types:
	- Client process - process that initiates communication
	- Server process - process that waits to be contacted
- Applications with P2P architectures have client and server processes


