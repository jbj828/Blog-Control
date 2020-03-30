---
date: '2020/3/30 11:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Sorting - Bubble Sort / Selection Sort
---

bubble sort / selection sort

<!-- more -->



### What is Bubble Sort?

  * Bubble sort, sometimes is also referred as Sinking sort.
  * Repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order.
  * 주어진 배열의 마지막 위치에 있는 요소를, 정렬되지 않은 직전 요소부터 첫 요소에 이르기까지 비교해 정렬 순서가 맞지 않은 모든 case에 대해 요소 위치를 바꿔줌. 이를 요소 수만큼 반복. 가장 간단하지만 비효율적인 알고리즘.

### Time & Space Complexity

  * Time Complexity - O(n2)
  * Space Complexity - O(1)

### When to use/avoid 

  * When to use:
    * When input is already sorted
    * Space is a concern
    * Easy to implement

  * When to avoid:
    * Average case time complexity is poor


### Coding Bubble Sort

```
package sorting;

public class BubbleSort {

	void bubbleSort(int arr[]) {
		int n = arr.length;
		for (int i = 0; i < n - 1; i++) //run from first cell to last cell
			for (int j = 0; j < n - i - 1; j++) //run from first cell to "last cell - iteration"
				if (arr[j] > arr[j + 1]) {
					int temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
	}//end of method

	
	/* Prints the array */
	void printArray(int arr[]) {
		int n = arr.length;
		for (int i = 0; i < n; ++i)
			System.out.print(arr[i] + " ");
		System.out.println();
	}

}// end of class
```

<br>

### Selection Sort

  * The Selection sort algorithm is based on the idea of finding the minimum or maximum element in an unsorted array and then putting it in its correct position in a sorted array.
  * 요소 위치 변경 횟수를 줄여 버블정렬을 일부 개선한 알고리즘. 정렬 순서가 맞지 않으면 무조건 자리를 바꿔줬던 버블정렬과 달리, 1회 iteration마다 최소값(혹은 최대값)을 찾고 단 한번만 해당 요소 위치를 바꿔줌.

### Time & Space Complexity

  * Time Complexity - O(n2)
  * Space Complexity - O(1)

### When to use/avoid 

  * When to use:
    * When we don't have additional memory
    * Easy to implement

  * When to avoid:
    * Average case time complexity is poor


### Coding Selection Sort

```
package com.chung;

public class SelectionSort {

    void selectionSort(int arr[]){

        for(int i = 0; i < arr.length; i++){
            int minimumIndex = i;
            for(int j = i+1; j < arr.length; j++){
                if(arr[j] < arr[minimumIndex]){
                    minimumIndex = j;
                }
            }
            if(minimumIndex != i){
                int temp = arr[i];
                arr[i] = arr[minimumIndex];
                arr[minimumIndex] = temp;
            }
        }
    }

    public static void printArray(int arr[]){
        for(int i =0; i < arr.length; i++){
            System.out.println(arr[i] + " ");
        }
    }
}
```


출처 : "Data Structures & Algorithms" by DS GUY


{% asset_img "jsp-session-study.png" 500 300 "title" %}
