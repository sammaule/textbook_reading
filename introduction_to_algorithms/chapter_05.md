
# Probabilistic Analysis and Randomised Algorithms

#### 5.1 The hiring problem

Example - need a new office assistant decide to interview replacements and hire if that candidate is better qualified than the current assistant.

```
HIRE-ASSISTANT(n)

1 best = 0
2 for i = 1 to n
3    interview candidate i
4    if candidate i better than candidate best
5        best = i
6        hire candidate i
```

Probabilisitic analysis - can be done if we know or make assumptions about the distribution of the inputs. When reporting running times in this way they are referred to as the average-case running time.

We call an algorithm randomised if its behaviour is determined by values produced by a random-number generator.

#### 5.2 Indicator random variables

Indicator random variables associated with event A take value 1 if A occurs and 0 otherwise.

Lemma 5.1 E(A) = Pr(A), pretty straightforward stuff. 

**Analysis of the hiring problem using indicator random variables**

Assume the candidates arrive in a random order.

$X_i = I\{\text{candidate } i \text{ is hired}\}$ 

Lemma 5.1 gives 

$E[X_i] = Pr\{\text{candidate } i \text{ is hired}\}$ 

Each candidate is equally likely to have been the best so far so candidate i will have probability 1/i of being the best so far. We can then compute E[X] as

![[Pasted image 20230124140127.png]]

Assuming that candidates are presented in a random order the average case total hiring cost is O(c ln n) where c is the cost of hiring a new member of staff.

#### 5.3 Randomized algorithms

Many randomized algorithms randomize the input by permuting a given input array. The goal is to produce a uniform random permutation.
