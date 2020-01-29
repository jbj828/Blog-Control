---
date: '2020/1/28 22:46:25'
tags:
  - Algorithm
categories:
  - Alogrithm
thumbnail: ''
permalink: ''
title: Reucursive
---

* Properties of Recursion
  * Some operation is performed multiple times with different inputs
  * In every step we try to make the problem smaller
  * We have to have a base condition which tells a system when to stop the recursion.

<!-- more -->
* Format of a 'Recursive Function'
  * Recursive Case : Case where the function recur
  * Base Case : Case where the function does not recur


Factorial example
```
Factorial(n):
  if(n equals 0){
    return 1;
  } else {
    return (n * factorial(n-1))
  }
```

Fibonacci series
```
fib(n)
  if(n is less than 1){
      return error message
  } else if(n is equal to 1 or 2){
      return n-1;
  } else{
      return fib(n-1) + fin(n-2);
  }
```

* Time Complexity of Recursive Algo

  * Problem statement : Given a sorted array of 11 numbers, find number 110
      10 20 30 40 50 ... 90 100 110

  * Solution

```
BinarySearch(int findNumber, int arr[], start, end):  ----- T(n)
  if(start equals end){
    if(arr[start] equals findNumber){
        return findNumber
    } else{
        return error message that number does not exist in the array
    }
  } 

  mid = findMid(arr[], start, end)  
    if(mid > findNumber){
      BianarySearch(int Number, int arr[], start, mid);  -------- T(n/2)
    }else if( mid < findNumber){
      BinarySearch(int Number, int arr[], mid, end);  ----------- T(n/2)
    }else if(mid = findNumber){
      return mid;
    }
```

* Time Complexity:
T(n) = O(1) + T(n/2)

* Back Substitution : 
    * T(n) = T(n/2) + 1 ------- Equation #1
    * T(1) = 1         -------- Base Condition
    * T(n/2) = T(n/4) + 1 ------Equation #2
    * T(n/4) = T(n/8) + 1 ------Equation #3
  

  T(n) = T(n/2) + 1
       = (T(n/4) + 1) + 1
       =  T(n/4) + 2
       = (T(n/8) + 1) + 2
       = T(n/8) + 3
       = T(n/2^k) + k 


       n/2^k = 1
           n = 2^k
           k = log n


       = T(1) + log n
       = 1 + log n
       = log n


