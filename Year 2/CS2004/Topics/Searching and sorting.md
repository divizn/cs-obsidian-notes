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



# Sorting in more detail

- Looking at:
	- Bubble sort
	- Quick sort
	- Radix sort
- We will also look briefly at other sorting algorithms

## Why bother with sorting?

- We talked about needing it for stuff like binary search
- Sorting applications are one of the most common algorithms
- They are implemented in computer games, network routing software, operating systems, AI, bin packing algorithms, etc.
- The sorting problem itself is easily understood
	- Not a lot of knowledge required to start implementing it
- The algorithms are quite small and manageable
	- They can be implemented in a short period of time
	- They are relatively simple to analyse

## Formal Definition of sorting

- The sorting problem is a mapping from $x$ to $y$ where 
	- $x$ and $y$ are both $n$ length real vectors (lists and/or arrays)
	- $y$ is a permutation of $x$ (different ordering)
	- $y_i <_{i+1}$ for all $i=0,....,n-1$ (or reverse)
- It is the problem of reordering items of an array in a certain order
- The algorithms can easily be applied to integers or character vectors
	- Sorting whole numbers
	- Sorting names and/or addresses
	- Essentially anything that can be ordered/compared

## Applications

- When an array is sorted, many problems involving this array becomes easier, for example: 
	- To search for a specific value
	- To find the smallest and/or largest value (min/max)
	- To count how many times a specific value appears in an array
	- To find out how unique are the values and delete duplicates
	- To do intersection and/or union between two different arrays

## Monkey sort

- AKA: Bogosort, stupid sort, slowsort, permutation sort
- Highly inefficient sorting algorithm
- Successively generates permutations of its input until it finds one permutation that is sorted
- Best case:
	- $O(n)$
- Worst case:
	- $O(n!)$


## Bubble sort

- It is one of the simplest sorting algorithms
- Repeatedly compare adjacent pairs of elements
- Swap the elements in pair putting the smaller element first
- When it reaches end of list, starts over
- It stops when no more swaps can be made
- If we compare pairs of adjacent elements and none are out of order, the list is sorted
- If any are out of order, we must have to swap them to get an ordered list
- Bubble sort will make passes through the list, swapping any elements that are out of order

```ts
let noSwaps = false
while noSwaps = false
	let noSwaps = true
	for i = 0 to n-2
		if x[i] > x[i+1] then
			swap x[i] and x[i+1]
			let noSwaps = false
		end if
	end for
end while
```

- Best case analysis
	- If the elements are in sorted order at the start, the `for` loop will compare the adjacent pairs but not make any changes
	- This means that the `noSwaps` variable will remain `true`
		- the `while` loop is only done once
	- Thus, comparisons are done, but no swaps
	- There are n-1 comparisons in the best case
- $\therefore B(n)=O(n)$

- Worst case analysis
	- If the best case, the while loop is done once, in the worst case the while loop needs to be done as many times as possible
		- This will be when the data is in **reverse order**
	- Each pass of the `for` loop must make at least one swap of the elements
	- The number of comparisons will be:
	- $$W(n)=\sum_{i=1}^{n-1}i={n-1n\over2}\equiv O(n^2)$$


## Quick sort

- Quick sort is a divide and conquer algorithm
- Quicksort picks an element from the list as the **pivot**, and partitions the list into two pieces:
	- Those elements smaller than the pivot value (not necessarily in order)
	- Those elements larger than the pivot value (not necessarily in order)
- Quicksort is then called **recursively** on both pieces (ALL DIVIDE AND CONQUER ALGORITHMS ARE IMPLEMENTED RECURSIVELY)


- Quicksort algorithm
```ts
if first < last then
	let pivot = pivotList(list,first,last)
	call quicksort(list,first,pivot-1)
	call quicksort(list,pivot+1,last)
end if
```

- `pivotList` algorithm
```ts
pivotValue = list(first)
pivotPoint = first
for index = first+1 to last
	if list[index] < pivotValue then
		pivotPoint += 1
		swap(list[pivotPoint],list[index])
	end if
end for
swap(list[first],list[pivotPoint])
```

- There are different variations of quick sort based on the different ways of picking the pivot:
	- Pivot always being the first element
	- Pivot always being the last element
	- Pivot is selected randomly
	- The median is chosen as the pivot


- Best case analysis
	- `pivotList` creates two parts that are the same size
	- And then all subsequent parts are the same size as the algorithm calls itself, this can be modelled as a binary tree
	- Summing up over the partitions we get $B(n)=B(nh)=O(n\log_2(n))$

- Worst case analysis
	- In the worst case, `pivotList` will do $n-1$ comparisons, but **creates one partition that has $n-1$ elements and the other will have no elements**
		- When will this happen?
	- Because we wind up just reducing the partition by one element each time
	- The worst case is given by:
	- $$W(n)=\sum^n_{i=2}(i-1)={n(n-1)\over 2}\equiv O(n^2)$$


## Comparison of Sorting Algorithms

| Method         | Best            | Average         | Worse           |
| -------------- | --------------- | --------------- | --------------- |
| Bubble Sort    | $O(n)$          | $O(n^2)$        | $O(n^2)$        |
| Insertion Sort | $O(n)$          | $O(n^2)$        | $O(n^2)$        |
| Merge Sort     | $O(n\log_2(n))$ | $O(n\log_2(n))$ | $O(n\log_2(n))$ |
| Quick Sort     | $O(n\log_2(n))$ | $O(n\log_2(n))$ | $O(n^2)$        |
| Selection Sort | $O(n^2)$        | $O(n^2)$        | $O(n^2)$                |

- We are interested in the worst case performance
- It is useful to consider the average
- Can we do $O(n)$ for the worst case?#


## Radix Sort

- Non-comparison sorting method
- The Radix sort method only works on binary or integer data
- Radix sort works by using a binary bucket sort for each binary digit
- We first "sort" by the least significant bit
- Split input into 2 sets (bucket) based on the bit - those that have a 0 or those that have a 1
	- The ordering of the data as they are put in each set (or bucket) must be maintained
- Then proceed to the next least significant bit and repeat until we run out of bits

![](radix-sort.png)

- The Radix sort takes $O(nb)$ time complexity
	- $n$ is the numbers items
	- $b$ is the numbers of bit bits (in the representation)
	- best, worst and average case
