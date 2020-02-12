---
date: '2020/2/12 15:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: AVL Tree 
---

AVL Tree

<!-- more -->

__Why AVL Tree?__

* Depending on Incoming data, A Binary Search tree can get skewed and hence its performance starts going down. Instead of O(log n) for insertion/searching/deleting it can go up to O(n)
* AVL tree attempts to solve this problem of 'skewing' by introducing concept called 'Rotation'.

__What is AVL Tree?__

* An AVL tree is a balanced 'Binary Search Tree' where the height of immediate subtrees of any node differs by at most one(also called balance factor).
* If at any time heights differ by more than one, rebalancing is done to restore this property(called rotation).
* Empty height is always considered -1.

<br>

### Algorithm of AVL Tree

* create, search, traverse Algorithm is totally same as the BST.



#### Insertion of node in AVL Tree

* Case#1 - Whene 'rotation' is not required.
    * The algorithm is same as the BST Insertion.
* Case#2 - When 'rotation is required(LL, LR, RR, RL).

__Left-Left Condition__

* What is Left-Left condition?
  * Left-Left Node from currentNode is causing disbalance.
  * In this case we do a 'Right Rotation'.

<br>

```
rightRotate(currentDisbalancedNode)
  newRoot = currentDisbalancedNode.left
  currentDisbalancedNode.left = currentDisbalancedNode.left.right
  newRoot.right = currentDisbalancedNode
  currentDisabledNode.height = calculateHeight(currentDisbalancedNode)
  newRoot.height = calculateHeight(newRoot)
```

<br>


* Time Complexity - O(1)
* Space Complexity - O(1)

<br>

__Left-Right Condition__

* What is Left-Right condition?
  * Left-Right Node from currentNode is causing disbalance.
  * In this case we do a 'Left Rotation followed by Right Rotation'.

<br>

```
leftRotate(currentDisbalancedNode'sLeftChild)
  newRoot = currentDisbalancedNode'sLeftChild.right
  currentDisbalancedNode'sLeftChild.right = currentDisbalancedNode'sLeftChild.right.left
  newRoot.left = currentDisbalancedNode'sLeftChild
  currentDisbalancedNode'sLeftChild.Height = calculateHeight(currentDisbalancedNode'sLeftChild)
  newRoot.Height = calculateHeight(newRoot)
  return newRoot


  rightRotate(currentDisbalancedNode)  ------ left-left Condition이랑 같음
```

<br>


* Time Complexity - O(1)
* Space Complexity - O(1)

<br>

__Right-Right Condition__

* What is Right-Right condition?
  * Right-Right Node from currentNode is causing disbalance.
  * In this case we do a 'Left Rotation'.

<br>

```
leftRotate(currentDisbalancedNode)
  newRoot = currentDisbalancedNode.right
  currentDisbalancedNode.right = currentDisbalancedNode.right.left
  newRoot.left = currentDisbalancedNode
  currentDisbalancedNode.Height = calculateHeight(currentDisbalancedNode)
  newRoot.Height = calculateHeight(newRoot)
  return newRoot
```

<br>


* Time Complexity - O(1)
* Space Complexity - O(1)

<br>

__Right-left Condition__

* What is Right-left condition?
  * Right-left Node from currentNode is causing disbalance.
  * In this case we do a 'Right Rotation followed by Left Rotation'.

<br>

```
rightRotate(currentDisableNode'sRight)
  newRoot = currentDisableNode'sRight.left
  currentDisableNode'sRight.left.right = currentDisableNode'sRight
  currentDisableNode'sRight.height = calculateHeight(currentDisableNode'sRight)
  newRoot.height = calculateHeight(newRoot)
  return newRoot;

leftRotate(currentDisabledNode)
  newRoot = currentDisabledNode.right
  currentDisabledNode.right = currentDisabledNode.right.left
  newRoot.left = currentDisabledNode
  currentDisabledNode.height = calculateHeight(currentDisabledNode)
  newRoot.height = calculateHeight(newRoot)
  return newRoot
```

<br>


* Time Complexity - O(1)
* Space Complexity - O(1)

<br>

__Insertion Algorithm in AVL Tree__

```
Node Insert(Node root, int data)
  if(root == null) return new Node(data)
  else if(data <= root.data) root.left = insert(root.left, data)
  else root.right = insert(root.right, data)
  
  int balance = height(root.left) - height(root.right)
  if(balance > 1)
    if height(root.left.left) >= height(root.left.right)
      RightRotation(root) //LL condition
    else
      LeftRotation(root.left)
      RightRotation(root)  // LR condition

  else if(balance < -1)  // if right subtree is overloaded
    if height(root.right.right) >= height(root.right.left)
      LeftRotation(root)  // RR condition
    else
      RightRotation(root.right)
      LeftRotation(root)  // RL condition
  
  root.height = max(root.left, root.right) + 1
  return root
```

<br>

* Time Complexity - O(log n)
* Space Complexity - O(log n)



<br>

#### Deletion of Node from AVL Tree

* Deletion of a node
  * Case#1 - When tree does not exists
  * Case#2 - When 'rotation' is not required(BST Conditions)
      * Node to be deleted is leaf node
      * Node to be deleted is having 1 child
      * Node to be deleted has 2 children
  * Case#3 - When 'rotation' is required(LL, LR, RR, RL)

<br>

```
deleteNodeOfAVL(currentNode, valueToBeDeleted)
  if(currentNode == null) return null;

  if(valueToBeDeleted < currentNode.value)
    then currentNode.left = deleteNodeOfAVL(currentNode.left, valueToBeDeleted)
  else if(valueToBeDeleted > currentNode.value)
    then currentNode.right = deleteNodeOfAVL(currentNode.right, valueToBeDeleted)
  else  //if the currentNode is the node to be deleted
      if currentNode have both children, then find minimum element from right subtree(Case#3)
          replace current node with minimum node from right subtree and delete minimum node from right

      else if nodeToBeDeleted has only left child(Case#2)
            then currentNode = currentNode.left
      else if nodeToBeDeleted has only right child
      (Case#2)
            then currentNode = currentNode.right
      
      else //if nodeToBeDeleted do not have child(Case#1)
            currentNode = null;

  int balance = checkBalance(currentNode.left, currentNode.right);

  if(balance > 1)
      if(checkBalance(currentNode.left().left(), currentNode.left().right()) > 0)
          currentNode = rightRotate(currentNode); //LL Condition
      
      else 
          currentNode.left = leftRotate(currentNode.left);
          currentNode = rightRotate  //LR condition
    
    else if(balance < -1)
      if(checkBalance(currentNode.right().right(), currentNode.right().left()) > 0)
          currentNode = leftRotate(currentNode); //RR Condition

      else 
          currentNode.right = rightRotate(currentNode.right); //RL condition
          currentNode = leftRotate(currentNode);

  if(currentNode.left() != null) then currentNode.left().setHeight(calculateHeight(currentNode.left));
  if(currentNode.right() != null) then currentNode.right().setHeight(calculateHeight(currentNode.right());
  currentNode.setHeight(calculateHeight(currentNode));

  return currentNode;      
```

<br>

* Time Complexity - O(log n)
* Space Complexity - O(log n)


출처 : "Data Structures & Algorithms" by DS GUY
