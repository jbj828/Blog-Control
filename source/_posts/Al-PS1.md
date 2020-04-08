---
date: '2020/4/7 12:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test Level1 - Day1
---

coding test level1

<!-- more -->


#### 2016년 a월 b일의 요일을 구하시오

```
function getDayName(a, b){
  let dayName = new Date(2016, a-1, b).toString().slice(0,3).toUpperCase()

  return dayName
}
```

#### 단어 s의 가운데 글자를 반환하는 함수 구하기. 단어의 길이가 짝수라면 가운데 두글자를 반환.

```
function solution(s){
    const wordLength = s.length;
    const middlePoint = Math.floor(wordLength / 2 );

    if(wordLength % 2 === 0){
        return s[middlePoint-1].concat(s[middlePoint]);
    } else if(wordLength % 2 === 1){
        return s[middlePoint];
    }
}
```

#### 같은 숫자는 싫어

```
function solution(arr){
  return arr.filter((val, index) => val !== arr[index +1])
}
```

#### 나누어 떨어지는 숫자 배열

```
function solution(arr, divisor){
  var answer = [];

  arr.map((o) => {
    o % divisor === 0 && answer.push(o)
  })

  return answer.length ? answer.sort((a,b) => a-b) : [-1];
}
```

#### 두 정수의 합

```
function adder(a, b){
  let result = 0;

  return (a+b)*(Math.abs(b-a)+1)/2;
}
```

#### 문자열 내 마음대로 정렬하기

```
function solution(strings, n) {

    return strings.sort((s1, s2) => s1[n] === s2[n] ? s1.localeCompare(s2) : s1[n].localeCompare(s2[n]))
}
```

#### 문자열 내 p와 y의 개수

```
function numPY(s){
  return s.match(/p/ig).length == s.match(/y/ig).length;
}
```

  - `match()` 메서드는 문자열이 정규식과 매치되는 부분을 검색한다.
  - `str.match(regexp)`
  - 문자열이 정규식과 일치하면, 일치하는 전체 문자열을 첫 번째 요소로 포함하는 `Array`를 반환한 다음 괄호 안에 캡처된 결과가 온다. 일치하는 것이 없으면 `null`이 반환.

