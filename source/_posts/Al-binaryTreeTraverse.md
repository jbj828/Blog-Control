---
date: '2020/2/6 23:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Binary Tree - Traverse
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

### * PreOrder Traversal

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
* Space Complexity - O(n)
