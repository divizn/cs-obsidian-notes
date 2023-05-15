- Depth-first search (DFS)
- Exhaustive search
- Breadth-first search (BFS)
- A* search (A-star)
- Minimum Spanning Trees (MST)

- Dijkstra's Algorithm

##### What is "search" in graphs?

- Start at the source node, and search until we find the target node
- When we work with graphs, we often wish to do something to each node in the graph exactly once
	- Visit each node **once and only once**
- Examples:
	- A piece of information that needs to be distributed to all the computers on a network
	- Look for information among computer in a network

###### Types of graph "search"

- There are other ways to search a graph other than visiting all the nodes
	- Finding a path between two nodes
	- Finding the shortest path between two nodes (number of edges)
	- Finding the cheapest path between two nodes (a function of edge weight)


# Depth-first Search

- Depth-first - allows us to explore nodes and edges of a graph
- The traversal will go as far as possible down a path until a "**dead end**" is reached
- In an undirected graph - a node is dead end if all of the nodes adjacent to it have already been visited
- In a directed graph - a node is a dead end if it has no outgoing edges and we visited everything else

## What is DFS

1. We visit the starting node and then proceed to follow links through the graph until we reach a dead end
2. We then back up along our path until we find an unvisited adjacent node, and continue in that new direction
3. The process completes when we back up to the starting node and all the nodes adjacent to it have been visited
4. If presented with two choices, we choose the node with numerically and/or alphabetically smaller label (just for convenience)

- DFS algorithm
```ts
visit(n) [do something to/at node n...]
mark(n)
for every edge nm from n to m in g do
	if m is not marked then
		DFS(g,m)
	end if
end for
```


## DFS Running Time analysis

- Remember:
	- DFS is called on each node exactly **once**
	- $n$ nodes: $O(n)$
	- Every edge is examined exactly twice, once from each of its vertices/nodes
	- $m$ edges: $O(2m)$
- $\therefore O(n)+O(2m)\equiv O(n+m)$
- If we assume that the work done as we visit each node is the most complex part of the process, the traversal is of order $O(n)$


# Exhaustive Search

- The exhaustive search systematically evaluates every possible path in a graph (exhaustive)
- This method is guaranteed to find what we are looking for (exhaustive)
- However this method is unsuitable for most real world problems (exhaustive)

```python
for ever edge nm (from n to m) in
	if m is not in p then
		p = p + {m}
		exhaustive(g,m,p)
	end if
end for
```

## Exhaustive Running Time analysis

- This is very complicated to compute
- It depends on how the nodes and edges are organised
- If we look at the worse case, that of a complete graph:
	- Here all the nodes are connected to each other
	- For the first node in the path there are $n-1$ edges to follow
	- For the second, $n-2$
	- For the third, $n-3$,...
	- Hence we get $(n-1)(n-2)(n-3)....1=O(n-1)!)$


# Breadth-first Search

- Breadth-first search is different to depth first in the way it explores the graph
- This search method considers neighbouring nodes first
	- All the neighbours of the start nodes are expanded first
	- Then the neighbours of the neighbours
	- Until the goal state is found
- This search is very expensive since all the partial paths being considered must be stored
- Similar to depth-first search, breadth-first search will eventually find a path to the goal, but it may not be the best path
- The algorithm is similar to the exhaustive search algorithm, but it stops when the goal node is reached
	- Exhaustive generates all paths



# Best-first search

- Beast first search is an improvement upon depth first search
- A heuristic is used to decide which node is explored next
	- A **heuristic** is a rule of thumb or best practice 
- For example nodes are expanded in order of lowest cost



## A* search

- The A* (a-star) search method is an example of a best-first search
- Very good for route finding applications
	- The AA website
	- The tube
- In order for the search to work, two estimates must be available
	- How much a partial path has cost
	- An estimate (**an under estimate**) of how far is left to the goal state e.g. a lower bound on how far to travel
- The A* algorithm will find an optimal path without necessarily considering all the routes

- The algorithm scores each partial path with the following function:
	- **$f=g+h$**
		- Where $g$ is the cost so far and $h$ is the estimate of the cost to the goal state
			- For example as the crow-files distance - London to Manchester: Land transport: 200.21 miles, crow files: 183.05
