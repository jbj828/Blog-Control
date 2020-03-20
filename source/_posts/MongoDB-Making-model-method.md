---
date: '2020/3/20 15:46:25'
tags:
  - MongoDB
categories:
  - MongoDB
thumbnail: ''
permalink: ''
title: Making Model Method(mongoose)
---

Making model method


<!-- more -->

보통 API 컨트롤러 파일에서 데이터 모델의 내장함수들에 직접 접근하여 데이터를 생성하고 조회를 한다.

이번엔 데이터 모델에 임의 메소드, 쿼리 헬퍼를 만들어서 데이터 작업을 좀 더 용이하게 하는 방법을 알아본다.

모델 메소드는 두 종류로 만들 수 있다. `.statics` 와 `.methods` 이다. 각 종류는 서로 가리키는 `this` 값이 다르다. 전자의 경우 모델 자체를 가리키고, 후자의 경우 데이터 인스턴스를 가리킨다. 

### static 메소드

```
// Check the user's email and password
userSchema.statics.findByCredentials = async function (email, password) {
    const user = await User.findOne({ email })

    if (!user) {
        throw new Error('Unable to login')
    }

    const isMatch = await bcrypt.compare(password, user.password)

    if (!isMatch) {
        throw new Error('Unable to login')
    }
    return user;
}
```

### 인스턴스 메소드

```
// Generate the token and save on the database
userSchema.methods.generateAuthToken = async function () {
    const user = this
    const token = jwt.sign({ _id: user._id.toString }, 'studyNodeJs')

    user.tokens = user.tokens.concat({ token })
    await user.save();

    return token;
}
```

메소드를 만들 땐, 스키마를 모델화 하기 전에, `.statics` 혹은 `.methods`를 사용하여 정의를 해주어야 한다.

이렇게 메소드를 만들면, 우리가 원하는 작업마다 이름을 붙여줄 수 있게 되고 코드를 분리시킬 수 있어 가독성도 높아진다. 쿼리를 작성할 때 데이터 구조를 확인하기 위하여 컨트롤러 파일과 모델 파일을 동시에 볼 필요도 없어서 편해진다. 


출처 : [backend](https://backend-intro.vlpt.us/) 