---
date: '2020/3/27 15:46:25'
tags:
  - VueJS
categories:
  - VueJS
thumbnail: ''
permalink: ''
title: Structure of Vuex
---

structure of vuex

<!-- more -->

모든 Vuex 애플리케이션의 중심에는 `store`가 있다. `store`는 기본적으로 애플리케이션 상태를 보유하고 있는 컨테이너이다. Vuex 저장소가 일반 전역 개체와 두 가지 다른 점이 있다.

  1. Vuex store는 반응형이다. Vue 컴포넌트는 상태를 검색할 때 저장소의 상태가 변경되면 효율적으로 대응하고 업데이트 한다.
  2. 저장소의 상태를 직접 변경할 수 없다. **커밋을 이용한 변이**만 가능하다. 이렇게 하면 모든 상태에 대한 추적이 가능해져 앱을 사용해 툴을 더 잘 이해할 수 있다.

```
//모듈 시스템 사용할 경우 Vue.use(Vuex)를 먼저 호출해야 한다

const store = new Vuex.store({
  state : {
    count : 0
  },
  mutations : {
    increment(state){
      state.count++
    }
  }
})
```

이제 state 객체에 `store.state`로 접근하여 `store.commit` 메소드로 상태 변경을 트리거 할 수 있다.

```
store.commit('increment')

console.log(store.state.count) // -> 1
```

다시 말해, `store.state.count`를 직접 변경하는 대신 변이를 수행하는 이유는 명시적으로 추적을 하기 때문이다. 

컴포넌트 안에서 저장소 상태를 사용하는 것은 단순히 계산된 속성 내에서 상태를 반환하는 것이다. 변경을 트리거하는 것은 컴포넌트 메소드에서 변경을 커밋하는 것을 의미한다.


**가장 기본적인 Vuex 카운터 앱**
```
<div id="app">
  <p>{{ count }}</p>
  <p>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
  </p>
</div>
```

```
// make sure to call Vue.use(Vuex) if using a module system

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
  	increment: state => state.count++,
    decrement: state => state.count--
  }
})

new Vue({
  el: '#app',
  computed: {
    count () {
	    return store.state.count
    }
  },
  methods: {
    increment () {
      store.commit('increment')
    },
    decrement () {
    	store.commit('decrement')
    }
  }
})
```



출처 : [Vuex](https://vuex.vuejs.org/kr/guide/)