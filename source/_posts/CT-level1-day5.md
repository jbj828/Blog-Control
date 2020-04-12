---
date: '2020/4/12 18:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test Level1 - Day5
---

Coding Test Level1 - Day5

<!-- more -->


### 하샤드 수

```
function solution(n){
    return !(n % (n+ "").split("").reduce((a,b) => +b + +a))
}
```

### 핸드폰 번호 가리기

```
function solution(s) {
    var result = "*".repeat(s.length - 4) + s.slice(-4)
    return result
}
```

 - `repeat()` 메서드는 문자열을 주어진 횟수만큼 반복해 붙인 새로운 문자열을 반환합니다.

```
str.repeat(count);
```

