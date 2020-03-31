---
date: '2020/3/31 14:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Sorting - Merge Sort
---

merge sort

<!-- more -->

## Merge Sort

  * Merge Sort is a Divide and Conquer algorithm.
  * It divides input array in two halves, keeps breaking those 2 halves recursively until they become too small to be broken further.
  * Then each of the broken pieces are merged together to inch towards final answer.
  * 리스트를 잘게 쪼갠 뒤 둘씩 크기를 비교해 정렬하고 분리된 리스트를 재귀적으로 합쳐서 정렬을 완성, 분할된 리스트를 저장해둘 공간이 필요해 메모리 소모량이 큰 편


{% asset_img "mergeSort.png" 500 300 "Merge Sort" %}

### Time & Space Complexity

  * Time Complexity - O(n log n)
  * Space Complexity - O(n)

### When to Use/Avoid Merge Sort

  * When to use:
    * When you need a `stable sort`
    * When average expected time is O(n log n)

  * When not to use:
    * When space is a concern like embedded systems

### Coding Merge Sort on Javascript


```
function merge(arr1, arr2){
    let result = [];
    let i = 0;
    let j = 0;

    while( i < arr1.length && j < arr2.length){
        if(arr1[i] < arr2[j]){
            result.push(arr1[i]);
            i++;
        } else {
            result.push(arr2[j]);
            j++;
        }
    }

    while( i < arr1.length){
        result.push(arr1[i]);
        i++;
    }
    while( j < arr2.length){
        result.push(arr2[j]);
        j++;
    }
    return result;
}


function mergeSort(arr){
    if(arr.length <= 1) return arr;
    let mid = Math.floor(arr.length /2);
    let left = mergeSort(arr.slice(0, mid));
    let right = mergeSort(arr.slice(mid));
    return merge(left, right);
}
```



출처 : "Data Structures & Algorithms" by DS GUY



