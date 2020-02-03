---
date: '2020/1/30 18:46:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Linked List
---

* What is linked list?
<!-- more -->
  * A linked list is a linear data structure where is element is a separate object. Each element(node) of a list comprises of two items - the date and a reference to the next code. The most powerful feature of Linked list is that it is of variable size.



*picture ref : data Structure and algorithms by DS GUY*

<br>

 __Linked List VS Array__

    1. Seperate Object : The node of Linked list is could be separated from the list. However, the cells of Array can't be separated. The Array itself is separated from other Array.
    2. Variable Size : You can add, delete the node from Linked list. However, Array can't.
    3. Random Access : You can access the each cell of Array by using index. But on the linked list, you have to loop over all the node to get the data you want.

__Components of Linked List__   

    1. Node : Contains Data & Reference to the next Node.
    2. Head : Reference to first node in the list.
    3. Tail : Reference to last node of the list.  
     
     
  #### Types of Linked List

* __Single Linked List__
  * In a singly linked list each node in the list stores the data of the node and a reference to the next node int the list. It does not store any reference to the previous node.
  {% asset_img "linkedlist.PNG" "linked list" %}
  <br>
* __Circular Linked List__
  * In the case of a circular doubly linked list, the only change thata occurs is that the end of the given list is linked to the front
  {% asset_img "circularSingle.PNG" "circular linked list" %}
  <br>
* __Double Linked List__
  * In double linked list each node contains two reference, that references to the previous and next node
  {% asset_img "doublelinkedlist.PNG" "double linked list" %}
  <br>
* __Circular Double Linked List__
  * The only change that occurs is that the end of the given list is linked back to the front of the list and vice versa.
  {% asset_img "circularDouble.PNG" "circular double linked list" %}

