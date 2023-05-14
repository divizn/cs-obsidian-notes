# Sorting

- Sorting is one of the most common tasks in data analysis
	- Examples:
		- Print out a collection of employees sorted by salary
		- Print out list of names in alphabetical order
- There are many sorting algorithms
- **Selection sort** algorithm repeatedly finds the smallest element in the unsorted tail region of a list and moves it to the front


# Selection Sort Algorithm

- Sorting an array of integers
- Array in original order:
$$[11,9,17,5,12]$$
- Find the smallest and swap it with the first element:
$$[5,9,17,11,12]$$
- Find the next smallest
$$[5,9,17,11,12]$$
- If it is already in the correct place (like here), find the next smallest and swap it with the first element of the unsorted portion:
$$[5,9,11,17,12]$$
- Repeat until unsorted position is of length 1 (array is sorted):
$$[5,9,11,12,17]$$

## How fast is the algorithm?

- To find the smallest, visit $n$ elements + 2 operations for the swap
- To find the next smallest, visit $n-1$ elements $+2$ operations for the swap
- The last term is 2 elements visited to find the smallest $+2$ operations for the swap

- With an array of size $n$, count how many primitive operations are needed:
	- $(n+2)+[(n-1)+2]+...+(1+2)+2$
		- This can be simplified to:
			- ${n^2\over2}+{5n\over2}+2$
	- In Big-O, we don't care about most of that and we simplify it down a lot so it becomes:
		- $n^2$


# Search algorithms

- Searching algorithms - check for an element from any data structure where it is stored
- Classed into two categories:
	- Sequential search e.g. **linear search**
		- The list is traversed sequentially, and every element is checked
		- The list does **NOT** need to be sorted
	- Interval search e.g. **binary search**
		- A 'divide and conquer' algorithm
		- The list **MUST** be sorted


## Binary search

- Task: search for a key in a **sorted** list (e.g. 21)
- First check the middle list element:
$$[1,5,6,12,21,
\overset{\overset{\text{middle}}{\downarrow}}{23},26,42,46,51,58]$$
- If the key matches the middle element, we are done
- If the key is less than the middle element, the key must be in the first half (else second half)
- Repeat till you find the key (or check all items):
$$[1,5,\overset{\overset{\text{middle}}{\downarrow}}{6}\underline{12,21},23,26,42,46,51,58]$$

$$[1,5,6,\overset{\overset{\text{middle}}{\downarrow}}{12},\underline{21},23,26,42,46,51,58]$$


### Binary search vs linear search

- We have an unsorted list of a million elements, and we would like to find a specific element
- Would it be faster to use **binary search with selection sort** or **linear search**?
	- Linear search - $O(n)$
	- Binary search + selection sort - $O(\log n)+O(n^2)=O(n^2)$
- Linear search performs better


