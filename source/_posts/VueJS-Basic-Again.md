---
date: '2020/4/13 15:46:25'
tags:
  - VueJS
categories:
  - VueJS
thumbnail: ''
permalink: ''
title: Using VueJS to Interact with DOM
---

Using VueJS to Interact with DOM

<!-- more -->

#### Modifying an Event with Event Modifiers

```
<p v-on:mousemove="updateCoordinates">
  Coordinates : {{ x }} / {{ y }}
   - <span v-on:mousemove.stop="">Dead Spot</span>
  </p>
```

Using `.stop`, we have same effect like `event.preventDefault()` or `event.stopPropagation()`

#### Listening to KeyBoard Events

```
 <input type="text" v-on:keyup.enter.space="alertMe">
 ```

You'll get the Alert Message when press the keyboard `enter` or `space`

```
<input type="text" v-on:keydown="value = $event.target.value">
<p>{{ value }}</p>
```

#### Two-way Binding

`v-model`

데이터가 양방향으로 흐르게 해주는 것. 즉, 데이터에 있는 값이 뷰에 나타나고, 이 뷰의 값이 바뀌면 데이터의 값도 바뀐다.

```
<input type="text" v-model="name">
 <p>{{name}}</p>
```

#### Computed Properties

computed 속성 대신 메소드와 같은 함수를 정의할 수 있다. 최종 결과는 두 가지 접근 방식이 동일하다. 차이점은 computed 속성은 종속 대상을 따라 저장(캐싱)
된다. computed 속성은 해당 속성이 종속된 대상이 변경될 때만 함수를 실행한다. 즉 `message`가 변경되지 않는 한, computed 속성을 여러 번 요청해도 계산을 다시 하지 않고 계산되어 있던 결과를 즉시 반환한다.

이에 비해 메소드를 호출하면 렌더링을 할 때마다 함수를 실행한다.

캐싱이 왜 필요할까? 계산에 시간이 많이 걸리는 computed 속성인 A가 있다고 가정하자. 여기에 더해 A에 의존하는 다른 computed 속성값도 있을 수 있다. 캐싱을 하지 않으면 A의 getter 함수를 꼭 필요한 것보다 더 많이 실행하게 된다. 캐싱을 원하지 않을 경우 메소드를 사용하면 된다.

#### Watch Properties

`watch` 옵션은 데이터 변경에 반응하는 보다 일반적인 방법을 제공한다. 데이터 변경에 대한 응답으로 비동기식 또는 시간이 많이 소요되는 조작을 수행하려는 경우에 가장 유용하다.