
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

## Heuristic Search

- NP-Hard problems cannot be solved in a straightforward manner
- So, we need to develop **approximation algorithms** to solve these problems
- A type of method called **Heuristic Search** can be used to try and find a solution
- We search for the best solution from a very large number of potential solutions
- However, a heuristic method might NOT always find the BEST solution
	- It aims to find a good solution in a reasonable amount of time
- We score the worth of each using a **Fitness Function**
- We try and find a solution that minimises or maximises the fitness
	- Depending on how we rate the solution
- The computational complexity of Heuristic search is often very difficult to define
- We therefore often rate their performance in terms of the **number of fitness function calls**
	- We compute the Big-O of this function
- We aim to choose the method that finds us the global optimum in the smallest number of fitness function evaluations


# Search Problems

- Many problems can be thought of as searching through candidate solutions to find one that is optimal
	- Systematically search through potential solutions **without** considering all of them
- We need some way to evaluate the fitness of the candidate solutions
	- Optimal = the fittest = the best
- Need to compare solutions and see which of the solutions are better or worse
- Also some sense of the adjacency (similarity) of solutions (or neighbourhood)


## Fitness

- In order to search for a solution, we must be able to compare potential solutions
	- e.g. is solution $s_1$ better than solution $s_2$?
		- Thus, we have the concept of fitness
	- We must derive a function (the **fitness/objective function**) that maps a solution to a value that rates how good the solution solves the problem in hand
	- We either try and **maximise** or **minimise** the fitness
	- A slight change in solution quality should result in a corresponding change in the fitness
		- Solution quality goes down $\rightarrow$ fitness goes down (decreases)
		- Solution quality goes up $\rightarrow$ fitness goes up (increases)


### Fitness landscapes

- It can be **helpful** to think of searching a landscape of solutions where:
	- The $x$ and $y$ co-ordinates represent a particular solution
	- Altitude ($z$ axis) represents the fitness of that solution
- This leads to the analogy what we wish to search for or climb peaks (or descend)

- The collection of **all possible solutions** can be considered as a high dimensional space, called the **search space** or **fitness landscape**
	- Each point in the search space represents one possible solution
- Often, some concept of distance between solutions exist and some concept of how "good" each point in the search space is **fitness/objective function**
- Techniques exist to map a high dimensional space to a two dimensional space, so we can plot the space/landscape




## Global and Local Optima

- The **global optimum** is the point or points in the search space with the **best** objective function evaluation
- A **local optimum** is the point (or points) in a subset/section of the search space with the **best** objective function evaluation
- **The subset or section of the search space in question may contain the global optima**
- Many search techniques can find local optima, but get "stuck" at them and cannot move on to find the global optima
	- e.g. Random Mutation Hill Climbing (RMHC)
![](glob-loc-optima.png)


## Representation

- When we are trying to solve a search based problem, we need a way to represent a potential solution
- This is usually a mathematical and/or data structure based way of describing the solution to a problem
- A good representation:
	- Should be a one-to-one mapping
	- No redundancy
	- No ambiguities
	- All potential solutions should be represented


## The Scales Problem

> Given $n$ objects of various weights, split them into two equally heavy piles (or as equal as possible)


- We have $n$ weights that are $W=[W_1,W_2,...W_n]$ in weight ($W_i>0$)
- We want to divide them into two equal piles in weight, or as equal as possible
- We are going to work with the general case, not a specific set of given weights, we want to solve the problem for **any** $W$


- We first look to see if there is a simple or standard method to solve the problem
	- For this example problem, there is not
- So, we need to:
	- **Design a representation**
	- **Construct a fitness function**
	- **Apply a heuristic search method**

##### Representation

- Each weight is either on the left hand side, or the right hand side
- Given that we have $n$ items into two piles/sets, we could use a *binary representation*
- We represent a solution as an **$n$ length binary string** (or array/vector/list) where:
	- A zero in position $i$ means that weight $i$ is on the left side of the scales
	- A one in position $i$ means that the weight $i$ is on the right side of the scales
	- This can represent all possible allocations
	- We will refer to this string as $S$ and each bit as $S_i$
	- If $S_i=0$, then weight $i$ is on the left hand side scale
	- If $S_i=1$, then weight $i$ is on the right hand side scale


##### Fitness

- We now need to design an appropriate fitness function
- This function should score on **how good a solution is at solving our problem**
- What's the aim of the problem?
	- Equal balancing (or as near as possible)
- Balanced would be when the sum of the weights on the left hand side (LHS) of the scales equals the sum of the right hand side (RHS)
- The worse this difference is, the worse our solution is at solving the problem
- The best fitness would be 0 (scale balanced)
- The worst fitness would be when the weights are on either the left, or right hand side
- Thus, meaning this is a **minimisation** problem
- Let $L$ = Sum of LHS
- Let $R$ = Sum of RHS
- Fitness = $\mid L-R\mid$ (absolute cause we only care about difference)
- So our **fitness function** will take 2 parameters:
	- A **potential solution** - a binary string of length $n$
	- A **set of weights** - a real vector/array of length $n$
- It will then return a real number (positive cause absolute)
- Each weight $w$, will either be added onto the left hand side $L$, or the right hand side $R$
- So we can iterate through each weight adding it to $L$ or $R$ depending on what side of the scales the representation specifies the weight is on 

![](scales-fitness.png)


##### Heuristic

- Need to search through a number of possible $S$ until we find the best one
	- i.e. When $F(S,W=0)$
	- or as close to 0 as possible
- We therefore need to apply an appropriate heuristic search method:
	- **Random Mutation Hill Climbing (RMHC)**
	- **Stochastic Hill Climbing (SHC)**
	- **Random Restart Hill Climbing (RRHC)**
	- **Simulated Annealing (SA)**
	- **Genetic Algorithms (GA)**
	- **Particle Swarm Optimisation (PSO)**
	- **Tabu-Search**
	- **Iterated Local Search**
	- **Evolutionary Programming (EP)**

