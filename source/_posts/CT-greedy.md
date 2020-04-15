---
date: '2020/4/15 18:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test - Level 2
---

Coding Test - Level 2

<!-- more -->


### 백준 그리디 알고리즘 1번 문제

```
function atm(n, time) {
    time.sort((a, b) => a - b)
    let totalTime = []

    let sum = 0;
    for (let i = 0; i < time.length; i++) {
        sum += time[i];
        totalTime.push(sum)
    }

    return totalTime.reduce((a, b) => a + b)
}
```

### 탑

```
function solution(heights){
  return heights.map((v, i)=>{
    while(i){
      i--
      if(heights[i] > v){
          return i+1
      }
    }
    return 0
  })
}
```

