---
date: '2020/3/31 00:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Sorting - Insertion Sort
---

insertion sort

<!-- more -->

### Insertion Sort

  * In Insertion sort algorithm we divide the given array into 2 parts. Sorted & Unsorted.
  * Then from Unsorted, we pick the first element and find its correct position in sorted array.
  * Repeat till Unsorted array is empty.

  * 모든 요소에 대해 앞에서부터 차례대로 이미 정렬된 배열(sorted list)과 비교하여 sorted list내 자신의 위치를 찾아 삽입함으로써 정렬을 완성, 입력데이터가 이미 정렬된 상태라면 O(n)의 빠른 속도를 보이지만 그렇지 않은 경우 다른 기법을 적용하는 것이 나음.

### Time & Space Complexity

  * Time Complexity - O(n2)
  * Space Complexity - O(1)

### When to Use/Avoid Insertion Sort

  * When to use:
    * No extra space
    * Simple implementation
    * Best when we have continuous inflow of numbers and we want to keep the list shorted

  * When to avoid:
    * Average case is bad

### Coding Insertion Sort

```
package sorting;

public class InsertionSort {
	
	static void insertionSort(int [] A) {
		 for(int  i = 1 ; i<A.length;i++) {  
			 int  tmp=A[i], j=i;
		     while ( j>0 && A[j-1]>tmp ) {	
		        A[j]=A[j-1];
		        j--;
		     }
		     A[j] = tmp;
		 }//end of for loop
	}//end of method
	
	
	public static void printArray(int []array) {
		for (int i = 0; i < array.length; i++) {
			System.out.print(array[i]+"  ");
		}
	}//end of method

}//end of class
```




출처 : "Data Structures & Algorithms" by DS GUY


{% asset_img "jsp-session-study.png" 500 300 "title" %}

