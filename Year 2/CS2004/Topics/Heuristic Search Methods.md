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