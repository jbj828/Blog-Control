---
date: '2020/3/31 22:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Sorting - Quick Sort
---

quick sort

<!-- more -->

## Quick Sort

  * Quick Sort is Divide and Conquer algorithm.
  * At each step it finds 'Pivot' and then makes sure that all the smaller elements are on the left of 'Pivot' and all the bigger elements are on the right side of 'Pivot'.
  * It does this recursively until the entire array is sorted.
  * Unlike Merge Sort, it does not requires any external space.
  * 피봇값을 기준으로 피봇 앞에는 피봇보다 작은 값, 뒤에는 큰 값이 오도록 하여 리스트를 분할하고, 분할된 두 개 리스트 각각에 재귀적으로 이 과정을 반복해 정렬을 완성. 합병정렬과 달리 주어진 배열을 임의로 나누지 않기 때문에 대개는 효율적이지만, 피봇값이 잘못 선택되면 O(n2)이 될 수도 있음.

### Time & Space Complexity

  * Time Complexity - O(n log n)
  * Space Complexity - O(n) : system이 모든 요소를 stack에 넣고 pop 할 경우

### When to Use/Avoid Merge Sort

  * When to use:
    * When average expected time is O(n log n)

  * When not to use:
    * When space is a concern like embedded systems
    * When stable sort is required





출처 : "Data Structures & Algorithms" by DS GUY


{% asset_img "jsp-session-study.png" 500 300 "title" %}

