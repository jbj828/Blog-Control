---
date: '2020/3/31 00:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Sorting - Insertion Sort / Bucket Sort 
---

insertion sort / bucket sort

<!-- more -->

## Insertion Sort

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


<br>

## Bucket Sort

 * Bucket sort is a sorting algorithm that works by distributing the elements of an array into a number of buckets.
 * Each bucket is then sorted individually.
 * 데이터를 루트에 넣었을 때 나온 값의 개수만큼 버킷을 두어 데이터를 나누고 버킷별로 정렬한 후 합쳐 정렬을 완성, 데이터 분포가 균등할 경우 계산복잡성을 낮출 수 있으나 그 반대의 경우 효과를 기대하기 어려울 수 있음

### Bucket Sort Algorithm

 * Create Number of buckets = ceil/floor(squareroot of total number of items)
 * Iterate through each number and place it in appropriate bucket
 * Appropriate bucket = Ceil((Value * number of buckets) / max value in array)
 * Sort all the buckets(Using `Quick Sort` is the best for time complexity)
 * Merge all the buckets

### Time & Space Complexity

  * Time Complexity - O(n log n)
  * Space Complexity - O(n)

### When to Use / Avoid Bucket sort

 * When to use:
   * When input is uniformly distributed over a range

 * When not to use
   * When space is a concern

### Coding Bucket Sort

BucketSort.java
```
package com.chung;

import java.util.ArrayList;
import java.util.Collections;

public class BucketSort {

    int arr[];

    // constructor
    public BucketSort(int arr[]){
        this.arr = arr;
    }

    // Prints Array
    public void printArray(){
        int tmp = 0;
        for(int i = 0; i < arr.length; i++){
            System.out.println(arr[i] + " ");
            tmp++;
            if(tmp == 20){
                System.out.println();
                tmp = 0;
            }
        }
    }

    // Prints Buckets
    public void printBucket(ArrayList<Integer>[] buckets){
        for(int i = 0; i < buckets.length; i++){
            System.out.println("\nBucket#" + i + ": ");
            for(int j = 0; j< buckets[i].size(); j++){
                System.out.println(buckets[i].get(j) + " ");
            }
        }
    }



    // Sorting Method
    public void bucketSort(){

        // Create sqrt# of buckets, so that the distribution is even
        int numberOfBuckets = (int) Math.ceil(Math.sqrt(arr.length));
        int maxValue = Integer.MIN_VALUE;
        int minValue = Integer.MAX_VALUE;

        // Find the min and max value from the array
        for(int value : arr){
            if(value < minValue){
                minValue = value;
            } else if( value > maxValue){
                maxValue = value;
            }
        }

        // Create an Array of Buckets
        ArrayList<Integer>[] buckets = new ArrayList[numberOfBuckets];

        // initializing empty buckets
        for(int i = 0; i < buckets.length; i++){
            buckets[i] = new ArrayList<Integer>();
        }

        for(int value : arr){
            int bucketNumber = (int) Math.ceil((value * numberOfBuckets) / maxValue);
            buckets[bucketNumber -1].add(value);
        }

        System.out.println("Printing buckets before sorting");
        printBucket(buckets);


        // Sort Buckets
        for(ArrayList<Integer> bucket: buckets){
            Collections.sort(bucket);
        }

        System.out.println("\n\nPrinting buckets after sorting");
        printBucket(buckets);

        // Concatenate buckets
        int index = 0;
        for(ArrayList<Integer> bucket: buckets){
            for(int value:bucket){
                arr[index] = value;
                index++;
            }
        }
    }

}
```

Main.java
```
package com.chung;

import java.util.Random;

public class Main {

    public static void main(String[] args) {


        int arr[] = new int[100];
        //Generating 100 random numbers in the range of 0-100
        Random random = new Random();
        for(int i=0;i<100;i++) {
            arr[i] = random.nextInt(100)+100;
        }


        //Passing this array to BucketSort method
        BucketSort bs = new BucketSort(arr);
        System.out.println("Array before Sorting: ");
        bs.printArray();
        bs.bucketSort();


        System.out.println("\n\nArray after Sorting: ");
        bs.printArray();

    }
}
```


출처 : "Data Structures & Algorithms" by DS GUY


{% asset_img "jsp-session-study.png" 500 300 "title" %}

