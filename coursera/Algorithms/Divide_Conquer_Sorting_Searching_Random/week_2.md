# Week 2 Notes

## O(n log n) Algorithm for Counting Inversions of Arrays

The divide and conquer Paradigm 

1. Divide into smaller subproblems
2. Conquer via recursive calls
  - Sometimes requires cleanup work 
3. Combine solutions of sub problems into one for the original problem
  - Usually where most of the ingenuity occurs 

### Problem 

INPUT: Array A containing the numbers 1,2,3, ... in some arbitrary order

OUTPUT: Number of inversions = number of pairs (i,j) of array indices with i < j
and A[i] > A[j].

### Examples and Motivation 

Array: [1,3,5,2,4,6]

Inversions: (3,2), (5,2), (5,4)

Motivation: numerical similarity measure between two ranked lists. 
(e.g. for 'collaborative filtering') 

In general the largest-possible number of inversions an array of n elements can
have is (n(n-1))/2.

### Hight-Level Approach

BRUTE-FORCE: O(n2) time

Key Idea #1: Divide and Conquer.
Cann an inversion (i,j) [with i<j]:
_left_: if i,j <= n/2 
_right_: if i,j > n/2
_split_: if i <= n/2 < j

Note: left and right splits can be computed recursively. The split inversions
need a separate subroutine.

### High-Level Algorithm 

```
Count (array A, length n)
  if n=1 return 0
  else
    x = Count (1st half of A, n/2)
    y = Count (2nd half of A, n/2)
    z = CountSplitInv (A,n) 
  return x+y+z
```
Goal: implement CountSplitInv in linear (O(n)) time
then Count will run in O(n logn) time [just like merge sort]

### Piggybacking on Merge Sort

Key Idea #2: have recursive calls both count inversions and sort.
[i.e., piggyback on merge sort]

Motivation: merge subroutine naturally uncovers split inversions.

### General Claim

Claim: 
the split inversions involving an element y of the 2nd array C are
precisely the number left in the 1st array B when y is copied to the output D.

Proof:
let x be an element of the 1st array B. 
1. if x is copied to output D before y, then x < y, therefore no inversion
involving x & y.
2. if y copied to output D before x, then y < x, therefore x&y are a split
inversion.

### Merge and Count Split Inv

while merging the two sorted subarrays, keep a running total of the number of
split inversions. 
when element of 2nd array C gets copied to output D, increment total by number
of elements remaining in 1st array B. 

Run time of subroutine: O(n) + O(n) = O(n)
Sort and count runs in O(n logn) time - just like merge sort. 
  

## O(n log n) Algorithm for Closet Pair

Input: a set of P ={p1, ...pn} of n points in the plane (R^2)

Notation: d(pi,pj) = Euclidean Distance
So if p_i = (x_i, y_i) and p_j = (x_j, y_j)
d(p_i,p_j) = sqroot((x_i-x_j)^2)+(y_i-y_j)^2))

Output: A pair of points

Assumption: All points have distinct x and y coordinates
 - Brute-Force search: takes O(n^2) time

1-Dimension Solution:
1. Sort points (O(n log_n) time)
2. return closest pair of adjacent points (O(n) time)

### High-Level Approach

1. make copies of points sorted
 - by x-coordinate (P_x) 
 - by Y-coordinate (P_y)
 [O(n log_n) time]

2. Use Divide & Conquer 

### ClosestPair(P_x,P_y)

1. let Q =left half of P, R = right half of P
   form Q_x,Q_y,R_x,R_y [takes O(n) time]
2. (p1,q1) = ClosestPair(Q_x,Q_y)
3. (p2,q2) = ClosestPair(R_x,R_y)
4. (p3,q3) = ClosestSplitPair(Px,Py)
5. Return best of (p1,q1),(p2,q2),(p3,q3)

KEY IDEA: Only need to bother computing the closest split pair in 'unlucky case'
where it's distance is less than d(P1,Q1) and d(P2,Q2) 

#### UPDATED VERSION 

1. let Q =left half of P, R = right half of P
   form Q_x,Q_y,R_x,R_y [takes O(n) time]
