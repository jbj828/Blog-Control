---
date: '2020/3/21 15:46:25'
tags:
  - MongoDB
categories:
  - MongoDB
thumbnail: ''
permalink: ''
title: Populate, Virtual
---

populate

<!-- more -->

### Populate

- 몽구스의 편리한 기능 중 하나인 populate
- 몽고DB를 사용하다보면 하나의 다큐먼트가 다른 다큐먼트의 ObjectId를 쓰는 경우가 있다. 그럴 때 그 ObjectId를 실제 객체로 치환하는 작업이 필요하다.
- 즉 populate는 ObjectId에 해당하는 값과 객체를 치환해주는 역할을 해준다.


```
const Task = mongoose.model('Task', {
 owner: {
 type: mongoose.Schema.Types.ObjectId,
 required: true,
 ref: 'User'
 }
})
```

`ref`에 해당 ObjectId가 속해있는 모델을 넣어준다. 자기자신을 가리켜도 되고 다른 컬렉션 모델이어도 상관없다.


You can fetch the owner of a given task.
```
const task = await Task.findById('5c2e505a3253e18a43e612e6')
await task.populate('owner').execPopulate()
console.log(task.owner)
```

결과적으로 **ObjectId가 실제 객체로 치환**된다.


 populate는 자바스크립트 단에서 합쳐주는 것이지 JOIN처럼 DB 자체에서 합쳐주는 것이 아니다. 따라서 성능이 그렇게 좋지는 않습니다. 특히 populate가 중첩되면 성능 문제가 생길 확률이 커집니다.

<br>

### Virtual

다큐먼트에는 없지만 객체에는 있는 가상의 필드를 만들어준다.

```
userSchema.virtual('detail').get(function(){
  return `I am ${this.nickname} and birthday is ${this.birth.toLocaleString()}.`
})
```

스키마에 virtual를 붙이면 users 컬렉션을 조회할 때 `{email: ..., password: ...., detail: ...}` 처럼 detail 필드가 생긴다. 그리고 get 메소드 안에 넣어준 함수의 return 값이 들어있다. 기존 필드들을 활용해서 새로운 가상 필드를 만드는 것이다.





 출처 : [zeroCho TV](https://www.zerocho.com/category/MongoDB/post/59a66f8372262500184b5363)