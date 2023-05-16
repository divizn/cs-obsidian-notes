# HC and SA

## Random Mutation Hill Climbing (RMHC)

- The RMHC algorithm is an iterative search method
- Aims to find a point in the search space that maximises some objective function (fitness)

- The RMHC algorithm starts off at some **random** point in the search space
- It then looks randomly at its **close neighbours** until it finds one with a **better** fitness
- The hill climbing algorithm then continues searching for improvement from this **new point**

- This is rather like the analogy of a hiker trying to climb up a hill in the fog
- They feel around themselves until they find a nearby direction that goes up
- They then move to this higher point and continue searching

 ![[Pasted image 20230515180727.png]]
- The hill climbing algorithm can easily get "stuck" in a local optima, e.g.:
![[Pasted image 20230515180903.png]]
	- From the starting point, the algorithm will **never** reach the global optima



## Stochastic Hill Climbing (SHC)

- The RMHC algorithm can have very variable performance
- We need to improve upon it to escape local optima
- We can do this by letting the algorithm accept worse fitness function values during its search
- This is the basis of the SHC algorithm
	- The chance of accepting is a function of how bad the change is
	- A very bad change will have a small change of being accepted
	- A slightly bad change will be accepted more often
	- Many ways of doing this, e.g. relies on **decision** function
