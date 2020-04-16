---
date: '2020/4/16 18:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test - Code Signal
---

Coding Test 


<!-- more -->

### 쇠막대기

```
function solution(arrangement) {

    var answer = 0;
    var stack = 0;
    for (let i = 0; i < arrangement.length; i++) {
        if (arrangement[i] === '(' && arrangement[i + 1] === ')') {
            answer += stack;
            i++
        } else if (arrangement[i] === '(') {
            stack++
        } else {
            stack--
            answer += 1
        }
    }
    return answer
}
```

### centuryFromYear

```
function centuryFromYear(year) {
    return Math.ceil(year / 100)
}
```

### checkPalindrome

```
function checkPalindrome(inputString) {
    return inputString == inputString.split('').reverse().join('');
}
```

### adjacentElementsProduct

```
function adjacentElementsProduct(arr) {
    return Math.max(...arr.slice(1).map((x, i) => [x * arr[i]]))
}
```

### shapeArea

```
function shapeArea(n) {
    return n*n + (n-1)*(n-1);
}
```

### Make array consecutive 2

```
function makeArrayConsecutive2(statues) {
    return Math.max(...statues) - Math.min(...statues) + 1 - statues.length
}
```


