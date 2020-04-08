---
date: '2020/4/8 15:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test Level1 - Day2
---

coding test level1

<!-- more -->

#### 문자열 내림차순으로 배치하기

```
function solution(s){
  return s.split('').sort().reverse().join('');
}
```

#### 문자열 다루기 기본

```
function solution(s){
  var regex = /^\d{6}$|^\d{4}$/;
  return regex.test(s);
}
```

#### 서울에서 김서방 찾기

```
function findKim(seoul){
  var idx = seoul.indexOf("Kim");
  return `김서방은 ${idx}에 있다`;
}
```

#### 소수 찾기

 *Failed*

```
function solution(n) {
    const s = new Set();
    for (let i = 1; i <= n; i += 2) {
        s.add(i);
    }
    s.delete(1);
    s.add(2);
    for (let j = 3; j < Math.sqrt(n); j++) {
        if (s.has(j)) {
            for (let k = j * 2; k <= n; k += j) {
                s.delete(k);
            }
        }
    }
    return s.size;
}
```

#### 수박수박수박수...

```
function solution(n){
  let result = "수박"

  result = result.repeat(n-1).substring(0,n);

  return result
}
```

#### 문자열을 정수로 바꾸기

```
function solution(str){
  return str/1
}
```

