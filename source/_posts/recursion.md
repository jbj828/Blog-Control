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


