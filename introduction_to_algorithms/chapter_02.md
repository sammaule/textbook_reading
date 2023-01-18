#### 2.1 Insertion sort

Solves the sorting problem 

keys - numbers to be sorted
satellite data - other data associated to keys
key + satellite data form a record

```
INSERTION SORT (A, n)
A - values to be sorted
n - number of values to sort

// start from the second card
1 for i = 2 to n
2 	key = A[i]
3	// Insert A[i] into the sorted subarray A[1:i-1]
4 	j = i - 1
5 	while j > 0 and A[j] > key
6 		A[j + 1] = A[j]
7 		j = j - 1
8 	A[j + 1] = key
```

Line 6 moves elements one position to the right, line 8 puts the key in the correct sorted position.

Loop invariant: "At the start of each iteration of the for loop of lines 1-8 the subarray A[1:i-1] consists of the elements originally in A[1:i-1] but in sorted order"

Loop invariants help show that algorithms are correct. To prove this you need three things:

1. Initialisation: True before first iteration of the loop (for insertion sort A[1] is sorted as only one element)
2. Maintenance: True before the next iteration of the loop (subarray is sorted by the for loop with the same elements)
3. Termination: The loop terminates and when it terminates the invarinace gives us a property that shows the algorithm is correct (terminates when i = n+1 so when A[i:n] is sorted)

**Exercises**

**2.1-1 Illustrate Insertion sort on array intially containing the sequence {31, 41, 59, 26, 41, 58}**

[Add photo from notebook]

**2.1-2 Consider the procedure SUM-ARRAY on the facing page. It computes the sum of the n numbers in array A[1:n]. State a loop invariant for this procedure, and use its initialization, maintenance, and termination properties to show that the SUMARRAY procedure returns the sum of the numbers in A[1:n].**

```
SUM-ARRAY (A,n)

1 sum = 0
2 for i = 1 to n
3     sum = sum + A[i]
4 return sum
```

Loop invariant - "At the start of each iteration of the for loop sum equals the sum of the sub array A[1:i-1]"

Initialisation - initially A[1:0] consists of no elements so the sum = 0 which is defined on line 1
Maintenance - At the end of each for loop the sum is equal to A[1:i-1] + A[i] so the loop invariant is still true
Termination - the for loop terminates when i = n+1 when the sum = A[1:n] which is the sum of the whole array.

**2.1-3 Rewrite the INSERTION-SORT procedure to sort into monotonically decreasing instead of monotonically increasing order.**

```
INSERTION SORT DECREASING(A, n)

// start from the second card
1 for i = 2 to n
2 	key = A[i]
3	// Insert A[i] into the sorted subarray A[1:i-1]
4 	j = i - 1
5 	while j > 0 and A[j] < key
6 		A[j + 1] = A[j]
7 		j = j - 1
8 	A[j + 1] = key
```

This only requires a change to the inequality sign on line 5. 

**2.1-4 Consider the searching problem:** 

**Input: A sequence of n numbers {a1; a2; ... ; a_n} stored in array A[1:n] and a value x.**

**Output: An index i such that x equals A[i] or the special value NIL if x does not appear in A.**

**Write pseudocode for linear search, which scans through the array from beginning to end, looking for x. Using a loop invariant, prove that your algorithm is correct. Make sure that your loop invariant fulfills the three necessary properties.**

```
LINEAR SEARCH (A, n)

1 for i = 1 to n
2	if A[i] = x
3		return i
4 return NIL
```

Loop invariant - "At the start of each iteration of the for loop the value x does not appear in A[1:i-1]"

Initialisation - this is an empty array so true
Continuation - the for loop continues only if x is not the value of A[i] so the invariant holds
Termination - the loop terminates either when the value x is found, or if n=n+1 so the algorithm is correct.

**2.1-5** Skipped

#### 2.2 Analysing algorithms

Analysing algorithms -> means predicting the resources that an algorithm requires, often computation time. 

