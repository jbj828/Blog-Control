---
date: '2020/1/30 18:46:25'
tags:
  - Algorithm
categories:
  - Alogrithm
thumbnail: ''
permalink: ''
title: Linked List
---

* What is linked list?
<!-- more -->
  * A linked list is a linear data structure where is element is a separate object. Each element(node) of a list comprises of two items - the date and a reference to the next code. The most powerful feature of Linked list is that it is of variable size.


{% asset_img "linkedlist.PNG" "linked list" %}
ref : data Structure and algorithms by DS GUY

* Linked List VS Array :
    1. Seperate Object : The node of Linked list is could be separated from the list. However, the cells of Array can't be separated. The Array itself is separated from other Array.
    2. Variable Size : You can add, delete the node from Linked list. However, Array can't.
    3. Random Access : You can access the each cell of Array by using index. But on the linked list, you have to loop over all the node to get the data you want.

* Components of Linked List :
    1. Node : Contains Data & Reference to the next Node.
    2. Head : Reference to first node in the list.
    3. Tail : Reference to last node of the list.


  