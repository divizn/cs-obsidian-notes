- Data structures are the "foundation stone" of all algorithms
- Representing the problem you are solving correctly will vastly help in designing a solution
- The use of the correct data structure will speed up an algorithm
- e.g. sorting a list of 1000 names
- We can measure how good is a particular data structure by using Big-O notation

# Types of data structures

## Lists

- A **list** is a sequence of zero or more data items
- The total number of items is said to be the **length** of the list
- The length of a given list can grow and shrink on demand
- Items can be accessed, inserted, or deleted at any position in a list
- Let's look at two ways to implement lists: **Arrays** and **LinkedList**


### Array implementation

- Arrays are the simplest and most widely used data structures
- Maintain insertion order of elements
- Elements are indexed - $O(n)$
- We are familiar with Java's `Arrays` and `ArrayLists`
	- An `Array` is a structure of fixed-size that can hold a collection of similar items
	- `ArrayList` is a variable length Collection class. They can increase or decrease the size dynamically


### LinkedList implementation

- Implementation of the `List` interface
- Maintain the insertion order of elements
- Elements are *not* indexed - when searching, start with the head and work our way through
- The complexity is $O(n)$
- What is the best and worst of insertion/deletion:
	- $O(1)$ - best (in Java `add`, `addFirst`, `addLast` are $O(1)$ because they know the position of the first and last elements so they don't need to traverse the LinkedList)
	- $O(n)$ - worst


## Stacks

- It Its basically like a stack in real life (stack of books)
- A stack is a special kind of list in which all insertions and deletions take place at one end
	- This is called the top
	- It has another name: "pushdown list"
- Its' items are added and deleted on  a last-in-first-out (**LIFO**) basis


### Using stacks

- To add an item to a stack, you **push** an item onto the top
- To remove an item from the top, you **pop** it
- So if you had a stack, and you pushed `20`, `10`, `13`, `5` onto it, and then popped, you would get `5` as its on the top of the stack


## Queues

- A queue is another special kind of list
	- Items are inserted at one end (end of list)
	- Items are deleted at the other end (front of list)
- Like an actual queue
- A queue is a **FIFO** type data structure
	- First-in-first-out
	- Items are deleted in the same order as they were added
- For a queue structure, we have two special names for insertion and deletion:
	- Enqueue (insertion)
	- Dequeue (deletion)


### Using queues

- To add an item to a queue, you **enqueue** an item into the queue
- To remove an item, you **dequeue** it
- So if you had a queue, and you enqueued `20`, `10`, `13`, `5` onto it, and then dequeued, you would get 20


## Hash tables

- A Hash Table (or Hash Map) is a data structure that maps a **Key** to a **Value**
- A special function called a **Hash function** performs this mapping
- This function usually maps the key to an index in an array
- Key and value could be any type of data structure

### Using hash tables

- The **hash function** returns the **hash value**
- The hash value maps the **key** to an **index** in our hash table
- The function should map within the array bounds



# Applications

- Lists
	- Many places in real life applications
	- Often used to implement other data structures e.g. queues and stacks
	- Used for mathematical vectors and matrices
- Stacks
	- Reverse a string
	- Undo mechanism in text editors
	- Web pages navigation in a web browser
	- Compilers - syntax evaluation
- Queues
	- Application with a single resource that you are trying to share
	- Printer queues
	- Email message queues
	- Processor queues
- Hash tables
	- Address books
	- Linking file name and path (local system)
	- Password verification


# Graphs

- Graphs are a useful data structure
- Examples of uses include:
	- Road maps
	- Project networks
	- Electrical circuits
	- Molecules
		- Relationship between genes, proteins, pathways, etc.
	- Relationships
		- Family tree
		- Students on courses


## An abstract view of graphs

A graph is a collection of nodes (**vertices**) which maybe connected in pairs by line segments called **edges**

![](graph-diag.png)


### Why study graphs?

- Example
	- Airline route map - an undirected graph
	- Cities - points (nodes, vertex)
	- Non-stop flight - lines connecting two cities

![](flight-graph.png)

- Computer networks
	- Computers - points (nodes, vertex)
	- Cables - lines connecting two computers (edges, arcs)
- What are your possible tasks?
	- Shortest cables
	- Lowest cost
	- Quickest delivery
	- Reliable
	- Fault-tolerant
- Many, many more applications (tube, satnav)


### The bridges of Konigsberg

![](konigsberg.png)

- Which route allows someone to cross all bridges exactly once?
- In 1736, Euler proved that is not possible
- Which lead to the field of Graph Theory

### How can a graph help?

- Questions:
	- What is the cheapest way to fly from London to Rome
	- Which route has the least flying time
	- If Heathrow is closed by bad weather, can you still fly between every other pair of cities, such as Edinburgh-Rome, Manchester-Rome?
	- If one computer in a network goes down, can email be sent between every other pairs of computers in the network?
- Graph algorithms can solve these problems


### Defining a graph

- The basic components of a graph $G=(V,E)$, includes:
	- $V$ - a set of vertices or nodes
	- $E$ - a set of edges or lines connecting the vertices in $V$
	- An edge $e=(u,v)$, is a connection between the vertices $u$ and $v$
- Example:
	- $V=(1,2,3,4,5)$
	- $E=((1,2),(1,3),(3,5),(2,5),(5,4))$
- ![](graph-example.png)

#### Graph definitions

- Directed Graph:
	- A directed graph is a pair $G=(V,E)$
	- Where $V$ is the set of vertices, and $E$ is a set of **ordered** pair of elements of $V$
	- For directed edges ($v,w)$ is in $E$, $v$ is tail, $w$ is head

- Undirected Graph:
	- An undirected graph is a pair $G=(V,E)$ where $E$ is a set of **unordered** pair of distinct elements of $V$
	- Edges have no orientation
	- For undirected graphs, $vw=wv$

- Complete Graph:
	- A complete graph is normally an undirected graph with an edge between **each** pair of vertices
		- $G=(V,E)$
		- $\forall e \in V\times V \Rightarrow e \in E$


##### Paths

- A sequence of $k$ vertices, $[v_1,v_2,...,v_k]$, such that any pair of consecutive vertices, $v_i,v_{i+1}$ are adjacent (connected by an edge) is called a **path**


##### Connectivity

- An undirected graph is connected if and only if, for each pair of vertices $v$ and $w$, there is a path from $v$ to $w$
- A directed graph is strongly connected if and only if, for each pair of vertices $v$ and $w$, there is a path from $v$ to $w$


##### Weighted Graph

- A weighted graph is a triple $G=(V,E,W)$
- Where $W:E\rightarrow R$ 
- $W(e)$ is called the weight of edge $e$


### Representation of graphs in implementation

- We often represent a graph as a **matrix (2D array)**, although other data structures can be used depending on the application
- If we have $N$ nodes to represent
	- For an **$N$ by $N$ matrix $G$, a non-zero value of $g_{ij}$ ($i$th row, $j$th column of $G$) means there is an edge between node $i$ and $j$**
- **Undirected** - assume that $g_{ij}$ is the same as $g_{ji}$
- **Directed** - assume that $g_{ij}$ is not always the same as $g_{ji}$
- **Non-weighted** - $g_{ij}$ is either one for an edge, or zero for no edge
- **Weighted** - $g_{ij}$ is the edge weight, or zero for no edge
- **Complete** - $g_{ij}$ is never zero

