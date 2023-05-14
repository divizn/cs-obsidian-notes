
# Comparing algorithms

- You have algorithm **A** and **B**
	- Both achieve the same thing
	- Which one do you choose?
- How would you compare them?
	- Low level - code of A vs code of B
	- High level - algorithm A vs algorithm B
- What are the criteria?
	- They are compared in terms of:
		- Efficiency
		- Time it takes
		- Resources consumed


# Run Time

- The running time of an algorithm varies with the input and typically grows with the input size]
- An algorithm may run faster on certain data sets than others
- Hence it would have the following run times:
	- **Best case**
		- Not very informative
		- Might not happen very often
	- **Average case**
		- Take all inputs and calculate time for all inputs
		- Sum all calculated values and divide by total inputs
	- **Worst case**
		- Easier to analyse
		- Crucial to applications such as air traffic control, surgery, finance and other real time applications


# Experimental studies

- Write a program implementing the algorithm
- Run the program with inputs of varying size and composition, multiple times
- Use a method such as `System.currentTimeMillis()` to get an accurate measure of the actual running time
- Plot the results to evaluate

## Limitations of experimental studies

- It is sometimes difficult to implement the algorithm
- Results may only be indicative of the running time for some inputs, but not for all possible inputs
- One algorithm can perform better than the rest for some inputs. For other inputs, another algorithm could be better
- In order to compare 2 algorithms, the same hardware and software must be used


## So what can we do?

- Can we calculate/estimate the running time without experiments?
- Is there an alternative to implementing and running a large number of experiments?
- Solution: **Asymptotic Analysis**


## Asymptotic Analysis

- The technique uses a high-level description of the algorithm instead of an implementation
- We evaluate the performance of an algorithm in terms of input size
- We calculate how does the time taken by an algorithm increase with the input size


## Estimating running-time

- Write down an algorithm using pseudocode
- In terms of a set of primitive operations
	- Count the number of steps
	- Consider worst case input
- Bound or "estimate" the running time
- This leads onto the Big-O notation for computational complexity


## T(n)

- Used to measure the running time/computation of an algorithm
- We refer to this resultant formulae as $T(n)$ where $n$ is the size of the input
- If there is more than one input, we might have $T(n,m, ...)$ where $n$ and $m$ are the sizes of the inputs
- We can use $T(n)$ to compute a **very** important property called the Big-O, $O(n)$ 


# Primitive Operations

- The basic computations performed by an algorithm
- Examples:
	- Evaluating an expression `x > y`?
	- Assigning a value to a variable `x = 0`
	- Indexing into an array -  for `A[0]` or `A[i]`, we might use the mathematical notation $a_0$ or $a_i$
	- Returning from a method

![](primitive.png)

