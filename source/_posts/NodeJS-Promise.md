---
date: '2020/3/15 20:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: Promise
---

promise

<!-- more -->


출처 : [Captain Pangyo](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
공부목적을 위해 이용했습니다.

### Promise

* “A promise is an object that may produce a single value some time in the future”

* 프로미스는 자바스크립트 비동기 처리에 사용되는 객체입니다. 

### Why we need it?

* 프로미스는 주로 서버에서 받아온 데이터를 화면에 표시할 때 사용한다. 일반적으로 웹 애플리케이션을 구현할 때 서버에서 데이터를 요청하고 받아오기 위해 사용한다.

비동기 처리를 위해 콜백 함수를 사용한 경우
```
const doWorkCallback = (callback) => {
    setTimeout(() => {
        // callback('Error', undefined);
        callback(undefined, [1, 3, 4])
    }, 2000);
}

doWorkCallback((error, result) => {
    if (error) {
        return console.log(error);
    }

    console.log(result);
})
```

비동기 처리를 위해 Promise API를 사용한 경우
```
const doWorkPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve([2, 3, 4]);
        reject('Thing went wrong!')
    }, 2000)
})


doWorkPromise.then((result) => {
    console.log('Success', result)
}).catch((error) => {
    console.log('Error', error)
})
```

### Promise의 3가지 상태(states)

여기서 말하는 상태란 프로미스의 처리 과정을 의미한다. `new Promise()`로 프로미스를 생성하고 종료될 때까지 3가지 상태를 갖는다.

  * Pending(대기) : 비동기 처리 로직이 아직 완료되지 않은 상태
  * Fulfilled(이행) : 비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태
  * Rejected(실패) : 비동기 처리가 실패하거나 오류가 발생한 상태

#### Pending

먼저 `new Promise()` 메서드를 호출하면 대기(Pending) 상태가 된다.

```
new Promise();
```

`new Promise()` 메서드를 호출할 때 콜백 함수를 선언할 수 있고, 콜백 함수의 인자는 `resolve`, `reject`입니다.

```
new Promise(function(resolve, reject){

});
```

#### Fulfilled(이행)

여기서 콜백 함수의 인자 `resolve`를 아래와 같이 실행하면 이행(Fulfilled) 상태가 됩니다.

```
new Promise(function(resolve, reject){
  resolve();
})
```

그리고 이행 상태가 되면 아래와 같이 `then()`을 이용하여 처리 결과 값을 받을 수 있습니다.

```
function getData(){
  return new Promise(function(resolve, reject){
    var data = 100;
    resolve(data);
  })
}

// resolve()의 결과 값 data를 resolveData로 받음
getData().then(function(resolveData){
  console.log(resolveData); // 100
})
```

#### Rejected(실패)

`new Promise()`로 프로미스 객체를 생성하면 콜백 함수 인자로 `resolve`와 `reject`를 사용할 수 있다. 여기서 `reject`를 아래와 같이 호출하면 실패(Rejected) 상태가 된다

```
new Promise(function(resolve, reject){
  reject();
})
```

그리고 실패 상태가 되면 실패한 이유(실패 처리의 결과 값)를 `catch()`로 받을 수 있다.ss

```
function getData(){
  return new Promise(function(resolve, reject){
    reject(new Error("Request is failed"))
  })
}

// reject()의 결과 값 Error를 err에 받음
getData().then().catch(function(err){
  console.log(err); // Error: Request is failed
})
```

{% asset_img "promise.PNG" 500 300 "promise" %}

프로미스 처리 흐름(출처 : MDN)


```
function getData() {
  return new Promise(function(resolve, reject) {
    $.get('url 주소/products/1', function(response) {
      if (response) {
        resolve(response);
      }
      reject(new Error("Request is failed"));
    });
  });
}

// 위 $.get() 호출 결과에 따라 'response' 또는 'Error' 출력
getData().then(function(data) {
  console.log(data); // response 값 출력
}).catch(function(err) {
  console.error(err); // Error 출력
});
```

위 코드는 서버에서 제대로 응답을 받아오면 resolve() 메서드를 호출하고, 응답이 없으면 reject() 메서드를 호출하는 예제입니다. 호출된 메서드에 따라 then()이나 catch()로 분기하여 응답 결과 또는 오류를 출력합니다.
