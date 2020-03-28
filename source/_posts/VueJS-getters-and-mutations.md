---
date: '2020/3/28 15:46:25'
tags:
  - VueJS
categories:
  - VueJS
thumbnail: ''
permalink: ''
title: Vuex - Getters and Mutations
---

getters and mutations

<!-- more -->


### Getters?

중앙 데이터 관리식 구조에서 발생하는 문제점 중 하나는 각 컴포넌트에서 Vuex의 데이터를 접근할 때 중복된 코드를 반복호출 하게 되는 것이다. 

```
// App.vue
computed: {
  doubleCounter() {
    return this.$store.state.counter * 2;
  }
},

// Child.vue
computed: {
  doubleCounter() {
    return this.$store.state.counter * 2;
  }
},
```

여러 컴포넌트에서 같은 로직을 비효율적으로 중복 사용하고 있다. 이 때, Vuex의 데이터(state) 변경을 각 컴포넌트에서 수행하는 게 아니라, Vuex에서 수행하도록 하고 각 컴포넌트에서 수행 로직을 호출하면, 코드 가독성도 올라가고 성능에서도 이점이 생긴다.

```
// store.js (Vuex)
getters : {
  doubleCounter : function(state){
    return state.counter * 2;
  }
},

// App.vue
computed : {
  doubleCounter(){
    return this.$store.getters.doubleCounter;
  }
},

// Child.vue
computed : {
  doubleCounter(){
    return this.$store.getters.doubleCounter;
  }
},
```

참고로, `computed`의 장점인Caching 효과는 단순히 state 값을 반환하는 것이 아니라, getters에 선언된 속성에서 filter(), reverse() 등의 추가적인 계산 로직이 들어갈 때 발휘된다.

#### mapGetters

Vuex에 내장된 helper 함수, mapGetter로 이미 위에서 한 번 가독성이 올라간 코드를 더 직관적이게 작성할 수 있다.

```
// App.vue
<div id="app">
  Parent counter : {{ parentCounter}}
</div>

// App.vue
import { mapGetters } from "vuex"

// ...
computed : mapGetters({
  parentCounter : 'getCounter' // getCounter는 Vuex의 getters에 선언된 속성 이름
}),
```

여기서 주의할 점은 위 방법은 컴포넌트 자체에서 사용할 computed 속성과 함께 사용할 수 없다는 점이다. 해결방안은 ES6의 문법 `...`을 사용하면 된다.

```
// App.vue

import { mapGetters } from "vuex"

computed : {
  ...mapGetters([
    'getCounter'
  ]),
  anotherCounter(){

  }
}
```
다만 `...` 문법을 사용하려면 Babel stage-2 라이브러리 설치 및 babel preset에 추가가 필요하다.


### Mutations?

Mutations란 Vuex의 데이터, 즉 state 값을 변경하는 로직들을 의미한다. Getters와 차이점은

  1. 인자를 받아 Vuex에 넘겨줄 수 있고
  2. computed가 아닌 methods에 등록

Actions와의 차이점은

  1. Mutations는 동기적 로직을 정의
  2. Actions는 비동기적 로직을 정의

**Mutations의 성격상 안에 정의한 로직들이 순차적으로 일어나야 각 컴포넌트의 반영 여부를 제대로 추적할 수가 있기 때문이다**

`commit`을 이용하여 state를 변경한다.

##### Mutations 등록

```
// store.js
export const store = new Vuex.Store({
  // ...
  mutations : {
    addCounter : function(state, payload){
      return state.counter++;
    }
  }
})
```

##### Mutations 사용

```
// App.vue
<div id="app">
  Parent counter : {{ parentCounter}} <br>
  <button @click="addCounter"></button>
</div>

// App.vue
methods : {
  addCounter(){
    // this.$store.state.counter++;
    this.$store.commit('addCounter');
  }
}
```

여기서 주목할 부분은 getters처럼 `this.$store.mutations.addCounter` 같은 접근이 불가능하고, commit을 이용하여 mutations 이벤트를 호출해야 한다는 점이다. 앞서 설명한 추적 가능한 상태 변화를 위해 프레임워크가 이렇게 구조화 되어 있는 것이다.

##### Mutations에 인자 값 넘기기

각 컴포넌트에서 Vuex의 state를 조작하는 데 필요한 특정 값들을 넘기고 싶을 때는 `commit()`에 두번째 인자를 추가한다.

```
this.$store.commit('addCounter', 10);
this.$store.commit('addCounter', {
  value : 10,
  arr : ["a", "b", "c"]
})
```

Vuex에서 아래와 같이 받을 수 있다.

```
mutations : {
  // payload가 { value : 10} 일 경우
  addCounter: function(state, payload){
    state.counter = payload.value;
  }
}
```
데이터 인자 명은 보통 `payload`를 많이 쓴다.


- 변경 된 state 값을 받아오는 **Getters**
- state 값을 변경하기 위한 메서드를 정의하는 **Mutations**


출처 : [Captain Pangyo](https://joshua1988.github.io/web-development/vuejs/vuex-getters-mutations/)