To predict this you need a model of the technology it runs on. This books uses a RAM model of computation, with characteristics:

- Instructions execute one after the other - not concurrently
- Each instruction takes the same amount of time and data access takes the same amount of time
- Data types: integer, floating point and character
- Doesn't consider any memory hierarchies e.g. caches or virtual memory. 

While you can create more realistic models, the RAM model is generally an excellent predictor of performance on actual machines.

Analysis of insertion sort - can look at the cost of each line and the amount of times it needs to run in the best and worst case to show that it is linear wrt n in the best case (presorted) and quadratic in the worst case (reverse sorted).

Typically care more about the worst case run time: 

- Gives an upper bound which is often useful to have
- Worst case often occurs
- average case is often roughly equivalent to the worst case

To highlight the rate of growth of the runtime of an algorithm we use $\Theta$ for the worst case run time. This is roughly equivalent to "roughly proportional when n is large". Because we use the when n is large bit we care only about the largest factor of n.

**Exercises**

**2.2-1 Express the function $n^3/1000 + 100n^2 - 100n + 3$ in terms of ‚ $\Theta$-notation.**

$\Theta(n^3)$

**2.2-2 Consider sorting n numbers stored in array $A[1:n]$ by first finding the smallest element of $A[1:n]$ and exchanging it with the element in $A[1]$. Then find the smallest element of $A[2:n]$, and exchange it with $A[2]$. Then find the smallest element of $A[3:n]$, and exchange it with $A[3]$. Continue in this manner for the first $n-1$ elements of A. Write pseudocode for this algorithm, which is known as selection sort. What loop invariant does this algorithm maintain? Why does it need to run for only the first $n-1$ elements, rather than for all n elements? Give the worst-case running time of selection sort in $\Theta$-notation. Is the best-case running time any better?** 

```
SELECTION SORT

1 for i = 1 to n - 1
2    key = A[i]
3    for j = i + 1 to n
4        if A[j] < key
5            temp = A[j]
6            index = j
7    A[i] = temp
8    A[index] = key
```

Loop invariant in the outer loop "A[1:i] is sorted and all entries A[i+1:n] are larger than or equal to all entries in A[1:i]" and in the inner loop "All entries in A[i: j-1] are greater than or equal to key"

Only needs to run for the first n-1 elements as on the final iteration it will sort the last two numbers in the array. If element n-1 is less than element n there will be no change, if element n-1 is greater than n then the elements will switch positions and the array will be sorted.

The worst case run time is $\Theta(n^2)$. The algorithm requires scanning $(n-1)+(n-2)+...+1=\sum_{i=1}^{n-1}i$ which by arethmetic progression is $=1/2(n^2-n)$. The best case will still be in $\Theta(n^2)$ as it will still have to traverse the whole array just without doing any swapping at the end.

**2.2-3 Consider linear search again (see Exercise 2.1-4). How many elements of the input array need to be checked on the average, assuming that the element being searched for is equally likely to be any element in the array? How about in the worst case? 34 Chapter 2 Getting Started Using $\Theta$-notation, give the average-case and worst-case running times of linear search. Justify your answers.**

Skipped

**2.2-4 How can you modify any sorting algorithm to have a good best-case running time?**

You can do an initial check to see if the array is already in the correct order, and if so terminate immediately.

#### 2.3 Designing Algorithms

Insertion sort is an example of the incremental method for algorithm design - it increments across elements in the array until they are sorted. 

Another method for algorithm design is "divide and conquer" where the problem is split into multiple subcomponents which are solved recursively and then combined to provide an overall solution.

Merge sort is an example of a divide and conquer algorithm.

**Divide** the subarray A[p:r] into two adjacent subarrays, each of half the size by computing the midpoint
**Conquer** by sorting each of the two subarrays recursively using merge sort
**Combine** by merging the two sorted subarrays back into A[p:r]

This bottoms out when the subarray to be sorted has just one element.

