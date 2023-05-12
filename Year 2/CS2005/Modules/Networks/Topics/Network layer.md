- Network layer protocol provides for **logical communication between hosts**
- The network layer can be decomposed into two interacting parts, the **data plane** and the **control plane**
- The **data plane** functions include per-router functions in the network layer that determine how a datagram arriving on one of a router's input links is forwards to one of that router's output links
- The **control plane** function include the network-wide logic that controls how a datagram is **routed** among routers along an end-to-end path from the source host to the destination host (using **routing algorithms**)
- Traditionally, the control plane routing protocols and the data plane forwarding functions have been implemented together, monolithically, within a route
- Software-defined networking (SDN) explicitly separates the data plane and the control plane by implementing the control plane functions as a separate service e.g. in a remote "controller"

- The network layer protocols run in every host and router
- On the **sending side**, the network layer takes segments from the transport layer, encapsulates each segment into a datagram, and then sends the datagrams to its nearby router
- On the **receiving side**, the network layer receives the datagrams from its nearby router, extracts the transport layer segments, and delivers the segments up to the transport layer

# Two key network layer functions

## Forwarding

- When a packet arrives at a router's input link, the router must move the packet to the appropriate output link
- For example, a packet arriving from a host to the nearby router must be forwarded to the next router on a path. 
- Forwarding is the most common and important one function in the data plane. 
- Other functions include blocking packets from exiting a router (e.g. if the packet originated at a known malicious sending host or is destined to a forbidden destination host) or duplicating packets and sent over multiple outgoing links

## Routing

- The network layer must determine the route or path taken by packets as they flow from a sender to a receiver
- The algorithms that calculate these paths are referred to as routing algorithms
- Routing is implemented in the control plane of the network layer


## Forwarding and routing

- **Forwarding** refers to the router-local action of transferring a packet from an input link interface to the appropriate output link interface. Forwarding takes place at very short timescales (typically a few nanoseconds) and thus is typically implemented in hardware
- **Routing** refers to the network-wide process that determines the end-to-end paths that packets take from source to destination. Routing takes place on much longer timescales (typically seconds) and is often implemented in software
- A key element in every network router is its' **forwarding table**. A router forwards a packet by examining the value of one or more fields in the arriving packets header and then using these header values to index into its forwarding table. The value stored in the forwarding table entry for those values indicates the outgoing link interface at that router to which that packet is to be forwarded

###  Configuration of forwarding tables

- **Traditional approach**
	- The routing algorithm that determines the contents of the routers' forwarding tables runs in each and every router and both forwarding and routing functions are contained within a router
	- The router algorithm function in one router communicates with the routing algorithm function in other routes to compute the values for its forwarding table
	- Performed by exchanging routing messages containing routing information according to a routing protocol
- **SDN approach**
	- The routing algorithm that determines the contents of the routers' forwarding table, runs in a physically separated remote controller that computers and distributes the forwarding tables to be used by each and every router
	- The routing device performs forwarding only, while the remote controller computes and distributes forwarding tables. The remote controller might be implemented in a remote data centre with high reliability and redundancy, and might be managed by the ISP or some third party
	- Routers and remote controllers communicate by exchanging messages containing forwarding tables and other pieces of routing information


## Router architecture

- A router consists of four components:
	- **Input ports** - An input port performs the **physical layer** function of terminating an incoming physical link at a router
		- An input port also performs link layer functions needed to interoperate with the link layer at the other side of the incoming link
		- It also performs a lookup function where the forwarding table is consulted to determine the router output port to which an arriving packet will be forwarded via the switching fabric
		- Control packets (for example packets carrying routing protocol information) are forwarded from an input port to the routing processor
		- The number of ports supported by a router can range from a relatively small number in enterprise routers to hundreds of high speed ports in a router at an ISPs edge
	- **Switching fabric** - The switching fabric connects the router's input ports to its output ports. This switching fabric is completely contained within the router
	- **Output ports** - An output port stores packets received from the switching fabric and transmits these packets on the outgoing link by performing the necessary link-layer and physical-layer functions
	- **Routing processor** - The routing processor performs control plane functions
		- In traditional routers, it executes the routing protocols, maintains routing tables and attached link state information, and computes the forwarding table for the router
		- In SDN routers, the routing processor is responsible for communicating with the remote controller in order to (among other activities) receive forwarding table entries computed by the remote controller, and install these entries in the router's input ports
		- The routing processor also performs the network management functions
