---
date: '2020/4/17 18:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test - Code Signal Intro 2
---

Coding Test - Code Signal Intro2



<!-- more -->

### All Longest Strings

```
function allLongestStrings(inputArray) {
    'use strict';
    let maxSize = Math.max(...inputArray.map(x => x.length));
    return inputArray.filter(x => x.length === maxSize);
}
```

### commonCharacterCount

```
function commonCharacterCount(s1, s2) {
    for (var i = 0; i < s1.length; i++) {
        s2 = s2.replace(s1[i], "!");
    }
    return s2.replace(/[^!]/g, "").length;
}
```

### isLucky

```
function isLucky(n) {
    var count = 0;
    n = String(n).split('').map(t => parseInt(t));
    n.forEach((el, i) => (i < n.length / 2) ? count += el : count -= el)
    return count == 0
}
```

### Sort by Height

```
function sortByHeight(a) {

    var people = a.filter(el => el > 0)
    people.sort((a, b) => a - b)

    for (let i = 0; i < a.length; i++) {
        if (a[i] !== -1) {
            a[i] = people.shift()
        }
    }

    return a
}
```

### reverseInParentheses

```
function reverseInParentheses(inputString) {
    while (inputString.includes('(')) {
        inputString = inputString.replace(/\(([^()]*)\)/, (_, str) => [...str].reverse().join(''));
    }
    return inputString;
}
```

### alternatingSums

```
function alternatingSums(a) {
    let teamA = []
    let teamB = []
    let result = []

    teamA = a.filter((e, i) => i % 2 === 0)
    teamB = a.filter((e, i) => i % 2 === 1)


    result.push(teamA.reduce((a, b) => a + b , 0))
    result.push(teamB.reduce((a, b) => a + b , 0))

    return result
}
```