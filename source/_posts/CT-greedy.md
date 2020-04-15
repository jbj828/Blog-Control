---
date: '2020/4/15 18:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test - Level2 / Day1
---

Coding Test - Level 2

<!-- more -->


### 백준 그리디 알고리즘 1번 문제(Greedy)

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

### 탑(Queue)

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

### 프린터(Queue)

```
function solution(priorities, location) {
    var arr = priorities.map((priority, index) => {
        return {
            index: index,
            priority: priority
        }
    })

    var queue = []

    while (arr.length > 0) {
        var firstEle = arr.shift()
        var hasHigherElement = arr.some(ele => ele.priority > firstEle.priority)

        if (hasHigherElement) {
            arr.push(firstEle)
        } else {
            queue.push(firstEle)
        }
    }

    return queue.findIndex(queueEle => queueEle.index === location) + 1
}
```