- We accept a new solution according to the following equation:
$$Pr(accept)={1\over 1+e^{(f'-f)\mid T}}$$
- Here:
	- $f'$ is the new fitness
	- $f$ is the old fitness
	- $T$ is a parameter (set to 25 for the 1000 prime scales problem)
- The correct choice of $T$ can be **very** difficult
- We get an average best of 8.0
	- 10 runs of 1000 iterations as in the RMHC example


## Random Restart Hill Climbing

- A **very** effective version of the Hill Climbing algorithm
- Here we run the normal RMHC algorithm a number of times and record the best
	- i.e. we start off in **different** sections of the search space
	- For example, we might run it 10 times for 100 iterations rather than once for 1000 iterations
- For our Scales example, we get an average best of 6.2


## Simulated Annealing

- Another method to try and improve the Hill Climbing algorithm
- it allows a worse solution to be accepted so that local maximums can be circumnavigated
	- Sometimes you need to **search and explore** instead of always **improve**
- The term "annealing" refers to the fact that the chance of accepting a worse solution reduces as the algorithm progresses
	- An analogy to the annealing process in metallurgy
	- When you take a molten hot metal and you cool it down slowly for it to reach its stable form


## A note about HC and SA

- All of the HC and the SA algorithms search for a good solution by starting at a random point and then examining neighbouring points
- This type of search is known as a **local or neighbourhood** search method



# Advanced Heuristic Search Methods

## Genetic Algorithms

- Genetic Algorithms (GA) are a powerful tool that can perform numerical optimisation and AI search
- It was inspired by evolutionary biology
- GAs can help in areas where there seems to be no solution
- GAs can usually find a partial answer
	- Other methods may well do better

### Controversies (Biological Evolution)

- GA is controversial as it takes ideas from biological evolution
- It tries to "mimic" evolution
- Evolution is the change of a **gene** pool over time
- A gene is a biological hereditary unit that is passed on (usually unaltered) for many generations
- Genes are contained within the nucleus of a cell, within Chromosomes
- Most organisms have multiple chromosomes
- The gene pool is a set of all genes for a specie
- If environment changes - gene pool must change too (for survival)
	- This process is called adaptation
	- Happens all the time
- Genes **mutate** through random chance
- Individuals are selected/survive through natural selection
- Populations evolve and breed through recombination


### Genes and chromosomes

- The technique of GA uses biological metaphors
	- Each **gene** is a binary digit
	- A **chromosome** is a single string of genes
- A **solution** to a problem is encoded as a chromosome
	- The encoding is called the **representation**
	- It must cover the whole **search space**
- A **fitness function** is needed to rate how good a solution a chromosome represents

### Knapsack Problem - Example

- Given $n$ items, each with a **weight** and a **value**, determine the items to include so that the total *weight is less than or equal to a given limit and the total value is as large as possible*

- We could solve this with a Genetic Algorithm
- The representation could be as follows (there may be **invalid chromosomes**):
$$[0,1,1,0,0,1,1,0,0,0]$$
- The population is the number of chromosomes "alive" at any one time
- The term generations is the number of time breeding has occurred

- Create a population of random chromosomes
- Each chromosome in the population is scored using a fitness function
- Create a new generation through genetic operators called **selection, crossover and mutation**
- Repeat until done - best solution to the problem


#### Crossover

- Analogous to recombination or breeding
- Typically genetic material from 2 parents are combined to create **children**
- Various crossover operators:
	- One-point crossover
	- Uniform crossover

- One-point crossover:
	- Chromosomes (with $n$ genes) move to the crossover pool with $CP$ chance.
	- Each are randomly paired up ($A$ and $B$)
	- Two children are created ($C$ and $D$)
	- A random number $p$ between 2 and $n-1$ is generated for each parent pair:
		- $1..p$ of $A$ become $1..p$ of $D$
		- $p+1...a$ of $A$ becomes $p+1...a$ of $C$
		- $1..p$ of $B$ becomes $1...p$ of $C$
		- $p+1...n$ of $B$ becomes $p+1..n$ of $D$
	- Put them in the population

- Uniform crossover
	- Uniform crossover is a more powerful extension
	- For each gene, there is a 50% chance that child $C$ gets the gene from parent $A$ and 50% for $B$
	- Child $D$ gets the gene that child $C$ does not


#### Mutation

- Analogous to biological mutation
- Small random tweak of the gene (in the chromosome), to get a new solution
- Mutation allows the GA to explore more of the search space and avoid failing into local minima

- Example mutation operator
	- Each bit (gene) of a chromosome is given a chance (probability) of $MP$ of inverting
		- A '1' becomes a '0'
		- A '0' becomes a '1'


#### Selection

- Aim to retain the best performing chromosomes from one generation to the next
- Forming new population
	- Equal in size to the original
- The chance of a chromosome surviving is proportional to it's fitness vs the total of the others
- Also known as the Survival of the Fittest via the Roulette Wheel
		- There are many other types


### GAs parameters

- $NG$ - Number of generations
- $PS$ - Population size
- $CP$ - Crossover Probability
- $MP$ - Mutation Probability
- $n$ - Number of Bits (Genes) making up each Chromosome


### Holland's GA Algorithm

![[Pasted image 20230516060951.png]]

- Initial population
	- Create an initial population of random solutions to the problem
- Crossover
	- Pair up those allowed to breed and recombine genes from the parents to produce new children
- Mutation
	- Mutate some of the genes of some of the chromosomes
- Kill of invalid chromosomes
	- Remove invalid solutions from the population
- Survival of the fittest
	- Select the fittest to survive the next generation


### Evolutionary Computation

- GA belong to a family of techniques that are inspired from evolution theory
- They are typically aimed at solving optimisation problems
- They can be used to generate Artificial Intelligence e.g. in games and robots
- There methods come under the field of Evolutionary Computation
	- Evolutionary Programming (covered)
	- Genetic Programming (covered)
	- Evolutionary Strategies (not covered)
	- Learning Classifier Systems (not covered)
	- Estimation of Distribution Algorithms (not covered)



#### Evolutionary Programming (EP)

 - EP is a similar approach to that of Genetic Algorithms
 - The emphasis is on **mutation** and there is **no crossover**
 - Every individual mutates, doubling the population
 - The mutation operators tend to be complex and/or adaptive
 - The selection/survival operator tends to be **Tournament Selection**

- With **tournament selection**, each member of the population is compared with a fixed number of other individuals
- For each comparison, the individual is awarded a point if it's fitness is better than the opponent
- The population is reduced back to its original size by retaining those with the highest score

![[Pasted image 20230516062801.png]]


#### Genetic Programming (GP)

- GP is an evolutionary approach that extends Genetic Algorithms
- We evolve computer programs by Natural Selection
- There are many techniques, but we go through **Symbolic Regression** which  is a type of **Genetic Programming**

- With symbolic regression, a mathematical expression is represented as a tree structure
- Consider the expression: $x^2 + \ln(10)-7.3x$, then the tree representing this is:
![[Pasted image 20230516063111.png]]

- Initially determine the set of terminals and functions
- The fitness of such a tree is a function of the observed data versus the calculated data resulting from evaluating the expression the tree represents
- Crossover and mutation are redesigned to handle tree structures
- The genetic programming algorithm is virtually the same as the genetic algorithm


## ASO, PSO and Swarm Intelligence

### Swarm Intelligence

- Inspiration from nature e.g. bees, fish , birds, ants (swarm)
	- Social insects:
		- Can solve many problems like finding food, feeding the brood, defending the nest, and building a nest
		- Several million years of success:
			- Efficient
			- Flexible
			- Robust
- It is the **interaction** of many simple parts creating **complex** behaviour
	- The net effect is group's collective wisdom is greater than the sum of the individuals
- Emergent behaviour as a side effect of the system
	- Behaviours that are not programmed or designed in the algorithm
		- e.g. find the shortest path to a food source; walk in a straight line in some studies
	- A challenge in theoretical physics to find minimal statistical models that capture these behaviours
- **Decentralised**, **self-organised** systems
- Only simple rules for each individual
	- Simple but extremely powerful
	- The problems are usually difficult to define
	- Solutions result from the behaviour and interactions between individual agents
	- Solutions are emergent in the systems

#### Swarm Intelligence Algorithms

- Most popular Algorithms:
	- Ant Colony Optimisation (ACO)
	- Particle Swarm Optimisation (PSO)


### Ant Colony Optimisation

- A **heuristic** optimisation method inspired by **biological systems**
- A multiple agent based approach for solving difficult combinatorial optimisation problems
	- Mainly **graph** based problems
		- Travelling salesman, vehicle routing, sequential ordering, graph colouring, manufacturing scheduling, routing in communications networks, etc.

#### Ant Behaviour

- Ants (blind) navigate from nest to food sources
- The shortest path is discovered via pheromone trails
	- Each ant moves at random (biased)
	- **Pheromone** is deposited onto the path
	- Ants detect the lead ants path and are inclined to follow
	- More pheromone on the path means an increased probability of the path being followed
	- Pheromone upgrade: **evaporation**

- Stigmergy:
	- Indirect coordination/communication between agents or actions
		- Individual behaviour modifies the environment, which in turn modifies the behaviour of other individuals
		- Stimulates the performance of subsequent actions leading to the spontaneous emergence of **coherent**, apparently **systematic** activity
		- Reduces (or eliminates) communication between agents
		- Supports efficient collaboration between simple agents
		- Produces complex, seemingly intelligent structures, without need for any planning, control, or even direct communication between the agents

#### 3 Key Rules in ACO

- Route selection
- Pheromone update
- Pheromone evaporation

##### Route Selection

- At the beginning of the search process, a constant amount of **pheromone** is assigned to all arcs
- When located at a node $i$ an ant $k$ uses the pheromone trail to compute the probability of choosing $j$ as the next node:
	$$p_{ij}^k\propto {Pheromone\ from\ node\ i\ to\ j\over Sum\ of\ Pheromone\ for\ all\ valid\ paths}$$
- The probability is zero for nodes that are unreachable from node $i$
- Similar to **Roulette Wheel Selection** in Genetic Algorithms

##### Pheromone Update

- The pheromone value of an arc ($i,j$) is updated when traversed by ant $k$ as follows:
$$t_{ij}'=t_{ij}+\Delta t_{ij}^k$$
$$t^k_{ij}\propto{1\over The\ Tour\ Length\ of\ Ant\ k\ so\ far}$$
- The probability of an arc being taken by subsequent ants is proportional to how **good** it was deemed by ants that have already traversed it


##### Pheromone Evaporation

- The pheromones "evaporate" by applying the following equation to all the arcs:
$$t'_{ij}=(1-p)t_{ij}$$
- Here $p \in (0,1)$ is a parameter
- Similar to the cooling rate heuristic for the temperature in Simulated Annealing

#### ACO Advantages and Disadvantages

- Advantages:
	- Can be used in dynamic applications
	- Rapid discovery of good solutions
	- Performs better against other global optimisation techniques
	- Easily parallelised
- Disadvantages:
	- Theoretical analysis is difficult 
	- Time to convergence uncertain
	- Performed poorly for large scale problems (e.g. >75 cities TSP)


### Particle Swarm Optimisation (PSO)

- Population based stochastic optimisation technique
- It uses a number of agents (particles) that constitute a swam moving around the search space looking for the best solution
- Each particle is treated as a point in an n-dimensional space which adjusts its "flying" according to its own flying experience as well as the flying experience of other particles


#### PSO Concepts

- Each particle keeps track of
	- Its coordinates in the solution space
	- Associated fitness
	- The best solution and fitness it has achieved so far
		- This value is called the personal best $P_{best}$
- The PSO algorithm also tracks the best value obtained so far by any particle in swarm
	- This value is called the global best $G_{best}$
- The basic concept of PSO lies in accelerating each particle towards its personal best and global best locations, with a random weighted acceleration at each time step
	- Inspired by "Bolds"
 - Each particle tries to modify its position using the following information:
	 - Current position
	 - Current velocity
	 - Distance between current position and $p_{best}$
	 - Distance between current position and $G_{best}$

![[Pasted image 20230516073833.png]]

![[Pasted image 20230516074013.png]]

##### Inertial Weight

- A large inertia weight ($w$) facilitates a global search while a small inertia weight facilitates a local search 
	- $\therefore$ larger weight = greater global search ability (exploration)
	- $\therefore$ smaller weight = greater local search ability (exploitation)
- By linearly decreasing the inertia weight from a relatively large value to a small value through the course of the PSO run gives the best PSO performance compared with fixed inertia weight settings
- Keep a proper balance between exploration and exploitation to avoid premature convergence to a local optimum yet still ensure a good rate of convergence to the optimum


#### PSO Advantages and Disadvantages

- Advantages:
	- Many optimisation applications in science and industry, including where GA can be applied, image recognition, training ANN (neural network), etc.
	- Simple implementation and less parameter tuning
	- Easily parallelised
- Disadvantages
	- Tendency to a fast and premature convergence
	- Slow convergence


#### PSO comparison with Evolutionary Computation (EC)

- No selection operation in PSO
	- All particles in PSO are kept as members of the population
	- PSO (and ACO) are the only algorithms (population based Heuristic search) that do not implement the survival of the fittest operator
- No crossover operator in PSO
- The PSO update formulae resembles mutation in EP


## Bin Packing and Data Clustering

### Bin Packing

- Fitting items effectively into a container
- The **bin packing** problem is where a number of $n4$ items of size $x_1,.....x_n$ need putting into the smallest number of bins (or boxes) of size/capacity $c$


#### Bin Packing algorithms

- Combinatorial problem
- There are a large number of bin packing applications:
	- Filling recycle bins
	- CD/Tape compilations
	- TV/Radio advertisements
- There are a large number of bin packing methods
- We will look at the **first-fit decreasing** bin packing algorithm

##### First-Fit Decreasing (FFD)

- This algorithm takes advantage of the idea packing a suitcase
- $n$ empty bins are created and numbered $1..n$
- The items that need to be packed are **sorted** in decreasing order
- Each item is packed into the first bin it will fit into, starting at the largest first
- Empty bins (on completion) are discarded/ignored
- e.g.
![[Pasted image 20230516075945.png]]


### Clustering

![[Pasted image 20230516080040.png]]

- Patterns - physical objects (the animals/plants)
- Clusters - categories of objects (the categories (animal kingdom, plant kingdom))
- Features - attributes of objects (colour: green, brown, grey)

#### Patterns, clusters and features
![[Pasted image 20230516080324.png]]

### Data Clustering

- **Data Clustering** is a common technique for data analysis
	- Used in many fields e.g. pattern recognition, image analysis and bioinformatics, etc.
- Data clustering is the process of arranging objects (as points) into a number of sets ($k$) according to "distance"
	- Each set (ideally) shares some common trait - often similarity or proximity for some defined distance measure
	- Each set will be referred to as a cluster/group
	- For the purposes of this module, each set is **mutually exclusive**, i.e. an item cannot be in more than one cluster
	- The objects in different clusters are "dissimilar" to the ones in others

#### Why Cluster?

- Knowing which objects are highly related to others is useful within data analysis
	- Less complex to model
	- A useful pre-processing tool
	- May give insight into the unknown properties of some of the objects

#### Applications

- Retail marketing
	- Retail companies often use clustering to identify groups of households that are similar to each other:
		- Household income
		- Household size
		- Head of household occupation
		- Distance from nearest urban area
- Sports science
	- Data scientist for sports teams often use clustering to identify players that are similar to each other on the following factors (different for other games):
		- Points per game
		- Rebounds per game
		- Assists per game
		- Steals per game
- Health insurance
	- Health insurance companies may collect the following information about households:
		- Total number of doctor visits per year
		- Total household size
		- Total number of chronic conditions per household
		- Average age of household members

#### Cluster representation

![[Pasted image 20230516081533.png]]
![[Pasted image 20230516081601.png]]


### Data similarity

- Distance between various data points from the data
- Many methods designed to work on **Distance Metrics** or **Similarity** between rows
	- e.g. K-Means
- Rows are compared to each other and a measure of how similar they are is used by the clustering methods
	- Similar rows are placed into the same cluster
- The performance of many clustering algorithms depends on selecting a good distance function
- Many ways to measure similarity between objects we're clustering
	- Eucliedean
	- Correlation
		- Pearson
		- Spearman
		- Kendal
	- Manhattan
	- etc.

#### Euclidean Distance

- The shortest distance between two points
- In the two dimensional case, this is the length of the right angled triangle constructed between two points (Pythagoras Theorem)
- The Euclidean distance between two $n$-dimensional points or two data objects stored as a row vector is defined as followed:
![[Pasted image 20230516081956.png]]

