---
date: '2020/4/4 12:30:25'
tags:
  - algorithm
categories:
  - Algorithm
thumbnail: ''
permalink: ''
title: Dynamic Programming
---

dynamic programming

<!-- more -->


### Dynamic Programming

A method for solving a complex problem by breaking it down into a collection of simpler subproblems, solving each of those subproblems just once, and storing their solutions.

It only works on problems with **Optimal Substructure** & **Overlapping Subproblems**

### Overlapping Subproblems

A problme is said to have `overlapping subproblems` if it can be broken down into subproblems which are reused several times.

Ex) Finbonnaci Numbers

### Optimal Substructure

A problem is said to have `optimal substructure` if an optimal solution can be constructed from optimal solutions of its subproblems.

### Meomoization

Storing the results of expensive function calls and returning the cached result when the same inputs occur again.

#### The Fibonacci with Recursive

```
function fib(num){
   if(num <= 2) return 1;
   return fib(num -1) + fib(num -2);
}
```

Time Complexity - O(2^n)

#### Meomoization : The Fibonacci with Memoized solution(Top-Down)

```
function fib(n, memo=[]){
  if(memo[n] !== undefined) return memo[n];
  if(n <= 2) return 1;
  var res = fib(n-1, memo) + fib(n-2, memo);
  memo[n] = res;
  return res;
}
```

Time Complexity - O(n)

### Tabulation

Storing the result of a previous result in a "table"(usually an array).
Usually done using iteration.
Better space complexity can be achieved using tabulation.

### Tabulation : The Fibonacci with tabulated solution(Bottom-up Approach)

```
function fib(n){
  if(n <= 2) return 1;
  var fibNums = [0, 1, 1];
  for(var i = 3; i <= n; i++){
    fibNums[i] = fibNums[i-1] + fibNums[i-2];
  }
  return fibNums[n];
}
```

Time Complexity - O(n)
Space Complexity is better than Memoized Version.

