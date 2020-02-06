---
date: '2020/2/4 11:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Stack
---


Stack data structure

<!-- more -->

__Implementation options of Stack__

  * Array
    * pros : Easy to implement
    * cons : Fixed size

<br>

  * Linked List
    * pros : Variable size
    * cons : Moderate in implementation

<br>
<br>

__When to use / avoid Stack__
<br>
 * When to use
   * Helps manage the data in particular way(LIFO)
   * Cannnot be easily corrupted(No one can insert data in middle)
<br>
 * When to avoid
   * Random access not possible - if we have done some mistake, its costly to rectify.

<br><br>

__Stack By Array__

* StackByArray.java
```
package com.chung;

public class StackByArray {
	
	int[] arr;
	int topOfStack;//keeps track of the cell which is last occupied in Array, this will help in insertion/deletion

	
	public StackByArray(int size) {
		this.arr = new int[size];
		this.topOfStack = -1;
		System.out.println("Successfully created an empty Stack of Size: "+size);
	}//end of method

	
	public void push(int value) {
		//if array is full, show stack overflow error
		if (isFullStack()) {
			System.out.println("Stack overflow error!!");
		} else {
			arr[topOfStack+1] = value;
			topOfStack++;
			System.out.println("Successfully inserted " + value + " in the stack");
		}
	}//end of method
	
	
	public void pop() {
		//if array is empty, show stack underflow error		
		if (isEmptyStack()) {
			System.out.println("Stack underflow error!!");
		} else {
			System.out.println("Poping value from Stack: " + arr[topOfStack] + "...");
			topOfStack--;
		}
	}//end of method

	
	public boolean isEmptyStack() {
		//if top pointer is zero, the stack is empty
		if (topOfStack == -1)
			return true;
		else
			return false;
	}//end of method
	
	
	public boolean isFullStack() {
		if (topOfStack == arr.length-1) {
			System.out.println("Stack is full !");
			return true;
		}else {
			return false;
		}
	}//end of method
		

	public void peekOperation() {
		if (!isEmptyStack())
			System.out.println("Top of Stack: " + arr[topOfStack]);
		else {
			System.out.println("The stack is empty!!");
		}
		System.out.println();System.out.println();
	}//end of method

	
	public void deleteStack() {
		arr = null;
		System.out.println("Stack is successfully deleted");
	}//end of method

}//end of class
```

<br><br>

__Stack By Linked List__

```
package com.chung;
import linkedList.SingleLinkedList;

public class StackByLinkedList {

	SingleLinkedList list;

	
	//constructor
	public  StackByLinkedList() {
		list = new SingleLinkedList();
	}//end of method

	
	public void push(int value) {
		if(list.getHead()== null) {
			list.createSingleLinkedList(value);
		}else {
			list.insertInLinkedList(value, 0);	
		}
		System.out.println("Inserted " + value + " in Stack !");
	}//end of method

	
	public int pop() {
		int value = -1;
		if (isEmpty()) {
			System.out.println("Stack underflow error!!");
		} else {
			value = list.getHead().getValue();
			list.deletionOfNode(0);
		}
		return value;
	}// end of method

	
	public boolean isEmpty() {
		if (list.getHead() == null)
			return true;
		else
			return false;
	}// end of method

	
	public int peek() {
		if (!isEmpty())
			return list.getHead().getValue();
		else {
			System.out.println("The stack is empty!!");
			return -1;
		}
	}// end of method
	

	public void deleteStack() {
		list.setHead(null);
	}//end of method
	
}//end of method
```