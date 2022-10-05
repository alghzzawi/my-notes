# Whiteboarding + Big O

## Big O
### Big O notation is used in computer science to describe the performance or complexity of an algorithm.
### Big O specifically describes the worst case scenario, and can be used to describe the required execution time or the space used.
### One of the basics that a programmer must have is a foundation in mathematics to be able to O (N log N) or any seemingly strange syntax. I found that the best way to fully understand Big O is to produce some examples in the code. Therefore, the following describes common growth commands along with descriptions and examples where possible.

1. ## O(1)
    ### Describes an algorithm that will always be executed at the same time

2. ## O(N)
    ### O(N) describes an algorithm whose performance will grow linearly and directly with the size of the input data set. A matching string can be found during any iteration of the for loop, it will always assume the upper bound where the algorithm will perform the maximum number of iterations.

3. ## O (N²)
    ### These algorithms include nested iterations over the data set. Deeper nested iterations will result in O(N³), O(N⁴), etc.

4. ## O(2^N)
    ### These algorithms include non-overlapping iterations over the data set.

> Note: The fastest Big O algorithm is O (log n).

## Examples for each Big O

```
. Logarithmic algorithm – O(logn) – Binary Search.
. Linear algorithm – O(n) – Linear Search.
. Superlinear algorithm - O(nlogn) - Heap Sort, Merge Sort.
. Polynomial algorithm - O(n^c) - Strassen's Matrix Multiplication, Bubble Sort, Selection Sort, Insertion Sort, Bucket Sort.
. Exponential algorithm – O(c^n) – Tower of Hanoi.
. Factorial algorithm – O(n!) – Determinant Expansion by Minors, Brute force Search algorithm for Traveling Salesman Problem.
```