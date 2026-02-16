## Introduction
* This data structure allows for *insertion* and *deletion* of data based on "priority" (using a "key" to determine the data's ranking)
* The data with the "smallest key" has the "highest priority" and will be the "first to be removed" from the queue
* Each elements in the queue includes a "key" and  "value" 
  <br>**Example** : ``[{"key", "value"}, {"key", "value"}, {"key", "value"}]``

## The Priority Queue ADT
**Note** : "ADT" or "Abstract Data Type" is _conceptual_ in programming that defines a data type and a set of operations _without actually implmented it_ (only speaks about "what it does" more than "how it does it")

### Image reference
![image.png](/Assets/operations-priority-queue.png)

## Ways to implementing a Piority Queue
1. Unsorted List (the "lazy" approach):
- **insertion is fast.** you just throw a new data at the end of the list
- **finding the minimum key is slow.** because the list is mess, the computer must scan every single item (time complexity = O(n)) to find which one has the smallest key (probably loop through a list and make a comparison)
2. Sorted List (the "organized" approach):
- **insertion is slow.** when you add a new item, you have to shift other items out of the way to maintain the sorted order (time complexity = O(n))
- **finding the minimum is fast.** since the list is organized and its already in order (smallest key to biggest key) so the smallest key will always in the very beginning (probably find the place to put the data in and make the index of all next data up by 1)

1. [Unsorted Example](/Data%20Structures/Priority%20Queues/Codes/Examples/UnsortedExample.md)
2. [Sorted Example](/Data%20Structures/Priority%20Queues/Codes/Examples/SortedExample.md)

### Image reference
![image.png](/Assets/bigo-comparison-priority-queue.png)
<sup>a comparison of Time Complexity between "unsorted" and "sorted" in implementations. finding and insertion is quite opposite</sup>

## Heaps
- This data structure allows both _insertions_ and _deletions_ in **logarithmic time** (time complexity = O(log n)) (Improved from previous stucture. Which was very fast!)
- Heap is binary tree (will be reference as **_T_** from now on) that _must_ satisfies these 2 properties
  - Heap-Order: In a heap **_T_**, for every position (will be reference as **_p_** from now on) except the root, the "key
  " at **_p_** is **greater than or equal** the "key" that stores at its parent.
  - Complete Binary Tree: A heap **_T_** with height (will be reference as **_h_** from now on) is a complete binary tree