---
date: '2020/2/5 12:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Circular Queue(Array) / Linear Queue(Linked List)
---


Queue


<!-- more -->


__Why learn Circular Queue?__

* dequeue operation causes blank cells Linear Queue(Array Implementation). 
* 삭제하고 남은 자리를 뒤에서부터 차례대로 채워넣으면 되지만 time complexity가 O(n)이 되어버린다. 우리의 목표는 항상 O(1)이다.

<br><br>

__time / space complexity__

* Array는 만들 때 space complexity가 O(n) 나머지 메서드는 모두 O(1)
* Linked List는 모든 메서드 O(1)
<br>
그러므로 Queue를 사용하고자 한다면 Linked List가 Space Complexity에서 낫기 때문에 Linked List사용하도록 한다

<br><br>

__When to Use / Avoid Queue__

* When to Use
  * Helps manage the data in particular way(FIFO)
  * Not easily corrupted(No one can easily insert data in middle)
<br>

* When to Avoid
  * Random access not possible - if we have done some mistake, it is costly to rectify

<br><br>

__Circular Queue Coding__

CircularQueueByArray.java
```
package com.chung;
public class CircularQueueByArray{
	
	int[] arr;
	int topOfQueue;
	int size;
	int start;

	
	public CircularQueueByArray(int size) {
		this.arr = new int[size];
		this.size = size;
		this.topOfQueue = -1;
		start = -1;
		System.out.println("Successfully created an empty queue of size: "+size);
	}//end of method


	public void enQueue(int value) {
		if(arr==null) {
			System.out.println("Array is not yet created. Please create one first.");
		}else if (isQueueFull()) {
			System.out.println("\nQueue overflow error!!");
		}else {
			initializeStartOfArray();
			if (topOfQueue+1 == size) { //if top is already at last cell of array, then reset it to first cell
				topOfQueue=0;
			}else {
				topOfQueue++;
			}
			arr[topOfQueue] = value;
			System.out.println("\nSuccessfully inserted "+value+" in the queue");
		}
	}//end of method

	
	public void initializeStartOfArray() {
		if (start == -1) { 
			start = 0;
		}
	}//end of method
	
	
	public void deQueue() {
		if (isQueueEmpty()) {
			System.out.println("Queue underflow error!!");
		} else {
			System.out.println("\n---------------------------------------------");
			System.out.println("Before Dequeue..");printArray();
			System.out.println("\nDequeing value from Queue...");
			System.out.println("Dequeued: "+arr[start]+" from queue");
			arr[start] = 0; //initialize the unused cell to 0
			if (start == topOfQueue) { //if there is only 1 element in Queue
				start = topOfQueue = -1;
			}else if (start+1 == size) { //if start has reached end of array, then start again from 0
				start=0;
			}else {
				start++;
			}
		}
		System.out.println("After Dequeue..");printArray();
		System.out.println("---------------------------------------------");
	}//end of method

	
	public boolean isQueueEmpty() {
		if (topOfQueue == -1)
			return true;
		else
			return false;
	}//end of method

	
	public boolean isQueueFull() {
		if (topOfQueue+1 == start) { //If we have completed a circle, then we can say that Queue is full
			return true;
		}else if ((start==0) && (topOfQueue+1 == size)) { //Trivial case of Queue being full
			return true;
		}else {
			return false;
		}
	}//end of method

	
	public void peekOperation() {
		//if stack is not empty, return the value on top of stack
		if (!isQueueEmpty()) {
			System.out.println("\nPeeking value from queue...");
			System.out.println(arr[start]); 
		}else {
			System.out.println("The queue is empty!!");
		}
	}//end of method

	
	public void deleteStack() {
		System.out.println("\n\nDeleting the entire Queue...");
		arr = null;
		System.out.println("Queue is successfully deleted !");
	}//end of method
	
	
	//Print entire array
	public void printArray() {
		System.out.println("Array now...");
		for(int i=0; i<size; i++) {
			System.out.print(arr[i]+"  ");
		}
		System.out.println("\nStart = " + start);
		System.out.println("End = "+ topOfQueue);
	}//end of method

}//end of class
```

<br><br>


QueueByLinkedList.java
```
package com.chung;

import linkedList.SingleLinkedList;

public class QueueByLinkedList {

    SingleLinkedList list;


    //constructor
    public QueueByLinkedList() {
        list = new SingleLinkedList();
    }//end of method


    public void enQueue(int value) {
        if (list.getHead() == null) {
            list.createSingleLinkedList(value);
        } else {
            // push a value on last of queue, update list tail too
            list.insertInLinkedList(value, list.getSize());
        }
    }//end of method


    public int deQueue() {
        int value = -1;
        if (isQueueEmpty()) {
            System.out.println("Queue underflow error!!");
        } else {
            value = list.getHead().getValue();
            list.deletionOfNode(0);
        }
        return value;
    }//end of method


    public int peek() {
        if (!isQueueEmpty())
            return list.getHead().getValue();
        else {
            System.out.println("The queue is empty!!");
            return -1;
        }
    }//end of method


    public boolean isQueueEmpty() {
        if (list.getHead() == null)
            return true;
        else
            return false;
    }//end of method


    public void deleteStack() {
        list.setHead(null);
    }//end of method

}//end of class
```