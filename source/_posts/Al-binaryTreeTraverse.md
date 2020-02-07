---
date: '2020/2/6 23:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Binary Tree - Traverse, Search, Insertion,(Linked List Implementation)
---

Traverse Binary Tree

<!-- more -->


### Traversing all nodes of Binary Tree(Linked List implementation)

__Depth first search__
1. PreOrder Traversal
2. InOrder Traversal
3. PostOrder Traversal

__Breadth first search__
1. LevelOrder Traversal

<br>

### * PreOrder Traversal(Using Stack)

- Root
- Left Subtree
- Right Subtree


```
preorderTraverse(root){  ----------------T(n)
  if(root equals null){
    return error message
  } else {
    print root
    preorderTraversal(root.left)  -------T(n/2)
    preorderTraversal(root.right) -------T(n/2)
  }
}
```
<br>
  
* Time Complexity - O(n)
* Space Complexity - O(n)  : Recursive call로 많은 노드가 스택에 push, pull 되기 때문에


<br>

### * In-Order Traversal(Using Stack)

- Left Subtree
- Root
- Right Subtree

```
inorderTraverse(root){  ----------------T(n)
  if(root equals null){
    return error message
  } else {
    inorderTraversal(root.left)  -------T(n/2)
    print root
    inorderTraversal(root.right) -------T(n/2)
  }
}
```
<br>
  
* Time Complexity - O(n)
* Space Complexity - O(n)



<br>

### * Post-Order Traversal(Using Stack)

- Left Subtree
- Right Subtree
- Root

```
postorderTraverse(root){  ----------------T(n)
  if(root equals null){
    return error message
  } else {
    postorderTraversal(root.left)  -------T(n/2)
    postorderTraversal(root.right) -------T(n/2)
    print root
  }
}
```
<br>
  
* Time Complexity - O(n)
* Space Complexity - O(n)


<br>

### * Level-Order Traversal(Using Queue)

```
levelOrderTraversal(root){
  create a Queue(Q)
  enqueue(root)
  while(Queue is not empty){
    enqueue() the child of the first element
    dequeue() and print
  }
}
```
<br>
* Time Complexity - O(n)
* Space Complexity - O(n)


<br><br>

### * Searching a node(Using Level-order Traversal)

```
searchForGivenValue(value){
  if(root == null){
    return error message
  } else {
    do a level order traversal
      if value found
        return success message
    return unsuccessful message
  }
}
```
<br>
* Time Complexity - O(n)
* Space Complexity - O(n)

<br>

### * Insertion of node(Using Level-order Traversal)

* Insertion
  * When the root is blank
  * Insert at first vacant child

<br>

```
insertNodeInBinaryTree(){
  if(root is blank){
    insert new node at root
  } else {
    do a level order traversal and find the first blank space
    insert in that blank place
  }
}
```
<br>
* Time Complexity - O(n)
* Space Complexity - O(n)

<br>

### * Deletion of node(Using Level-order Traversal)

* Insertion
  * When the value to be deleted is not existing in the tree
  * When the value to be deleted exists in the tree

<br>

```
deleteNodeFromBinaryTree()
  search for the node to be deleted
  find deepest node in the tree(using level order traversal)
  copy deepest node's data in current node
  delete deepest node
```
<br>
* Time Complexity - O(n)
* Space Complexity - O(n)