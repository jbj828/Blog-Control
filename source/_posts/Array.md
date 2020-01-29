---
date: '2020/1/29 13:46:25'
tags:
  - Algorithm
categories:
  - Alogrithm
thumbnail: ''
permalink: ''
title: Basic Array Theory and Single Dimension Array
---

* Types of Array

<!-- more -->

  * One Dimensional   (Array[i])
  * Multi Dimensional 
    * two Dimensioanl  (Array[row][col])
    * three  ''        (Array[depth][row][col])
    * four   ''
    * .. n   Dimensional

주로 one, two dimensional 사용함


* How is an Array represented in Memory?
  * 2d 3d 관계없이 memory에는 1행에 순서대로 저장된다. 1d Array 랑 같은 방식이라고 보면 된다.


* Create an Array
  * Declare : Creates a reference to Array
  * Instanciation of an Array : Creates a Array
  * Initialization : Assigns values to cells in Array



* Single Dimension Array
  * Array has a index. So when we consider the time complexity, we don't need to loop all the array to get the value. We can just use the index to get the value.

```
package com.chung;

public class SingleDimensionArray {
	int arr[] = null;

    
    //Constructor
	public SingleDimensionArray(int sizeOfArray) {
		arr = new int[sizeOfArray];
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.MIN_VALUE;
		}
	}

	
    // Print the array
	public void traverseArray() {
		try {
			for (int i = 0; i < arr.length; i++) {
				System.out.print(arr[i] + " ");
			}
		} catch (Exception e) {
			System.out.println("Array no longer exists !");
		}
	}
    
    
	//Insert value in the Array
	public void insert(int location, int valueToBeInserted) {
		try {
			if (arr[location] == Integer.MIN_VALUE) {
				arr[location] = valueToBeInserted;
				System.out.println("Successfully inserted " + valueToBeInserted + " at location: " + location);
			} else {
				System.out.println("This cell is already occupied by another value.");
			}
		} catch (ArrayIndexOutOfBoundsException e) {
			System.out.println("Invalid index to access array !");
			// e.printStackTrace();
		}
	}

	
	

		
	// Access a particular element of an array
	public void accessingCell(int cellNumber) {
		try {
			System.out.println(arr[cellNumber]);

		} catch (ArrayIndexOutOfBoundsException e) {
			System.out.println("Invalid index to access array !");

		}
	}

	
	//Search for an element in the given Array
	public void searchInAnArray(int valueToSearch) {
		for (int i = 0; i < arr.length; i++) {
			if (arr[i] == valueToSearch) {
				System.out.println("Value found !");
				System.out.println("Index of " + valueToSearch + " is: " + i);
				return;
			}
		}
		System.out.println(valueToSearch + " is not found!!");
	}


	//Delete value from given Array
	public void deleteValueFromArray(int deleteValueFromThisCell) {
		try {
			arr[deleteValueFromThisCell] = Integer.MIN_VALUE;
		} catch (ArrayIndexOutOfBoundsException e) {
			System.out.println();
			System.out.println("Cant delete the value as cell# provided is not in the range of array !");
			// e.printStackTrace();
		}
	}
	
	
	//Delete the entire Array
	public void deleteThisArray() {
		arr = null;
		System.out.println("Array has been succefully deleted");
	}
	
}//end of class
```