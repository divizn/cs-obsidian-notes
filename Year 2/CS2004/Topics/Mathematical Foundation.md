# What is covered

- Variables
- Sets
- Equations
- Functions
- Subscripts
- Summation
- Products


# Variables

- A **variable** is a symbol used to represent a mathematical construct
	- e.g. numbers, sets, lists, vectors, matrices
	- Often lower case letter or Greek letters are used
		- e.g. $x, y, z, \omega, \alpha, \beta$ 
- Variables in Mathematics are treated the same as variables within a programming language
- They can be thought of as a box containing a value that can be read from or written to



# Sets

- A set is a collection of objects called elements
- Sets can be finite or infinite
- A set has **no order**
- A set only contains **one copy** of an item

- Some well known sets:
	- $\mathbb{R}$ - Real numbers
	- $\mathbb{Z}$ - Integers
	- $\mathbb{N}$ - Natural numbers (integers $\ge$ 0)
	- The alphabet
- $a \in A$: an item $a$ is a member of set $A$
	- $\notin$: not a member
- $\mid A \mid$ is the cardinality of A, i.e. how many items in A
- The empty set: $\phi =$ {}


## Set operators

- A = {1,2,4,6,7}
- B = {2,3,5,8,9}

- Intersection (and):
	- $A \cap B =$ {2}
- Union (or):
	- $A \cup B =$ {1,2,3,4,5,6,7,8,9}

- **Subset**
	- If $A$ is a set, and $B \subseteq A$ (then $B$ is a subset of $A$)
- **Superset**
	- In the example above, $A$ is a superset of $B$


# Equations

- An **equation** uses mathematical operators to relate one set of variables or numbers to another set of variables or numbers
- For example:
	- $2+2 = 4$
	- $y = mx + c$
	- $ax^2 + bx + c = 0$
	- $(x-a)^2 + (y-b)^2 = r^2$


# Function

- A **function** is a relation that uniquely associates members of one set with members of another set
	- e.g. $y=x+1 -> f(x)=x+1$
- Functions can take parameters
	- e.g. $f(x,y)=2x+y$

- Function we need to know is the **exponential function**
	- $f(x)=\exp(x)=e^x$


# Subscripts

- A **subscript** is a natural number that indexes a list of variables
	- For example
		- Let $X$ be the list (or vector) $[x_1,....,x_n]$
			- To access any element, we use the notation $x_i$, where $1\le i\le n$ 
			- We use the notation $\mid X\mid$ to refer to the number of elements in the list $X$, which is $n$ in this case


# Summation

- To sum all the elements, we would use this notation:
$$S=\sum_{i=1}^{n}x_i$$
$$s=x_1 + x_2 + x_3 + ...x_n$$

# Products

- Let $X$ be the list $[x_1,.....,x_n]$, then if we want to multiply together all of the elements, we would use the notation:
$$S=\prod_{i=1}^nx_i$$


# Permutations

- The number of ways that $r$ ordered items can be picked (**arranged**) from $n$ items
- Defined as:
$$P^n_r={n!\over(n-r)!}$$


# Combinations

- The number of ways that $r$ unordered items can be picked (**selected**) from $n$ items
- Defined as:
$$C_r^n={\begin{pmatrix}n\\r\end{pmatrix}}={n!\over r!(n-r)!}$$

## Permutations and combinations

- If the order is important, then we use **permutations**, otherwise we use **combinations**


# Logarithms

- A **logarithm** is the power to which a number is raised to get some other number
	- $\log_{10}100=2$ because $10^2=100$
- There are logarithms using different base units
	- $\log_28=3$ because $2^3=8$
- The most common logarithms are base 10 and natural logarithms
- A base 10 logarithmic equation is usually written in the form:
	- $\log a=r$ 
