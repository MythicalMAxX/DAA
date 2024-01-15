## Divide and Conquer
The general steps of the "Divide and Conquer" strategy are as follows:

**Divide:** Break the problem into smaller, more manageable subproblems. This step typically involves dividing the input data or problem into two or more smaller instances.

**Conquer:** Solve each subproblem recursively. If the subproblems are small enough, solve them directly.

**Combine:** Combine the solutions of the subproblems to get the solution to the original problem. This step is often crucial for the efficiency of the algorithm.

Several well-known algorithms in computer science follow the "Divide and Conquer" paradigm. Here are some examples:

**Merge Sort:** Divides the array into two halves, recursively sorts each half, and then merges them to achieve the final sorted array.

**Quick Sort:** Chooses a pivot element, partitions the array into elements less than the pivot and elements greater than the pivot, and recursively applies the process to each partition.

**Binary Search:** Divides a sorted array into two halves and searches for an element in one of the halves, reducing the search space in each step.

## Matrix Multiplication:
The "Divide and Conquer" strategy is not limited to sorting algorithms; it is a versatile approach used in various areas of computer science and mathematics. Its efficiency often relies on the ability to break down a problem into smaller, independent parts.

**Divide:** Split the matrices A, B, and C into four equal-sized submatrices. For matrices A and B, this involves dividing them into four quadrants. For matrix C, it involves creating four empty quadrants.

```
A = | A11  A12 |    B = | B11  B12 |    C = | C11  C12 |
    | A21  A22 |        | B21  B22 |        | C21  C22 |
```
**Conquer:** Recursively compute the product of the submatrices. This involves multiplying the corresponding submatrices and summing the results. The product matrices are stored in the submatrices of C.

```
C11 = A11 * B11 + A12 * B21
C12 = A11 * B12 + A12 * B22
C21 = A21 * B11 + A22 * B21
C22 = A21 * B12 + A22 * B22
```
**Combine:** Assemble the submatrices C11, C12, C21, and C22 into the final matrix C.

```
C = | C11  C12 |
    | C21  C22 |
```
This "Divide and Conquer" approach reduces the number of scalar multiplications compared to the standard algorithm. The time complexity of the divide-and-conquer matrix multiplication algorithm is approximately O(n^2.81), which is an improvement over the straightforward cubic algorithm.

### Here's a simplified pseudocode for "Divide and Conquer" matrix multiplication:

```
function matrixMultiply(A, B):
    n = size of matrices A, B
    if n == 1:
        return A * B  // Base case

    // Divide
    partition A, B, and C into submatrices
    A11, A12, A21, A22 = partitions of A
    B11, B12, B21, B22 = partitions of B
    C11, C12, C21, C22 = partitions of C

    // Conquer
    P1 = matrixMultiply(A11, B11)
    P2 = matrixMultiply(A12, B21)
    P3 = matrixMultiply(A11, B12)
    P4 = matrixMultiply(A12, B22)
    P5 = matrixMultiply(A21, B11)
    P6 = matrixMultiply(A22, B21)
    P7 = matrixMultiply(A21, B12)
    P8 = matrixMultiply(A22, B22)

    // Combine
    C11 = P1 + P2
    C12 = P3 + P4
    C21 = P5 + P6
    C22 = P7 + P8

    return C
```
This algorithm can be optimized further using techniques such as Strassen's algorithm for matrix multiplication, which has a time complexity of approximately O(n^2.81).


## Convex Hull

![](https://upload.wikimedia.org/wikipedia/commons/9/9a/Animation_depicting_the_Monotone_algorithm.gif)

### Choose the Pivot Point:

Find the point with the lowest y-coordinate (and the leftmost point in case of ties) as the pivot point. This point is guaranteed to be on the convex hull.
### Sort Points by Polar Angle:

Sort the remaining points based on their polar angles with respect to the pivot point. If two points have the same polar angle, the one closer to the pivot comes first.
### Build the Convex Hull:

Process each point in the sorted order. For each point, check if it makes a left or right turn with the two previously processed points.
If it makes a left turn, include it in the convex hull. If it makes a right turn, remove the last point from the convex hull and repeat the check until a left turn is encountered.
### Convex Hull is Complete:

After processing all points, the convex hull is complete.
The time complexity of Graham's Scan is typically O(n log n), where n is the number of points.

### Here's a simple pseudocode representation of the Graham's Scan algorithm:

```
function grahamScan(points):
    pivot = point with the lowest y-coordinate (and leftmost in case of ties)
    sort points by polar angle with respect to pivot

    stack = empty stack
    push pivot and the first two points to stack

    for i = 3 to n:
        while the last two points and points[i] make a non-left turn:
            pop the last point from stack
        push points[i] to stack

    return stack
```
The resulting stack contains the vertices of the convex hull in counterclockwise order.
