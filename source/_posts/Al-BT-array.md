---
date: '2020/2/9 22:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Binary Tree - Array Implementation
---

Binary Tree implemented by Array

<!-- more -->

__How does tree looks when implemented via Array?__

* Left Child - cell[2x]
* Right Child - cell[2x+1]
* cell[0] = null 

<br>

__Creation of Binary tree__

```
createBinaryTree()
  create a blank array of 'size'
  update lastUsedIndex to 0
```
<br>

* Time Complexity : O(1)
* Space Complextiy : O(n)

<br>

__Insertion of node__

* Insertion
  * If array is full, return error message
  * Insert at first vacant cell in Array

<br>

```
insertValueInBinaryTree()
  if Tree is full
    return error message
  else
    insert value in first unused cell of array
    update lastUsedIndex
```

<br>

* Time Complexity : O(1)
* Space Complextiy : O(1)

<br>


__Search a node__

* Search
  * When the value to be searched does not exists in the tree
  * When the value to be searched exists in the tree

<br>

```
searchValueInBinaryTree()
  traverse the entire array from 1 to lastUsedIndex
  if value is found
    return success message
  return error message
```

<br>

* Time Complexity : O(n)
* Space Complextiy : O(1)

<br>

__In-Order Traversal__


```
InorderTraversal(index)
  if index > lastUsedIndex
      return
  else
    InorderTraversal(index*2)
    print current index.value
    InorderTraversal(index*2 + 1)
```

<br>

* Time Complexity : O(n)
* Space Complextiy : O(n) ---- stack에 쌓이기 때문에

<br>

__Levle-Order Traversal__


```
levelOrderTraversal()
  loop: 1 to lastUsedIndex
    print current index.value
```

<br>

* Time Complexity : O(n)
* Space Complextiy : O(1) 

<br>

__Deletion of Node__

* Deletion
  * When the value to be deleted is not existing in the tree
  * When the value to be deleted is exists in the tree

```
deleteNodeFromBinaryTree()
  search for desired value in array
    if value found
      replace this cell's value with last cell and update lastUsedIndex
  return error message
```

<br>

* Time Complexity : O(n)
* Space Complextiy : O(1) 

<br>

__Delete Binary Tree__


```
deleteBinaryTree()
  set array as null
```

<br>

* Time Complexity : O(1)
* Space Complextiy : O(1) 

<br>
