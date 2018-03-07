# Week 1 Notes

## The Algorithm Designer's Mantra

>"Perhaps the most important principle for the good algorithm design is to
>refuse to be content" - Aho 

## Karatsuba Multiplication 

A Recursive Algorithm for multiplying large numbers 

## Merge Sort - Motivation and Example 

Merge sort is 60 years old, but still used frequently 
It's also a good intro to divide & conquer algorithms 

## The Sorting Problem

*Input:* Array of n numbers, unsorted
*Output:* Same number, sorted in increasing order

## Merge Sort: Pseudocode 

### Steps 

1. Divide array in half
2. Recursively sort 1st half of array
3. Recursively sort 2nd half of array
4. Merge the two separate arrays

### Pseudocode for Merge 

C = output array [length = n]
A = 1st sorted array [n/2]
B = 2nd sorted array [n/2]
i = 1 [counter for A]
j = 1 [counter for B]
k = 1 [counter for C]

```
for k =1 to n
  if A(i) < B(j)
    C(k) = A(i)
    i++
  else [B(j) < A(i)]
    C(k) = B(j)
    j++
end
```

## Merge Sort Running Time?

Key Question: running time of the merge sort on an array of numbers?
(running time is equivalent to the number of lines of code executed)

2 operation for initializing counters (j & k)
1 comparison per loop
1 assignment per loop
1 increment of counter per loop
1 initialization of k

*Upshot:* running time of merge on array of m numbers is <= 4m + 2
m is at least one, so really it's 6m


*Claim:* Merge sort requires <= 6n log2n + 6n operations to sort n numbers 

Recursion Tree Method: Write out all the work done by the recursive algorithm in
a tree structure with the children of a given node corresponding to the
recursive calls made by that node. The point of the structure is to facilitate
an interesting way to count the overall work done by the algorithm and to better
facilitate the analysis.

The recursion tree has roughly log2(n) levels of recursion

At each level j=0,1,2,...,log2n — there are 2^j subproblems, each of size n/2^j


## Guiding Principles of Analysis of Algorithms 

1. Use 'worst case analysis' to determine what the slowest possible completion
time for the algorithm can be, given an input of size n.
  - Other types of analysis:
    - average-case analysis: analyze the average running time of an algorithm 
      under assumptions about the relative frequencies of inputs
    - benchmark analysis: use agreed upon benchmark inputs, which represent
      practical inputs for the algorithm.
    - both require domain knowledge

2. Don't pay much attention to constant factors, lower - order terms. 
  - Justifications: 
    - Way easier
    - Constants depend on architecture/compiler/programmer
    - Lose very little predictive power

3. Asymptotic Analysis: focus on running time for *large* input sizes n. 
  - Some algorithms may be superior for smaller input sizes of n, but will
    perform worse on larger input sizes. For this course, only big input
    problems are interesting.

A fast algorithm is one where the worst-case running time grows slowly with the
input size

The holy grail of algorithms runs in linear time


## Asymptotic Analysis 

Vocabulary for the design and analysis of algorithms.

High-level idea: suppress constant factors and lower-order terms.
Lower order terms are generally irrelevant for large inputs.
Constant factors are too system dependent

Example: equate 6n log2n + 6n with just n logn
Terminology: running time is O(nlog n) where n = input size 

## Big-Oh: 

English Definition:
T(n) = O(f(n)) If eventually (for all sufficiently large n), T(n) is bounded
above by a constant multiple of f(n) 


Formal Definition: 
T(n) = O(f(n)) 
if and only if there exists constants c, n` > 0 such that T(n) <= c * f(n) for
all n >= n`
n` is the point of intersection between c * f(n) and T(n)

Warning: C & n` cannot depend on n.


## Big Omega and Theta 

Omega Notation: Greater than or equal to 

Theta Notation: Equals. 
If T(n) = theta(f(n)) then it is both O(f(n)) and ø(f(n)) 

Little-Oh Notation:
T(n) = o(f(n)) if and only if for ALL constants c>0 and there exists a constant
n` such that T(n) <= c*f(n) and  n >= n`

