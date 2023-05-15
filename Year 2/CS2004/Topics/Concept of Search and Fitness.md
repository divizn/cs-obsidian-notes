
# Recap of NP Hard problems

![](np-diag.png)

- NP hard problems are a class of problems that can't be solved the "traditional" way
- Typically these problems:
	- Have a "best known" computational complexity in exponential time, e.g. $O(n)=2^n$
	- e.g. $2^1=2,2^{10}=1024, 2^{95}=39614081257132168796771975168$
	- They have no direct analytical solution
- Thus, we may have to approximate a solution to them
- For some problems, we need to search for a solution from a (usually) very large number of possibilities
	- **Search problems**, i.e. searching for the answer in some **solution space**
- The solution spaces for many every day problems can be very, very large, too large to search exhaustively
	- Search algorithms to guide the search...
- The search algorithm may not find the optimal solution to the problem
	- It will give a good solution in **reasonable time**
- We often need special search algorithms known as **heuristics**

# Heuristic

- A heuristic is a "rule of thumb" or some loose set of guidelines
	- That may find a solution (not guaranteed)
	- e.g. find end of maze by keeping hand against one side of wall
- Usage of domain knowledge in the search process, speeds up the search process
- In AI, these are used to improve the performance of methods, in our case, search methods
	- Expert knowledge
	- Common sense


# Search Problems

- Many problems can be thought of as searching through candidate solutions to find one that is optimal
	- Systematically search through potential solutions **without** considering all of them
- We need some way to evaluate the fitness of the candidate solutions
	- Optimal = the fittest = the best
- Need to compare solutions and see which of the solutions are better or worse
- Also some sense of the adjacency (similarity) of solutions (or neighbourhood)


# Fitness

- In order to search for a solution, we must be able to compare potential solutions
	- e.g. is solution $s_1$ better than solution $s_2$?
		- Thus, we have the concept of fitness
	- We must derive a function (the **fitness/objective function**) that maps a solution to a value that rates how good the solution solves the problem in hand
	- We either try and **maximise** or **minimise** the fitness
	- A slight change in solution quality should result in a corresponding change in the fitness
		- Solution quality goes down $\rightarrow$ fitness goes down (decreases)
		- Solution quality goes up $\rightarrow$ fitness goes up (increases)


## Fitness landscapes

- It can be **helpful** to think of searching a landscape of solutions where:
	- The $x$ and $y$ co-ordinates represent a particular solution
	- Altitude ($z$ axis) represents the fitness of that solution
- This leads to the analogy what we wish to search for or climb peaks (or descend)

- The collection of **all possible solutions** can be considered as a high dimensional space, called the **search space** or **fitness landscape**
	- Each point in the search space represents one possible solution
- Often, some concept of distance between solutions exist and some concept of how "good" each point in the search space is **fitness/objective function**
- Techniques exist to map a high dimensional space to a two dimensional space, so we can plot the space/landscape



# Global and Local Optima

- The **global optimum** is the point or points in the search space with the **best** objective function evaluation
- A **local optimum** is the point (or points) in a subset/section of the search space with the **best** objective function evaluation
- **The subset or section of the search space in question may contain the global optima**
- Many search techniques can find local optima, but get "stuck" at them and cannot move on to find the global optima
	- e.g. Random Mutation Hill Climbing (RMHC)
