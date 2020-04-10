---
date: '2020/4/9 23:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test Level1 - Day3
---

Coding Test Level1 - Day3

<!-- more -->

### 시저 암호

```
function solution(s, n) {
    var result = "";

    for (var i = 0; i < s.length; i++) {
        if (s[i] == " ") result += " "
        else
            result += String.fromCharCode((s.charCodeAt(i) > 90) ?
                (s.charCodeAt(i) + n - 97) % 26 + 97 : (s.charCodeAt(i) + n - 65) % 26 + 65
            )
    }

    return result
}
```

### 약수의 합

```
function solution(num) {
    let sum = 0;
    for (let i = 1; i <= num; i++) {
        if (num % i === 0) sum += i
    }
    return sum
}
```

