---
date: '2020/2/14 22:16:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Binary Heap
---

Binary Heap theory 

<!-- more -->

<br>

__What is Binary Heap__

* Definition : Binary Heap is a Binary Tree with some special properties.
  <br>

  1. Heap property

    * Value of any given node must be <= value of its children(Min-Heap)
    * Value of any given node must be >= value of its children(Max-Heap)
  <br>
  2. Complete tree

    * All levels are completely filled except possibly the last level and the last level has all keys as left as possible.
    * This makes Binary Heap ideal candidate for Array Implementation.

<Br>

__Why should we learn Binary Heap?__

There are cases when we want to find 'min/max' number among set of numbers in log(n) time. Also, we want to make sure that Inserting additional numbers does not take more than O(log n) time.

<br>

* Possible Solutions:
 
  1. Store the numbers in sorted Array <- Take O(n) time complexity
  2. Store the numbers in Linked List in sorted manner <- Take O(n) time complexity

<br>
Binary Heap will solve this problem with O(log n).

<br>

__Types of Binary Heap__

1. Min-Heap : If the value of each node is less than or equal to value of both of its children.
2. Max-Heap : If the value of each node is more than or equal to value of both of its children.


<br>

__Practical Use__
1. Prim's Algorithm
2. Heap Sort
3. Priority Queue


<br><br>

#### Binary Heap - Array Representaion

* Implementation options
  * Array based Implementation
  * Reference/Pointer based Implementation

<br>

__Insertion in Heap__

```
insertValueInHeap(value)
  if tree does not exists
    return error message
  else
    insert 'value' in first unused cell of Array
    sizeOfHeap++
    heapifyBottomToTop(sizeOfHeap)  ----- O(log n) : this means the height of the tree, the recursive call will step every node until it reaches the number which is smaller(Min-Heap) than its children
```

<Br>

* Time Complexity - O(log n)
* Space Complexity - O(log n) 

<br>


__ExtractMin from Heap__

```
extractMin()
  if tree does not exist
    return error message
  else
    extract 1st cell of Array
    promote last element to first
    sizeOfHeap--
    heapifyTopToBottom(1)
```

<Br>

* Time Complexity - O(log n)
* Space Complexity - O(log n) 

<br>

__Delete Heap__

<br>

```
deleteHeap()
  set array to null
```

<br>

* Time Complexity - O(1)
* Space Complexity - O(1) 




<br>

__Reason why we don't use Reference implementation(linked list) on Binary Heap__

* When we try to extract min/max number from the tree using reference, we need to loop all over the tree to find the value. This procedure takes O(n) time complexity. Inefficient!!

<Br><Br>

출처 : "Data Structures & Algorithms" by DS GUY

