- Network layer protocol provides for **logical communication between hosts**
- The network layer can be decomposed into two interacting parts, the **data plane** and the **control plane**
- The **data plane** functions include per-router functions in the network layer that determine how a datagram arriving on one of a router's input links is forwards to one of that router's output links
- The **control plane** function include the network-wide logic that controls how a datagram is **routed** among routers along an end-to-end path from the source host to the destination host (using **routing algorithms**)
- Traditionally, the control plane routing protocols and the data plane forwarding functions have been implemented together, monolithically, within a route
- Software-defined networking (SDN) explicitly separates the data plane and the control plane by implementing the control plane functions as a separate service e.g. in a remote "controller"

- The network layer protocols run in every host and router
- On the **sending side**, the network layer takes segments from the transport layer, encapsulates each segment into a datagram, and then sends the datagrams to its nearby router
- On the **receiving side**, the network layer receives the datagrams from its nearby router, extracts the transport layer segments, and delivers the segments up to the transport layer