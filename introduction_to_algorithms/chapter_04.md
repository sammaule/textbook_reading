## Divide and Conquer

Base case - problem simple enough to solve directly
Recursive case - perform divide, conquer and combine steps

Recursions bottom out when the reach a base case 

**Recurrence**: equation that describes a function in terms of its value on other, typically smaller, arguments.

General form of a recurrence is a function containing the recursive case and the base case. 

**Algorithmic recurrence**: A recurrence T(n) is algorithmic if for a threshold $n_0>0$:

1. For all n < n0 T(n) = $\Theta(1)$
2. For all $n \geq n_0$ every path of recursion terminates in a defined base case within  a finite number of recursive invocations.

#### 4.1 Multiplying square matrices

A divide and conquer algorithm for matrix multiplication:

We can split a matrix into four sub matrices and multiply using following equations
![[Pasted image 20230123144305.png]]

```
MATRIX-MULTIPLY-RECURSIVE(A, B, C, n)

1 if n == 1
2    c11 = c11 + a11 x b11  // base case
3    return
4 // Divide
5 partition A, B and C into n/2 x n/2 submatrices
6 // Conquer
7 MATRIX-MULTIPLY-RECURSIVE(A11, B11, C11, n/2)
8 MATRIX-MULTIPLY-RECURSIVE(A11, B12, C12, n/2)
9 MATRIX-MULTIPLY-RECURSIVE(A21, B11, C21, n/2)
10 MATRIX-MULTIPLY-RECURSIVE(A21, B12, C22, n/2)
11 MATRIX-MULTIPLY-RECURSIVE(A12, B21, C11, n/2)
12 MATRIX-MULTIPLY-RECURSIVE(A12, B22, C12, n/2)
13 MATRIX-MULTIPLY-RECURSIVE(A22, B21, C21, n/2)
14 MATRIX-MULTIPLY-RECURSIVE(A22, B22, C22, n/2)
```

T(n) - worst case time to multiply 2 n x n matrices using this procedure

We can ignore the base case when we state the recurrence. 

In line 5 we have a partition operation which takes $\Theta(1)$ time
Lines 7 - 14 call MATRIX-MULTIPLY-RECURSIVE 8 times each for 2 n/2 sized matrices

We can then give a recurrence equation for the running time as:

$$T(n) = 8T(n/1) + \Theta(1)$$

#### 4.2 Strassen's algorithm for matrix multiplication

Strassen developed an algorithm that could do matrix multiplication in less than $\Theta(n^3)$ time. Not going to go into detail on this section.

#### 4.3 The substitution method for solving recurrences

Substitution method for solving recurrences has two steps:

1. Guess the form of the solution using symbolic constants
2. Use mathematical induction to show that the solution works, and find the constants

#### 4.4 The recursion tree method for solving recurrences

Recursion tree - each node represents the cost of a single subproblem. 

To solve:

- sum the costs within each level to get the per-level costs
- sum all the per-level costs to get the total cost

For example for the recursion equation $T(n) = 3T(n/4) + \Theta(n^2)$

If we assume that n is a factor of 4 then the recursion tree will bottom out when $n/4^i=1$ which solving for i gives $i= \log_4n$

You can then sum the cost of each level to get the cost for the entire tree. 

#### 4.5 The master method for solving recurrences

Provides a cookbook for solving recursions of the form $T(n)=aT(n/b)+f(n)$ 

driving function: f(n) bit
master recurrence - a recurrence of the general form given above

The master theorem:

The asynmptotic behaviour of T(n) can be characterised as follows:

1. If the exists a constant $\epsilon >0$ such that $f(n)=O(n^{\log_b a-\epsilon})$ then $T(n)=\Theta(n^{\log_b a})$
2. If the exists a constant $k \geq 0$ such that $f(n)=O(n^{\log_b a} \lg^k n)$ then $T(n)=\Theta(n^{\log_b a} \lg^{k+1}n)$
3. If there exists a constant $\epsilon > 0$ such that $f(n) - \Omega(n^{\log_b a+\epsilon})$ and if f(n) satisfies the regularity condition $af(n/b) \leq cf(n)$ for some constant $c < 1$ and all sufficiently large n then $T(n) = \Theta(f(n))$ 

$n^{\log_b a}$ is the watershed function
f(n) is the driving function

In all of the three cases we compare the watershed function to the driving function.

* If the watershed function grows (asympototicall and polynomially) faster than the driving function then case 1 applies. This would be when the total cost of the leaves dominates the costs from the internal nodes.
* Case 2 applies if they grow at the same asymptotic rate
* Case 3 applies when the driving function grows faster than the watershed function. This is when the root cost dominates the cost of all other nodes in the recursion tree.



