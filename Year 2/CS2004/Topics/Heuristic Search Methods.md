# Random Mutation Hill Climbing (RMHC)

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



# Stochastic Hill Climbing (SHC)

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


# Random Restart Hill Climbing

- A **very** effective version of the Hill Climbing algorithm
- Here we run the normal RMHC algorithm a number of times and record the best
	- i.e. we start off in **different** sections of the search space
	- For example, we might run it 10 times for 100 iterations rather than once for 1000 iterations
- For our Scales example, we get an average best of 6.2