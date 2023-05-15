- Depth-first search (DFS)
- Exhaustive search
- Breadth-first search (BFS)
- A* search (A-star)
- Minimum Spanning Trees (MST)

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