## The Role of Algorithms in Computing

#### 1.1 Algorithms

"Informally, an algorithm is any well-defined computational procedure that takes some value, or set of values, as input and produces some value, or set of values, as output in a finite amount of time."

Can also be defined as a tool for solving a specfic computation problem (defined formally as the inputs and desired output).

"A data structure is a way to store and organize data in order to facilitate access and modifications."

Hard problems - NP-complete noone knows whether efficient algorithm exists for NP-complete problems. Travelling salesman problem is an example of an NP-complete problem. You can solve this problem by using efficient approximation algorithms.

Chips now being designed to contain several processing cores to perform more computations per second. To elicit the best performance need to design algorithms with parallism in mind. 

#### Exercises

**1.1-1 Describe your own real-world example that requires sorting. Describe one that requires finding the shortest distance between two points.**

Sorting: Sorting post for different postman routes

Shortest distance: Finding a driving route from point A -> B

**1.1-2 Other than speed, what other measures of efficiency might you need to consider in a real-world setting?**

You might also need to consider space efficiency.

**1.1-3 Select a data structure that you have seen, and discuss its strengths and limitations.**

Dictionary

Strengths: Look up speeds in dictionaries are extremely quick through the use of hash tables. 

Weaknesses: dictionaries are unorded (at least in Python), they take up a lot more space than other data structures 

**1.1-4 How are the shortest-path and traveling-salesperson problems given above similar? How are they different?**

Shortest path problem: problem of finding a path between two points such that the distance between them is minimised.

Travelling salesperson problem: Given a list of cities and distances between them find the shortest path that visits all  cities once and returns to the origin city.

Similarities: They both aim to minimise distance

Differences: The shortest path problem looks for shortest distance between two points vs. multiple points for the TSP; TSP requires returning to the origin node; TSP is NP-complete.

**1.1-5 Suggest a real-world problem in which only the best solution will do. Then come up with one in which "approximately" the best solution is good enough.**

Crytograpohy problems e.g. digital signatures are problems where only the best solution will do, there is no room for error.

Approximately the best solution is generally fine for routing problems, a few percentage points additional distance from optimal is unlikely to be a big problem.

**1.1-6 Describe a real-world problem in which sometimes the entire input is available before you need to solve the problem, but other times the input is not entirely available in advance and arrives over time.**

In medical diagnoses sometimes you will have the results of all diagnostic tests, whereas in other scenarios this information might arrive over time.

#### 1.2 Algorithms as a technology

**Efficiency** 

Insertion sort takes $cn^2$ time to sort where c is a constant. Merge sort takes $cn\lg n$ time to sort so will be much quicker to run for larger n.

**Algorithms and other technologies**

"The example above shows that you should consider algorithms, like computer hardware, as a technology. Total system performance depends on choosing efficient algorithms as much as on choosing fast hardware."

Advancements in algorithm design can improve performance of systems.

"Machine learning can be thought of as a method for performing algorithmic tasks without explicitly designing an algorithm, but instead inferring patterns from data and thereby automatically learning a solution. At ûrst glance, machine learning, which automates the process of algorithmic design, may seem to make learning about algorithms obsolete. The opposite is true, however. Machine learning is itself a collection of algorithms, just under a different name."

ML is a different paradigm for algorithm design - you have a set of algorithms to choose from which themselves define new algorithms, working at a meta level.

#### Exercises

**1.2-1 Give an example of an application that requires algorithmic content at the application level, and discuss the function of the algorithms involved.**

Any search app requires algorithmic content at the application level. The function of the algorithm is to take the user input and provide an ordered list of the most relevant documents.

**1.2-2 Suppose that for inputs of size n on a particular computer, insertion sort runs in $8n^2$ steps and merge sort runs in 64 n lg n steps. For which values of n does insertion sort beat merge sort?**

Insertion sort beats merge sort when: 

$$
8n^2 < 64n\lg n
$$
$$n/8 < \lg n$$
$$1/8 < \frac{\lg n}{n}$$

**1.2-3 What is the smallest value of n such that an algorithm whose running time is $100n^2$ runs faster than an algorithm whose running time is $2^n$ on the same machine?**

To compare the running times of the two algorithms, we can set the expressions equal to each other and solve for n:

$$100n^2 = 2^n$$

$$\log{100n^2} = \log{2^n}$$

$$2\log{n} + \log{100} = n\log{2}$$

$$n\log{2} - 2\log{n} - \log{100} = 0$$

#### Problems

**1-1 Comparison of running times**

For each function f(n) and time t in the following table, determine the largest size n of a problem that can be solved in time t, assuming that the algorithm to solve the problem takes f(n) microseconds.

| |1s|1m|1h|1d|1 month| 1y | 1century|
| --- | --- | --- | --- | --- | --- | --- | --- |
| $\log n$ | $\exp(1\times1e6)$ | $\exp(60\times1e6)$ | $\exp(3600\times1e6)$ | $\exp(86400\times1e6)$ | $\exp(2.59e6\times1e6)$ | $\exp(3.15e7\times1e6)$ | $\exp(3.15e9\times1e6)$ |
| $\sqrt n$| 1e12 | 3.6e15 | 1.3e19 | 7.5e21 | 6.7e24 | 10e26 | 10e30 |
| $n$ | 1e6 | 6e7 | 3.6e9 | 8.64e10 | 2.59e12 | 3.15e13 | 3.15e15 |
| $n \log n$ | 1.89e5 | 8.7e6 | 4.2e8 | 8.7e9 | 2.3e11 | 2.5e12 | 2.2e14 |
| $n^2$ | 1e3 | 7.8e3 | 6e4 | 2.9e5 | 1.6e6 | 5.6e6 | 5.6e7 |
| $n^3$ | 1e2 | 3.9e2 | 1.5e3 | 4.4e3 | 1.4e4 | 3.2e4 | 1.5e5 |
| $2^n$ | 19 | 25 | 31 | 36 | 41 | 44 | 51 |
| $n!$ | 9 | 11 | 12 | 13 | 15 | 16 | 17 |