2. (p1,q1) = ClosestPair(Q_x,Q_y)
3. (p2,q2) = ClosestPair(R_x,R_y)
4. let D = min {d(p1,q1, d(p2,q2)}
5. (p3,q3) = ClosestSplitPair(Px,Py,D)
6. return best of (p1,q1),(p2,q2),(p3,q3)

### ClosestSplitPair(Px,Py,D)

let X = biggest x - coordinate in the left of P [O(1)time]
let Sy = points of P within x-coordinate in [x-S,x+S], sorted by y-coordinate
 - [O(n) time]
Initialize best = D, best pair = null
For i = 1 to |Sy| - 7
  For j = 1 to 7
    let p,q = ith, (i+j)th points of Sy
    If d(p,q) < best
      best = (p,q), best pair = d(p,q)


## The Master Method

MOTIVATION: potentially useful algorithmic ideas often need more mathematical
analysis to evaluate 

RECALL: grade-school multiplication algorithm uses O(n^2) operation to multiply
two n-digit numbers

### A Recursive Algorithm 

Recursive Approach: 
Write x = 10^(n/2) a+b    y = 10^(n/2)c+d 
[where a,b,c,d are n/2 - digit numbers]

So: 
  x*y = 10^n*ac + 10^(n/2)(ad+bc) + bd 

Algorithm #1: recursively compute ac,ad,bc,bd then computer (*) in the obvious
way

T(n) = max number of operations this algorithm needs to multiply two n-digit
numbers

Recurrence: express T(n) in terms of running time of recursive calls
Base Case: T(1) <= a constant 
For all n > 1: T(n) <= 4T(n/2) + O(n) 

### A Better Recursive Algorithm

GAUSS: recursively compute ac,bd,(a+b)(c+d)
[recall ad+bc = (3) -(1)-(2)]

Base Case: T(1) <= a constant 
For all n > 1: T(n) <= 3T(n/2) + O(n)

### Formal Statement 

A black box for solving recurrences.

Assumption: all sub problems have equal size

Recurrence Format: 
1. Base case: T(n) <= a constant for all sufficiently small n.
2. For all larger n: T(n) <= aT(n/b) + O(n^d)
   where a = number of recursive calls (>= 1)
   b = input size shrinkage factor (>1)
   d = exponent in running time of "combine step" (>=0)
  [a,b,d independent of n] 

### Formulation of Theorum 

If T(n) <= aT(n/b) + O(n^d) 

then 

T(n) = { 
case 1: if a = b^d 
  then O(n^d log n)
case 2: if a < b^d
  then O(n^d)
case 3: if a > b^d 
  then O(n^(log_b a)) 
}

### Examples 

MERGE SORT: 
a = number of recursive calls = 2
b = input size shrinkage factor = 2
c = exponent in running time of combine step = 1

2^1 = 2, therefore case 1

O(n log n)

STRASSEN'S MATRIX MULTIPLICATION: 
a = number of recursive calls = 7
b = input size shrinkage factor = 2
d = exponent in running time of combine step = 2

7 > 2^2, therefore case 3 
O(n^(log_b a)) 

### Master Method Proof 

a = branches of recursive calls  

a^j = # of level-j sub problems 
[n/(b^j)] = size of each level-j sub problem 

<= a^j * c * [n/(b^j)]^d = cn^d * [a/(b^d)]^j 

a = rate of sub problem proliferation 
b^d = rate of work shrinkage (per sub problem) 

Either: 
Case 1: The rate of sub problem proliferation is the same as the rate of work
shrinkage
Case 2: The rate of sub problem proliferation is less than the rate of work
shrinkage 
Case 3: The rate of sub problem proliferation is greater than the rate of work
shrinkage 


### Proof P2

Basic Sums Fact
For r != 1, we have 
  1 + r + r^2 + r^3 + ..... r^k = (r^(k+1) - 1)/(r - 1 )

Upshot:
1. if r < 1 is constant, <= 1/(1-r) = a constant 
  [ 1st term of sum dominates ]
2. if r > 1 is constant, RWS is <= r^k * (1 + (1/(r-1)))  
  [ Last term of sum dominates ]

Case 2: 

If a < b^d [ RSP < RWS ] = O(n^d)
 [ Total work dominated by top level ]

Case 3: 

If a > b^d [ RSP > RWS ]
(*) = O(n^d * ((a/(b^d))


a^(log_b n) = the number of leaves of the recursion tree

a^(log_b n) == n^(log_b a) 

