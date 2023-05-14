## What
 
 - An **algorithm** is a set of steps for solving problems
 - Algorithms are everywhere
	 - In humans: 
		 - Preparing a meal (has steps to solve a problem)
		 - Navigate somewhere (has steps to solve a problem)
		 - Doing laundry (has steps to solve a problem)
	- In computers:
		- Doing a Maths problem (has steps to solve a problem)
		- Sorting a list (has steps to solve a problem)
		- Searching a list (has steps to solve a problem)

- An algorithm is any well-defined computational procedure that takes some value(s) as input and produces some value(s) as output
- An algorithm can be seen as a tool for solving a well-specified **computational problem**


## Why

- Some algorithms that solve the same problem can differ massively in their efficiency
- Computers may be getting faster but they are not infinitely fast
	- For example - sorting a list of billions of numbers could take a computer a very long time
	- If we do not make the algorithms efficient, then they may take too long to run


# Analysis of an Algorithm

- This is the indication of the time a computer will take to solve a problem given the size of the problem
- If we do not analyse our algorithms, we don't know how long they will take
- Runtime of an algorithm is abstract, and is usually measured in operations
	- This allows us to compare 2 algorithms independent of the speed of a computer
- Also known as the **computational complexity** of an algorithm



# The Fake Coin Problem

- You have 64 £1 coins ($N=64$)
- All the coins are supposed to be the **same weight and size**
- You find out that **one of the coins is fake** and **weighs less** than the rest
- We want to find the fake coin using a balance scale

- To outline an algorithm to find the fake coin, we need to consider:
	- How many times do you have to weight?
	- Easiest approach is not necessarily the best approach
	- What algorithm will take the shortest period of time
	- Need an algorithm that is efficient, for example can handle 10,000 ($N=10000$) coins

### Example Solutions

####  **Solution one pseudocode**

- Weigh 2 coins together till you find the fake

```haskell
if weight(left) == weight(right) then
	take next two coins
else
	coins are fake
endif
	repeat until fake coin found or no coins left to check
```

- For the worst case: 
	- The fake coin is the last or the one before the last
		- This would take 32 steps ($N \div 2$)
		- $O(N)$ - linear time
	- In the best case (first coin first or second), the same statement will only have to run once

#### **Solution two pseudocode**

- Split the set of coins into 2 subsets of equal size; ($N \div 2$)


```c
if weight(left) != weight(right) then
	lighter side containts the fake coin
	split the lighter n/2 coins
else neither side contains the fake coin
endif
```

- Started with $N=64$
- This algorithm divides the coin into 2 equal parts
- If fake coin is the 41st coin - we find the coin in 6 steps
- $N = 64 = 2^6$ - ($2$ because we split in 2, $6$ because of the amount of steps)
- So if $N = 2^k$, then $k = \log_2N$
- Therefore the time complexity of this algorithm is $O(\log(N))$ (we don't care about the base in time complexity)
 - This algorithm is called a **binary search** algorithm
	 - The number of splits is equivalent to the number of levels $k$ in the corresponding complete binary tree
- Since there is only one comparison on each level, the **worst case** is to conduct $\log(N+1)$



# Topics

[Foundation of Algorithm Analysis](Foundation%20of%20Algorithm%20Analysis.md)
[Mathematical Foundation](mathematical%20foundation.md)
[Searching and sorting](Searching%20and%20sorting.md)
