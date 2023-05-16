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


## Genes and chromosomes

- The technique of GA uses biological metaphors
	- Each **gene** is a binary digit
	- A **chromosome** is a single string of genes
- A **solution** to a problem is encoded as a chromosome
	- The encoding is called the **representation**
	- It must cover the whole **search space**
- A **fitness function** is needed to rate how good a solution a chromosome represents

## Knapsack Problem - Example

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


### Crossover

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


### Mutation

- Analogous to biological mutation
- Small random tweak of the gene (in the chromosome), to get a new solution
- Mutation allows the GA to explore more of the search space and avoid failing into local minima

- Example mutation operator
	- Each bit (gene) of a chromosome is given a chance (probability) of $MP$ of inverting
		- A '1' becomes a '0'
		- A '0' becomes a '1'


### Selection

- Aim to retain the best performing chromosomes from one generation to the next
- Forming new population
	- Equal in size to the original
- The chance of a chromosome surviving is proportional to it's fitness vs the total of the others
- Also known as the Survival of the Fittest via the Roulette Wheel
		- There are many other types


## GAs parameters

- $NG$ - Number of generations
- $PS$ - Population size
- $CP$ - Crossover Probability
- $MP$ - Mutation Probability
- $n$ - Number of Bits (Genes) making up each Chromosome


## Holland's GA Algorithm

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


## Evolutionary Computation

- GA belong to a family of techniques that are inspired from evolution theory
- They are typically aimed at solving optimisation problems
- They can be used to generate Artificial Intelligence e.g. in games and robots
- There methods come under the field of Evolutionary Computation
	- Evolutionary Programming (covered)
	- Genetic Programming (covered)
	- Evolutionary Strategies (not covered)
	- Learning Classifier Systems (not covered)
	- Estimation of Distribution Algorithms (not covered)



### Evolutionary Programming (EP)

 - EP is a similar approach to that of Genetic Algorithms
 - The emphasis is on **mutation** and there is **no crossover**
 - Every individual mutates, doubling the population
 - The mutation operators tend to be complex and/or adaptive
 - The selection/survival operator tends to be **Tournament Selection**

- With **tournament selection**, each member of the population is compared with a fixed number of other individuals
- For each comparison, the individual is awarded a point if it's fitness is better than the opponent
- The population is reduced back to its original size by retaining those with the highest score

![[Pasted image 20230516062801.png]]


### Genetic Programming (GP)

- GP is an evolutionary approach that extends Genetic Algorithms
- We evolve computer programs by Natural Selection
- There are many techniques, but we go through **Symbolic Regression** which  is a type of **Genetic Programming**

- With symbolic regression, a mathematical expression is represented as a tree structure
- Consider the expression: $x^2 + \ln(10)-7.3x$, then the tree representing this is:
![[Pasted image 20230516063111.png]]