- If $h$ is always zero (i.e. we do not have any information about how far away the goal is), then the algorithm becomes similar to depth-first search
- If $g$ is always zero, then the algorithm is called a **Greedy search**
	- Making locally optimal choices at each stage with the hope of finding the global optimum
![](a-star-example.png)


# Minimum Spanning Trees

- A spanning tree is a sub-graph that is also a tree (no cycles) that contains all of the nodes of the super-graph
	- The super-graph is usually a **complete** graph
	- The edges can only come from the super-graph
- A graph may have many spanning trees
- The **cost** of a spanning tree is the sum of all the edge weights
- The minimum spanning tree (MST) is the spanning tree with the **minimum** cost
```ts
let x be a random node from V
let Vnew = {x}
let Enew = { }
while Vnew != V
	choose an edge {u,v} with minimal weight (u is in Vnew and v is not in
	Vnew)
	Vnew = Vnew + {v}
	Enew = Enew + { {u, v} }
end while
```

## Applications of MST

- Network Design
	- E.g. computer networks, telecommunications networks, transportation networks, water supply networks, etc.
- CfA redshift survey
	- MSTs used for understanding the large-scale structure of the universe
- Approximation algorithms for NP-hard problems
	- e.g. travelling salesman problem
- Cancer imaging
	- The British Columbia Cancer Research centre uses them to describe the arrangement of nuclei in skin cells


# Dijkstra's Algorithm

## Shortest Path problem

- The problem of finding a path between two nodes in a graph such that the sum of weights of its edges is minimised e.g.
	- Shortest path between two intersections on a road map
	- A network package being efficiently routed through the network

### Shortest Path example

- You want to find the shortest possible way from home to your favourite shop
- You know that there are roads on the way that are more congested and difficult to use than others, and you want to avoid those
- Edges that are more difficult are given a large weight, whereas edges that are easier are given a lower edge weight
- The shortest path found by the algorithm will try and avoid edges with larger weights


- Problem variations:
	- **Single-source shortest path problem** - shortest paths from source node to all other nodes in the graph
	- **Single-destination shortest path problem** - shortest paths from all nodes in the directed graph to a single destination node
	- **All-pair shortest path problem** - shortest paths between every pair of nodes in the graph
- Various algorithms for solving the problem: Dijkstra's algorithm, Bellman-Ford algorithm, A* search algorithm, Floyd Warshall algorithm, etc.

## Dijkstra's Algorithm

- Conceived by pioneer computer scientist Edsger Dijkstra
- The algorithm is a **greedy approach**
	- Making best (optimal) choice at each stage hoping that the end result is the best result
- Given a start, the algorithm finds the shortest paths between the start node and all other nodes in a graph

- Used to solve the shortest path problem
	- Both directed and undirected graphs
	- All edges **must have non-negative weights**
	- Graphs must be connected
- Many variants but the most common is to find the shortest paths from a source node to all other nodes in the graph
- Given an end destination, we can keep track of visited nodes and thus find the path

```ts
let unvisited = all unvisited nodes from G
let distance of start node = 0
let parents = a list of null
let distance of all other nodes = infinity
while unvisited is not empty
	let current node = node with the smallest distance from unvisited
	remove currentNode from unvisited
	if currentNode position is goal
		backtrack to get path
	end if
	for each neighbour in unvisited to currentNode
		let newDist = currentNodes distance + distance currentNode+neighbou
		if newDist < neighbours distance
			set neighbours distance to newDist
			set neighbours parent to currentNode
		 end if
	 end for
 end while
```

- The complexity of the algorithm depends on the implementation and the data structure:
	- The classic implementation is $O(n^2)$, n being the number of nodes of the graph
	- Using other implementations like heaps: $O(E+n\log n)$, $E$ is the number of edges and $n$ is the number of nodes of the graph


## Applications of Dijkstra's Algorithm

- Finding the Shortest Path
- GPS System
	- A geographical map as a graph
	- Locations in the map are nodes/vertices
	- Road between locations are edges
	- Weights of edges are distance between two locations
- Network routing
- Commercial shipping
- etc.

