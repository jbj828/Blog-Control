---
date: '2020/4/8 20:30:25'
tags:
  - Javascript
categories:
  - Javascript
thumbnail: ''
permalink: ''
title: ES6 - Set
---

es6 -set

<!-- more -->

Set은 데이터 타입 중 하나이며 **중복되는 값을 가지지 않는 값들의 리스트**이다. 이 때 값에는 순서가 존재하지 않다. 

### 구성자(Constructor)

새로운 set을 만들 때 `new Set()`을 활용한다. 이 때 구성자에 반복자(iterator)를 작성할 수 있다.

```
const foo = new Set();
console.log(foo) // Set {}

const bar = new Set([1,2,3]);
console.log(bar) // Set {1,2,3}
```

set을 만들 때 중복되는 값을 가진 반복자를 넘기면, `Set`이 알아서 중복되는 값들 중 맨 앞의 값만 남기고 무시한다.

```
const foo = new Set([1,2,2,3,4,5,5,6])
console.log(foo) // Set {1,2,3,4,5,6}
```

### 객체 Set을 진짜 Set으로

`Set`이 존재하기 이전에는 일반 객체를 활용해서 set을 구현해야 했다. 하지만 문자열(string)만이 객체의 속성으로 쓰일 수 있기 때문에 몇 가지 문제점이 나타났다. 예를 들면, `5`는 `"5"`로 형 강제 변환(coercion)이 일어나고, `{}`는 `[object Object]`가 되었다. 하지만 `Set`은 값의 타입을 강제로 변환하지 않는다. `5`와 `"5"`는 두 개의 다른 값이 된다.

```
const foo = new Set();

foo.add({})  // 빈 객체 추가
foo.add({})

console.log(foo.size) // 2
console.log(foo) // Set { {}, {} }

foo.add(10);
foo.add("10");
foo.add(10); // 이미 10이 있기 때문에 무시된다

console.log(foo); // Set { {}, {}, 10, "10" }
```

이와 같이 여러 개의 서로 다른 객체들을 set에 추가할 수 있다. 이 때 `Set`은 값을 추가할 때, `Object.is()`메소드를 이용해서 두 값을 비교한다.

```
Object.is(10,10) // true
Object.is(10, '10') // false
Object.is({}, {}) // false
```

### Set을 배열로 바꾸기

```
const foo = new Set(['Iphone', 'Galaxy'])
const fooInArray = [ ...foo ];
console.log(fooInArray) // ['Iphone', 'Galaxy']
```

### Method

  - add
  - size
  - has : set에 값이 존재하는지 확인. true / false 반환
  - delete(값) : set에서 값 제거
  - clear() : set에서 모든 값을 제거

만약 add를 통해 값을 추가할 때, 이미 그 값이 존재한다면 무시된다.


출처 : [HyeoKoo Alex Kwon](https://medium.com/@khwsc1/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-es6-set%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90-9b7294dfba99)