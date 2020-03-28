---
date: '2020/3/28 18:46:25'
tags:
  - VueJS
categories:
  - VueJS
thumbnail: ''
permalink: ''
title: Vuex - Actions
---

actions

<!-- more -->

### Actions?

Mutations에는 순차적인 로직들만 선언하고 Actions에는 비순차적 또는 비동기 처리 로직들을 선언한다. 

Mutations의 역할은 State 관리이다. 상태관리 자체는 한 데이터에 대해 여러 개의 컴포넌트가 관여하는 것을 효율적으로 관리하기 위한 것이다. 하지만 Mutations에 비동기 처리 로직들이 포함되면 같은 값에 대해 여러 개의 컴포넌트에서 변경을 요청했을 때, 변경 순서 파악이 어렵게 된다. 

이 문제를 사전에 차단하기 위해 비동기 처리 로직은 Actions로, 동기 처리 로직은 Mutations로  나눠서 구현한다.

따라서, `setTimeout()`이나 서버와의 http 통신 처리 같이 결과를 받아올 타이밍이 예측되지 않은 로직은 Actions에 선언한다.

##### Actions 등록

```
// store.js
export const store = new Vuex.Store({
  // ...
  mutations : {
    addCounter : function(state, payload){
      return state.counter++;
    }
  },
  actions : {
    addCounter : function(context){
      // commit의 대상인 addCounter는 mutations의 메서드를 의미
      return context.commit('addCounter'); 
    }
  }
})
```

상태가 변화하는 걸 추적하기 위해 actions는 결국 mutations의 메서드를 호출(commit)하는 구조가 된다.

```
// store.js
export const store = new Vuex.Store({
  actions : {
    getServerData : function(context){
      return axios.get("sample.json").then(function(){
        //...
      })
    },
    delayFewMinutes : function(context){
      return setTimeout(function(){
        commit('addCounter');
      }, 1000)
    }
  }
})
```
HTTP get 요청이나 setTimeout과 같은 비동기 처리 로직들은 actions에 선언해준다.

##### Actions 사용

앞에선 mutations를 이용하여 counter를 하나씩 늘렸다. 이번엔 actions를 이용해보자. actions를 호출할 때는 아래와 같이 **dispatch()**를 이용한다

```
// App.vue
methods : {
  //Mutations를 이용할 때
  addCounter(){
    this.$store.commit('addCounter');
  }
  // Actions를 이용할 때
  addCounter(){
    this.$store.dispatch('addCounter');
  }
}
```

##### Actions에 인자 값 넘기기

```
<button @click="asyncIncrement({by : 50, duration: 500})">Increment</button>
```

```
export const store = new Vuex.Store({
  actions : {
    // payload는 일반적으로 사용하는 인자 명
    asyncIncrement : function(context, payload){
      return setTimeout(function(){
        context.commit('increment', payload.by);
      }, payload.duration);
    }
  }
})
```



출처 : [Captain Pangyo](https://joshua1988.github.io/web-development/vuejs/vuex-getters-mutations/)

