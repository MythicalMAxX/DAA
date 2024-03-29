# Sorting Algorithm
## Time Complexity:
```
Algorithm         | Time Complexity      | Space Complexity | Stability | In-Place |
-------------------|----------------------|------------------|-----------|----------|
Insertion Sort     | O(n^2)               | O(1)             | Yes       | Yes      |
Selection Sort     | O(n^2)               | O(1)             | No        | Yes      |
Bubble Sort        | O(n^2)               | O(1)             | Yes       | Yes      |
Merge Sort         | O(n log n)           | O(n)             | Yes       | No       |
Quick Sort         | O(n^2) (worst case)  | O(log n)         | No        | Yes      |
Heap Sort          | O(n log n)           | O(1)             | No        | Yes      |
Radix Sort         | O(kn) (k is the      | O(k+n)           | Yes       | Yes      |
                   | number of digits)    |                  |           |          |
Bucket Sort        | O(n^2) (worst case)  | O(n)             | Yes       | Yes      |
Counting Sort      | O(n+k) (k is the     | O(k)             | Yes       | Yes      |
                   | range of input)      |                  |           |          |
```
## Classification:
```
Category            | Algorithms                   |
---------------------|------------------------------|
Simple Sorting      | Insertion Sort, Selection Sort, Bubble Sort, Counting Sort |
Efficient Sorting   | Merge Sort, Quick Sort, Heap Sort |
Distribution Sorting | Radix Sort, Bucket Sort       |

```
## Insertion Sort
### Concept:
Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It's much like sorting a hand of playing cards.

