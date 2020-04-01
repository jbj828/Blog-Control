---
date: '2020/3/30 00:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Sorting
---

sorting

<!-- more -->

### What is Sorting?

Sorting refers to arranging data in a particular format : either ascending or descending

### Types of Sorting

{% asset_img "sorting1.PNG" 500 500 "Types-of-sorting" %}

<br>


### In-Place vs Out-Place Sorting

입력리스트 내부에서 정렬이 이뤄지는 경우를 가리킵니다. 반대는 정렬 도중에 별도 저장공간을 필요로 하는 경우입니다. 합병정렬의 경우 입력리스트를 분할해 이를 정렬하고 다시 합치는 과정에서 분할된 리스트를 별도로 저장해 두어야 합니다. 카운팅정렬과 래딕스정렬은 입력값의 빈도를 세어서 저장해 두는 변수, 결과리스트를 저장해 둘 변수가 필요합니다. 버킷정렬은 버킷이라는 변수를 만들 공간이 있어야 합니다.

##### In-Place Sort:

  * Sorting algorithms which does not require any extra space for sorting.
  * Example - Bubble Sort

##### Out-Place Sort:

  * Sorting algorithms which requires extra space for sorting
  * Example - Merge sort

<br>

### Stable vs Unstable Sorting

##### Stable Sort:

  * If a Sorting algorithm after sorting the contents **does not change the sequence** of similar content in which they appear, is called Stable sorting.
  * Example - Insertion sort

##### Unstable Sort:

  * If a sorting algorithm after sorting the contents, **changes the sequence** of similar content in which they appear, it is called Unstable sorting.
  * Example - Quick Sort

<br>

### Why "Stable Sort" is important?

  * Scenarios where 'sort key' is not the entire identity of the item.
  * Consider a person object with a name and a Age. Let's say we sorted based on their name. If we were to then sort by age in a stable way, we'd guarentee that our original ordering would be preserved for people with the same age.
  * 'group by' clauses of Database uses this concept very heavily.


<br>

### Few Terminologies

  * Increasing Order
    * If successive element is greater than previous one.
    * ex) 1,3,4,6,8,9

  * Decreasing Order
    * If successive element is less than current one.
    * ex) 9,8,6,4,3,1

  * Non-Increasing Order
    * If successive element is less than or equal to its previous element in the sequence. This order occurs when the sequence contains duplicate values.
    * ex) 9,8,6,3,3,1

  * Non-Decreasing Order
    * If the successive element is greater than or equals to its previous element in the sequence. This order occurs when the sequence contains duplicate values.
    * ex) 1,3,3,6,8,9


### Sorting Algorithms Compared

{% asset_img "compareSort.PNG" 500 500 "Compare Sorting Algorithms" %}
<br>


출처 : "Data Structures & Algorithms" by DS GUY