The merge procedure is carried out in the combine step. This splits the subarray into two and then iterates from left to right in each array, placing the lowest value at the leftmost place in the original array. When this completes the subarray is sorted.

![[Screenshot 2023-01-12 at 10.43.02.png]]

Lines 1-3 -> run in constant time
Lines 4-7 -> $\Theta(n_L+n_R)=\Theta(n)$ time
Lines 8-10 -> constant time
Lines 12-27 -> Each iteration of the three while loops copies one value to A for a total of n iterations. Since each loop is constant time then this section is $\Theta(n)$

We can then define the full routine MERGE-SORT in pseudocode

```
MERGE-SORT(A, p, r)
1 if p >= r
2     return
3 q = floor((p+r)/2)
4 MERGE-SORT(A, p, q)
5 MERGE-SORT(A, q+1, r)
6 MERGE(A, p, q, r)
```

Analysing divide and conquer algorithms - this is often done by using a recurrence equation or recurrence, which describes the overall running time on input of size n in terms of the running time on smaller inputs. 

**Analysis of merge sort**
 
Divide -> the divide step just computes the middle of the subarray (line 3)
Conquer -> Recursively solve two problems of size n/2 which contributes $2T(n/2)$
Combine -> Merge procedure we know is in $\Theta(n)$ as above

The worst case runtime for merge sort is then $T(n)=2T(n/2)+\Theta(n)$

We can show that $T(n)=\Theta(n\lg n)$ if we assume n is exact power of two. 

We have that T(n) = c1 when n=1 and T(n) = 2T(n/2) +c2n when n>1

For n as exact power of two can show with recursion trees that the tree will have depth lg(n+1) and a cost $\Theta(n)$ at each level. Therefore the cost is in $\Theta(n\lg n)$.

2.3-1 Using Figure 2.4 as a model, illustrate the operation of merge sort on an array initially containing the sequence {3; 41; 52; 26; 38; 57; 9; 49}. 

Picture in notebook

2.3-2 The test in line 1 of the MERGE-SORT procedure reads r, then the subarray AŒp W r� is empty. Argue that as long as the initial call of MERGE-SORT.A; 1; n/ has n  1, the test r. 



2.3-3 State a loop invariant for the while loop of lines 12318 of the MERGE procedure. Show how to use it, along with the while loops of lines 20323 and 24327, to prove that the MERGE procedure is correct. 

2.3-4 Use mathematical induction to show that when n  2 is an exact power of 2, the solution of the recurrence T .n/ D ( 2 if n D 2 ; 2T .n=2/ C n if n > 2 is T .n/ D n lg n. 

2.3-5 You can also think of insertion sort as a recursive algorithm. In order to sort AŒ1 W n�, recursively sort the subarray AŒ1 W n  1� and then insert AŒn� into the sorted subarray AŒ1 W n  1�. Write pseudocode for this recursive version of insertion sort. Give a recurrence for its worst-case running time. 

2.3-6 Referring back to the searching problem (see Exercise 2.1-4), observe that if the subarray being searched is already sorted, the searching algorithm can check the midpoint of the subarray against v and eliminate half of the subarray from further Problems for Chapter 2 45 consideration. The binary search algorithm repeats this procedure, halving the size of the remaining portion of the subarray each time. Write pseudocode, either iterative or recursive, for binary search. Argue that the worst-case running time of binary search is ‚.lg n/. 

2.3-7 The while loop of lines 537 of the INSERTION-SORT procedure in Section 2.1 uses a linear search to scan (backward) through the sorted subarray AŒ1 W j  1�. What if insertion sort used a binary search (see Exercise 2.3-6) instead of a linear search? Would that improve the overall worst-case running time of insertion sort to ‚.n lg n/? 

2.3-8 Describe an algorithm that, given a set S of n integers and another integer x, determines whether S contains two elements that sum to exactly x. Your algorithm should take ‚.n lg n/ time in the worst case.

#### Problems

Skipped