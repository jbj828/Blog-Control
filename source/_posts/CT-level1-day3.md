---
date: '2020/4/11 23:30:25'
tags:
  - Coding Test
categories:
  - Coding Test
thumbnail: ''
permalink: ''
title: Coding Test Level1 - Day3, 4
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

### 이상한 문자 만들기

```
function solution(s){
    var result = "";
    var num = 0;

    for(var i = 0; i < s.length; i++){
        if(s.charAt(i) == " "){
            num = 0
            result += " "
        } else if(num % 2 === 0){
            result += (s.charAt(i)).toUpperCase()
            num++
        } else {
            result += (s.charAt(i)).toLowerCase()
            num++
        }
    }
    return result
}
```

### 자릿수 더하기

```
function solution(num) {
    let sum = 0;
    let str = num + "0"
    let i = 0;
    while (i < str.length - 1) {
        sum += str[i] / 1
        i++
    }
    return sum;
}
```

### 자연수 뒤집어 배열로 만들기

```
function solution(n){
    var arr = []

    do {
        arr.push(n%10)
        n = Math.floor(n/10)
    } while(n > 0)

    return arr;
}
```

### 정수 내림차순으로 배치하기

```
function solution(n){
    const newN = n + "";
    const newArr = newN
        .split("")
        .sort()
        .reverse()
        .join("");

        return +newArr;
}
```

### 정수 제곱근 판별

```
function solution(n) {

    let x = Math.sqrt(n)
    if (Math.floor(x) === x) {
        return Math.pow(x + 1, 2)
    } else {
        return -1
    }
}
```

### 제일 작은 수 제거하기

```
function solution(arr){
    arr.splice(arr.indexOf(Math.min(...arr)), 1);
    if(arr.length < 1) return [-1];

    return arr;
}
```

### 짝수와 홀수

```
function solution(num){
    return num % 2 ? "Odd" : "Even"
}
```

### 콜라츠 추측

```
function solution(num, count = 0) {
    return num == 1 ?
        (count >= 500 ? -1 : count) :
        solution(num % 2 == 0 ? num / 2 : num * 3 + 1, ++count)
}
```

### 평균 구하기

```
function solution(arr){
    return arr.reduce((a,b) => a+b) / arr.length
}
```