![](https://upload.wikimedia.org/wikipedia/commons/9/9c/Insertion-sort-example.gif)

### Explanation:
Imagine you have a deck of cards, and they're all mixed up. Insertion Sort works by taking one card at a time and placing it in its correct position in the sorted part of the deck.

## Here's how it works step by step:

### Start with the second card: 
Assume the first card is already sorted because a single card is always sorted. So, start with the second card.

### Compare and insert:
Compare the second card with the first. If it's smaller, swap them. Now, the first two cards are in sorted order.

Extend the sorted part: Take the third card and compare it with the second, then with the first. Insert it into the correct position in the sorted part of the deck.

### Repeat: 
Keep doing this for every card until the entire deck is sorted.

### Example:
Let's say you have these numbers: 5, 2, 9, 1, 5, 6

Start with 2 (assuming 5 is already sorted): [2, 5, 9, 1, 5, 6]
Move to 9, insert it in the correct position: [2, 5, 9, 1, 5, 6]
Move to 1, insert it: [1, 2, 5, 9, 5, 6]
Move to 5, insert it: [1, 2, 5, 5, 9, 6]
Move to 6, insert it: [1, 2, 5, 5, 6, 9]
Real-life analogy:
Think of Insertion Sort like arranging books on a shelf. You take one book at a time and place it in the correct spot on the shelf to make sure all the books are in order.

### Algorithm:
Here's a simple version of the Insertion Sort algorithm in pseudocode:

```
for i = 1 to n-1
    key = arr[i]
    j = i - 1

    while j >= 0 and arr[j] > key
        arr[j + 1] = arr[j]
        j = j - 1

    arr[j + 1] = key
```
This algorithm iterates through the array, comparing and shifting elements until the entire array is sorted.


## Selection Sort
### Concept:
Selection Sort is another simple sorting algorithm that works by dividing the array into a sorted and an unsorted region. In each iteration, it selects the smallest (or largest, depending on the order) element from the unsorted region and swaps it with the first unsorted element.

![](https://upload.wikimedia.org/wikipedia/commons/3/3e/Sorting_selection_sort_anim.gif)

### Explanation:
Imagine you have a list of numbers, and you want to sort them in ascending order. Selection Sort works like finding the smallest number and placing it at the beginning, then finding the next smallest and placing it in the second position, and so on.

### Here's how it works step by step:

**Find the minimum:** Go through the unsorted part of the list and find the smallest element.

**Swap:** Swap the smallest element with the first element of the unsorted part.

**Extend the sorted part:** The first element is now in its correct place. Consider it part of the sorted region and move to the next unsorted element.

**Repeat:** Keep doing this until the entire list is sorted.

### Example:
Let's say you have these numbers: 5, 2, 9, 1, 5, 6

Find the smallest (1) and swap with the first element: [1, 2, 9, 5, 6, 5]
Now, the first element is sorted. Move to the next unsorted element (2).
Find the smallest (2) in the remaining list and swap with the second element: [1, 2, 9, 5, 6, 5]
Repeat this process until the entire list is sorted.
### Real-life analogy:
Think of Selection Sort like arranging students by height in a line. You find the shortest student and place them at the beginning, then find the next shortest and place them next to the first, and so on.

### Algorithm:
Here's a simple version of the Selection Sort algorithm in pseudocode:

```
for i = 0 to n-1
    minIndex = i

    for j = i+1 to n
        if arr[j] < arr[minIndex]
            minIndex = j

    swap arr[i] with arr[minIndex]
```
This algorithm iterates through the array, finding the smallest element in the unsorted part and swapping it with the first unsorted element.


## Bubble Sort
### Concept:
Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

![](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)

### Explanation:
Imagine you have a list of numbers, and you want to sort them in ascending order using Bubble Sort. The algorithm compares pairs of adjacent elements and swaps them if they are in the wrong order. This process is repeated until the entire list is sorted.

Here's how it works step by step:

**First Pass:** Compare the first two elements. If they are in the wrong order, swap them. Move to the next pair of elements, and so on, until the end of the list. The largest element will "bubble up" to the end of the list.

**Second Pass:** Repeat the process, but ignore the last (already sorted) element. The second-largest element will now be in its correct position.

**Repeat:** Continue this process, each time ignoring one more element from the end, until the entire list is sorted.

### Example:
Let's say you have these numbers: 5, 2, 9, 1, 5, 6

**First Pass:** [2, 5, 1, 5, 6, 9] (largest element moved to the end)
**Second Pass:** [2, 1, 5, 5, 6, 9] (second-largest element in its correct position)
**Third Pass:** [1, 2, 5, 5, 6, 9] (entire list is sorted)
### Real-life analogy:
Think of Bubble Sort like sorting a line of people based on their heights. Taller people (larger elements) move towards the end of the line with each pass until the entire line is sorted.

### Algorithm:
Here's a simple version of the Bubble Sort algorithm in pseudocode:

```
for i = 0 to n-1
    for j = 0 to n-i-1
        if arr[j] > arr[j+1]
            swap arr[j] with arr[j+1]
```
This algorithm iterates through the array, comparing adjacent elements and swapping them if they are in the wrong order, "bubbling" the larger elements towards the end of the array.


## Merge Sort
### Concept:
Merge Sort can be thought of as breaking a big problem into smaller subproblems, solving each subproblem individually, and then combining the solutions to get the final result.

![](https://miro.medium.com/v2/format:webp/0*K7cD17vfL7FdTTLK.gif)

### Explanation:

**Divide:** Split the unsorted array into two halves.
**Conquer:** Recursively sort each half.
**Combine:** Merge the two sorted halves back together.
### Here's a visual explanation:

Consider the array [38, 27, 43, 3, 9, 82, 10]. We'll break it down step by step.

**Divide:** Split the array into two halves: [38, 27, 43] and [3, 9, 82, 10].

```
[38, 27, 43]   [3, 9, 82, 10]
```
**Conquer:** Recursively sort each half.

Sort the left half: [27, 38, 43]
Sort the right half: [3, 9, 10, 82]
**Combine:** Merge the two sorted halves.

```
[27, 38, 43]   [3, 9, 10, 82]
     \               /
      \             /
       \           /
        \         /
         \       /
          \     /
           \   /
            \ /
[3, 9, 10, 27, 38, 43, 82]
```
### Real-life analogy:
Think of Merge Sort like organizing a bookshelf. Divide the books into two piles, sort each pile separately, and then merge them back together in a sorted order.

### Algorithm:
Here's a simplified version of the Merge Sort algorithm in pseudocode:

```
mergeSort(arr):
    if length of arr > 1
        mid = length of arr / 2
        leftHalf = arr[0...mid-1]
        rightHalf = arr[mid...end]

        mergeSort(leftHalf)
        mergeSort(rightHalf)

        merge(arr, leftHalf, rightHalf)

merge(arr, left, right):
    i = j = k = 0

    while i < length of left and j < length of right
        if left[i] <= right[j]
            arr[k] = left[i]
            i = i + 1
        else
            arr[k] = right[j]
            j = j + 1
        k = k + 1

    // Copy the remaining elements of left and right, if any
    while i < length of left
        arr[k] = left[i]
        i = i + 1
        k = k + 1

    while j < length of right
        arr[k] = right[j]
        j = j + 1
        k = k + 1
```
This algorithm ensures that the smaller parts of the array are sorted first, and then these sorted parts are combined to form a fully sorted array.


## Heap Sort
### Concept:
Build a max heap from the unsorted array.
Swap the root (maximum element) with the last element and reduce the size of the heap.
Heapify the root to maintain the max heap property.
Repeat steps 2-3 until the heap size becomes 1.

![](https://upload.wikimedia.org/wikipedia/commons/f/fe/Heap_sort_example.gif)

### Visual Explanation:
Consider the array [12, 11, 13, 5, 6, 7] as an example.

### Build Max Heap:

```
Initial array: [12, 11, 13, 5, 6, 7]

             12
           /    \
         11      13
       /    \    /
      5      6  7
```
### Swap and Heapify:

Swap the root (12) with the last element (7) and heapify the root.

```
After swap: [7, 11, 13, 5, 6, 12]

             7
           /    \
         11      13
       /    \    /
      5      6  12
```
### Repeat:

Repeat the process until the heap size becomes 1.

```
After swapping and heapifying: [6, 11, 13, 5, 7, 12]
             6
           /    \
         11      13
       /    \    /
      5      7  12
```
```
After swapping and heapifying: [5, 11, 13, 6, 7, 12]
             5
           /    \
         11      13
       /    \    /
      6      7  12
```
```
After swapping and heapifying: [5, 6, 13, 11, 7, 12]
             5
           /    \
         6      13
       /    \    /
      11     7  12
```
```
After swapping and heapifying: [5, 6, 12, 11, 7, 13]
             5
           /    \
         6      12
       /    \    /
      11     7  13
```
### Sorted Array:
The array is now sorted: [5, 6, 7, 11, 12, 13]

### Real-life analogy:
Think of a max heap as a line of people, where each person is taller than their children. Heap Sort is like arranging the line from the tallest person to the shortest.

### Algorithm:
Here's a simplified version of the Heap Sort algorithm in pseudocode:

```
heapSort(arr):
    buildMaxHeap(arr)
    
    for i = length of arr - 1 to 1
        swap arr[0] with arr[i]
        heapify(arr, 0, i)

buildMaxHeap(arr):
    n = length of arr
    
    for i = n/2 - 1 to 0
        heapify(arr, i, n)

heapify(arr, i, n):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2

    if left < n and arr[left] > arr[largest]
        largest = left

    if right < n and arr[right] > arr[largest]
        largest = right

    if largest != i
        swap arr[i] with arr[largest]
        heapify(arr, largest, n)
```
This algorithm ensures that the largest element is always at the root of the heap, allowing us to efficiently extract the maximum element and build a sorted array.


## Quick Sort
### Concept:
**Select a Pivot:** Choose an element from the array to act as a pivot.
**Partitioning:** Rearrange the array so that elements less than the pivot are on the left, and elements greater than the pivot are on the right.
**Recursion:** Apply Quick Sort recursively to the left and right sub-arrays.
**Combine:** The sorted sub-arrays are combined to get the final sorted array.

![](https://upload.wikimedia.org/wikipedia/commons/9/9c/Quicksort-example.gif)

### Visual Explanation:
Consider the array [38, 27, 43, 3, 9, 82, 10] as an example.

### Select a Pivot:
Let's choose the last element, 10, as the pivot.

### Partitioning:
Rearrange the array so that elements less than 10 are on the left, and elements greater than 10 are on the right.

```
[9, 3, 10, 27, 43, 82, 38]
```
### Recursion:
Apply Quick Sort recursively to the left and right sub-arrays.

```
[3, 9, 10, 27, 43, 82, 38]
         ^ Pivot
```
```
[3, 9, 10, 27, 43, 82, 38]
                     ^ Pivot
```
Continue this process until each sub-array is sorted.

### Combine:
The final sorted array is obtained by combining the sorted sub-arrays.

```
[3, 9, 10, 27, 38, 43, 82]
```
### Real-life analogy:
Think of Quick Sort like organizing a deck of cards. You choose a card (pivot), arrange the cards less than it to the left and those greater to the right. Repeat this process for the smaller groups until the entire deck is sorted.

### Algorithm:
Here's a simplified version of the Quick Sort algorithm in pseudocode:

```
quickSort(arr, low, high):
    if low < high
        pivotIndex = partition(arr, low, high)
        quickSort(arr, low, pivotIndex - 1)
        quickSort(arr, pivotIndex + 1, high)

partition(arr, low, high):
    pivot = arr[high]
    i = low - 1

    for j = low to high - 1
        if arr[j] <= pivot
            i = i + 1
            swap arr[i] with arr[j]

    swap arr[i + 1] with arr[high]
    return i + 1
```
This algorithm efficiently sorts the array in-place by selecting a pivot, partitioning the array around the pivot, and recursively applying the process to the sub-arrays.


## Radix Sort
### Concept:

**LSD Approach:** Start by sorting based on the least significant digit (rightmost) and move towards the most significant digit (leftmost).
**Bucket Sorting:** Distribute elements into buckets according to the current digit being considered.
**Combine Buckets:** Combine the buckets to get a partially sorted array.
**Repeat:** Repeat the process for each digit until the entire array is sorted.

### Visual Explanation:
**Consider an array of integers:** [170, 45, 75, 90, 802, 24, 2, 66]. We'll sort this array using Radix Sort with LSD approach.

### LSD - First Pass (Rightmost Digit):

```
Bucket 0: [170, 90, 802]
Bucket 2: [2]
Bucket 4: [24]
Bucket 5: [45]
Bucket 6: [66]
Bucket 7: [75]
Combine the buckets: [170, 90, 802, 2, 24, 45, 66, 75]
```
### LSD - Second Pass (Next Digit to the Left):

```
Bucket 0: [802, 2]
Bucket 1: [170]
Bucket 2: [24]
Bucket 4: [45]
Bucket 5: [66]
Bucket 7: [75, 90]
Combine the buckets: [802, 2, 170, 24, 45, 66, 75, 90]
```
### LSD - Third Pass (Next Digit to the Left):

```
Bucket 0: [2, 24]
Bucket 4: [45]
Bucket 5: [66]
Bucket 7: [75]
Bucket 8: [802, 170, 90]
Combine the buckets: [2, 24, 45, 66, 75, 802, 170, 90]
```
Now, the array is sorted.

### Real-life analogy:
Think of Radix Sort like organizing a set of books on a bookshelf. You start by sorting based on the rightmost digit of the page numbers, then move to the next digit, and so on.

### Algorithm:
Here's a simplified version of the Radix Sort algorithm in pseudocode:

```
radixSort(arr):
    maxDigit = getMaxDigitCount(arr)
    
    for i = 1 to maxDigit
        bucketSort(arr, i)

bucketSort(arr, digitPlace):
    create 10 buckets (0-9)

    for each number in arr
        digit = getDigit(number, digitPlace)
        place the number in the corresponding bucket

    reconstruct the array from the buckets

getDigit(num, place):
    return (num / 10^(place-1)) % 10

getMaxDigitCount(arr):
    maxDigit = 0

    for each number in arr
        maxDigit = max(maxDigit, countDigits(number))

    return maxDigit

countDigits(num):
    count = 0

    while num > 0
        num = num / 10
        count = count + 1

    return count
```
This algorithm efficiently handles the sorting of numbers by considering each digit at a time.


## Bucket Sort
### Concept:

**Divide into Buckets:** Divide the input array into a number of equally sized buckets.
**Sort each Bucket:** Sort each individual bucket. This can be done using another sorting algorithm or recursively applying Bucket Sort.
**Concatenate Buckets:** Combine the sorted buckets to get the final sorted array.

![How to Bucket Sort](https://i.makeagif.com/media/5-18-2016/a7ppGv.gif)

### Visual Explanation:
**Consider an array of numbers:** [0.42, 0.32, 0.33, 0.52, 0.37, 0.47, 0.51]. We'll sort this array using Bucket Sort.

### Divide into Buckets:

```
Bucket 0.3: [0.32, 0.33]
Bucket 0.4: [0.42, 0.37, 0.47]
Bucket 0.5: [0.52, 0.51]
```
### Sort each Bucket:

Sort each individual bucket. In this case, the buckets are already sorted, but you might use another sorting algorithm for this step.

### Concatenate Buckets:

**Combine the sorted buckets:** [0.32, 0.33, 0.37, 0.42, 0.47, 0.51, 0.52]

Now, the array is sorted.

### Real-life analogy:
Think of Bucket Sort like organizing a set of numbers by placing them into different containers (buckets), sorting each container separately, and then combining them to get a fully sorted list.

### Algorithm:
Here's a simplified version of the Bucket Sort algorithm in pseudocode:

```
bucketSort(arr):
    n = length of arr
    buckets = create empty array of n empty buckets

    for i = 1 to n
        index = n * arr[i]
        append arr[i] to the bucket at index

    for each bucket in buckets
        sort the bucket (you can use another sorting algorithm or recursively apply bucketSort)

    concatenate the sorted buckets to get the final sorted array
```
This algorithm assumes that the input is uniformly distributed over the range [0, 1). If the input range is different, you may need to adjust the indexing and bucket creation accordingly.

Certainly! Let's explore Counting Sort with a simple and fun explanation, an example, and a real-life analogy.

### Counting Sort:

**Explanation:**
Counting Sort is like organizing a set of toys based on their types. Imagine you have different types of toys like cars, teddy bears, and building blocks, and you want to arrange them neatly. Counting Sort helps us do that!

![](https://d18l82el6cdm1i.cloudfront.net/uploads/hrUDdYC7OH-countingsort.gif)

**How it works:**
1. **Counting the Toys:**
   - We start by counting how many of each type of toy we have. For example, we count how many cars, teddy bears, and building blocks we have.

2. **Organizing by Count:**
   - Once we know the counts, we can organize the toys in order. If we have 3 cars, 2 teddy bears, and 4 building blocks, we'll arrange them like this.

   ```plaintext
   Cars | Teddy Bears | Building Blocks
   ------------------------------------
   Car 1 | Bear 1       | Block 1
   Car 2 | Bear 2       | Block 2
   Car 3 |              | Block 3
   ```

   We've organized them based on their counts!

3. **Putting them Back:**
   - Finally, we put the toys back in this new order, and voilà! Our toys are sorted.

**Example:**
Let's say we have a bunch of numbers: 4, 2, 1, 4, 3, and 2. We want to sort them using Counting Sort.

1. **Count the Numbers:**
   - Count how many times each number appears.

   ```plaintext
   1: 1 time
   2: 2 times
   3: 1 time
   4: 2 times
   ```

2. **Organize by Count:**
   - Arrange the numbers based on their counts.

   ```plaintext
   1 | 2 | 3 | 4
   -------------
   1 | 2 | 1 | 2
   ```

3. **Put them Back:**
   - Put the numbers back in this new order.

   ```plaintext
   1, 2, 2, 3, 4, 4
   ```

And there you go! The numbers are now sorted.

### Algorithm
```
CountingSort(arr):
    // Step 1
    max_element = FindMaxElement(arr)
    
    // Step 2
    count = InitializeCountArray(max_element)
    
    // Step 3
    CountOccurrences(arr, count)
    
    // Step 4
    ModifyCountArray(count)
    
    // Step 5
    output = InitializeOutputArray(arr)
    
    // Step 6
    PlaceElements(arr, count, output)
    
    return output

// Helper Functions:

// Step 1: Find the maximum element in the array
FindMaxElement(arr):
    max_element = arr[0]
    for element in arr:
        if element > max_element:
            max_element = element
    return max_element

// Step 2: Initialize a count array with zeros
InitializeCountArray(max_element):
    count = array of size (max_element + 1) initialized with zeros
    return count

// Step 3: Count the occurrences of each element in the array
CountOccurrences(arr, count):
    for element in arr:
        count[element] += 1

// Step 4: Modify the count array to store cumulative count
ModifyCountArray(count):
    for i from 1 to size(count) - 1:
        count[i] += count[i - 1]

// Step 5: Initialize the output array
InitializeOutputArray(arr):
    output = array of size length(arr)

// Step 6: Place elements in their sorted position
PlaceElements(arr, count, output):
    i = length(arr) - 1
    while i >= 0:
        element = arr[i]
        count[element] -= 1
        output[count[element]] = element
        i -= 1
```

**Real-Life Analogy:**
Imagine you have a bag of candies with different colors—red, blue, and green. Counting Sort is like arranging all the red candies together, then the blue ones, and finally the green ones. It helps you quickly find and organize your favorite candies!

So, Counting Sort is like becoming a toy organizer or a candy sorter. It makes things neat and easy to find!
