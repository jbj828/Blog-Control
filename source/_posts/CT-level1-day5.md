---
date: '2020/4/14 18:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test Level1 - Day5, 6
---

Coding Test Level1 - Day5, 6

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

### 행렬의 덧셈

```
function solution(A, B) {
    return A.map((a, i) => a.map((b, j) => b + B[i][j]))
}
```

  - `map()` 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다.

```
arr.map(callback(currentValue[, index[, array]])[,thisArg])
```

### Summer/Windter Coding(~2018)

```
function solution(d, budget) {
    d.sort((a, b) => a - b)

    while (d.reduce((a, b) => (a + b), 0) > budget) d.pop()

    return d.length
}
```

### 완주하지 못한 선수

```
function solution(participant, completion) {
    participant.sort()
    completion.sort()

    for(let i in participant){
        if(participant[i] !== completion[i]) return participant[i]
    }
}
```

### 모의고사

```
function solution(answers) {
    let answer = []
    const a1 = [1, 2, 3, 4, 5]
    const a2 = [2, 1, 2, 3, 2, 4, 2, 5]
    const a3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5]

    let a1c = anwsers.filter((a, i) => a === a1[i % a1.length]).length
    let a2c = anwsers.filter((a, i) => a === a2[i % a2.length]).length
    let a3c = anwsers.filter((a, i) => a === a3[i % a3.length]).length

    const max = Math.max(a1c, a2c, a3c)

    if (a1c === max) answer.push(1)
    if (a2c === max) answer.push(2)
    if (a3c === max) answer.push(3)

    return answer
}
```

### 체육복

```
function solution(n, lost, reserve) {
    let answer = n;

    for (let i = 0; i < reserve.length; i++) {
        if (lost.includes(reserve[i])) {
            lost.splice(lost.indexOf(reserve[i]), 1)
            reserve.splice(i, 1)
            i--
        }
    }

    for (let i = 0; i < reserve.length; i++) {
        if (lost.includes(reserve[i] - 1)) {
            lost.splice(lost.indexOf(reserve[i] - 1), 1)
            reserve.splice(i, 1)
            i--;
        } else if (lost.includes(reserve[i] + 1)) {
            lost.splice(lost.indexOf(reserve[i] + 1), 1)
            reserve.splice(i, 1)
            i--
        }
    }

    answer = n - lost.length;
    return answer
}
```

