---
date: '2020/2/10 23:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Binary Search Tree 
---

The theory of BST
<!-- more -->

__What is BST?__

* Binary Search Tree(BST) is a Binary Tree which all the nodes follows the below mentioned properties
  * The left sub-tree of a node has a key less than or equal to its parent node's key.
  * The right sub tree of a node has a key greater than to its parent node's key.

<br>

__Why should we learn BST?__

* Binary tree implemented by linked list has good space efficient compared to the BT implemented by Array. However, it is not good on Insertion, deletion, searching, traversing which has time complexity of O(n). BST will improve the time complexity of binary tree by O(log n).

<br><br>

__Algorithm - Creation of blank BST__

```
createBST()
  Initialize Root with null
```

<br>

* Time Complexity - O(1)
* Space Complexity - O(1)

<br>

__Algorithm - Searching a node in BST__

```
BST_Search(root, value)  ------------T(n)
  if(root is null)
    return null
  else if(root == value)
    return root
  else if(value < root)
    BST_Search(root.left, value)  ----T(n/2)
  else if(value > root)
    BST_Search(root.right, value) ----T(n/2)
```

<br>

* Time Complexity - O(log n)
* Space Complexity - O(log n) ----beacuse of recursive call

<br>

__Algorithm - Traverse in BST__

* Totally same as traversing Binary Tree

<br>


__Algorithm - Inserting a node in BST__

* Cases
  * BST is  blank
  * BST is non-blank

Using Stack on the behind of the scene.

```
BST_Insert(currentNode, valueToInsert)
  if(currentNode is null)
    create a node, insert 'valueToInsert' in it
  else if(valueToInsert <= currentNode's value)
    currentNode.left = BST_Insert(currentNode.left, valueToInsert)
  else
    currentNode.right = BST_Insert(currentNode.right, valueToInsert)
  return currentNode
```

<br>

* Time Complexity - O(log n)
* Space Complexity - O(log n) 

<br>


__Algorithm - Deleting a node in BST__

* Cases
  * Node to be deleted is leaf node
  * Node to be deleted is having 1 child
  * Node to be deleted has 2 child


Using Stack on the behind of the scene.

```
deleteNodeOfBST(root, valueToBeDeleted)  --------------------------------------T(n)
  if(root == null) return null;
  if(valueToBeDeleted < root.value)
    then root.left = deleteNodeOfBST(root.left, valueToBeDeleted)   ---------------T(n/2)
  else if(valueToBeDeleted > root.value)
    then root.right = deleteNodeOfBST(root.right, valueToBeDeleted)  ---------------T(n/2)
  else // if cuurentNode is the node to be deleted
      if root have both children, then find minimum element from right subtree(Case#3)  -------------O(log n)
          replace current node with minimum node from right subtree and delete minimum node from right
      else if node ToBeDeleted has only left child(Case#2)
            then root = root.left();
      else // if node ToBeDeleted do not have child(Case#1)
            root = null;
  return root;
```

<br>

* Time Complexity - O(log n)
* Space Complexity - O(log n) 

<br>

__Algorithm - Deleting entire tree in BST__



```
DeleteBST()
  root = null;
```

<br>

* Time Complexity - O(1)
* Space Complexity - O(1) 

<br>