---
date: '2020/3/20 13:46:25'
tags:
  - NodeJS
categories:
  - NodeJS
thumbnail: ''
permalink: ''
title: JSON Web Token
---

token

<!-- more -->

### Token 기반 인증에 대한 소개

  1. **Stateless** Server
     상태를 유지하지 않음. 상태 정보를 저장하지 않으면 서버는 클라이언트 측에서 들어오는 요청만으로만 작업을 처리한다.이렇게 상태가 없는 경우 클라이언트와 서버의 연결고리가 없기 때문에 서버의 확장성(Scalability)가 높아진다.

  2. Best for Mobile Application
      Android/iOS 모바일 어플리케이션을 개발한다면, 안전한 API를 만들기 위해서 쿠키 같은 인증 시스템은 이상적이지 않다(쿠키 컨테이너를 사용해야 함). 토큰 기반 인증 도입하면, 간단하게 이 번거로움을 해결 할 수 있다
    
  3. 인증정보를 다른 어플리케이션으로 전달
      대표적 예로 OAuth가 있다. 페이스북/구글 같은 소셜 계정들을 이용하여 다른 웹 서비스에서도 로그인 할 수 있게 할 수 있다.

  4. 보안
      토큰 기반 인증 시스템을 사용하여 어플리케이션 보안 높일 수 있다.

### 토큰 기반 시스템의 작동 원리

1. 유저가 아이디와 비밀번호로 `로그인`
2. 서버측에서 해당 `계정정보를 검증`
3. 계정정보가 정확하다면, 서버측에서 유저에게 `signed토큰을 발급`(signed의 의미는 해당 토큰이 서버에서 정상적으로 발급된 토큰임을 증명하는 signature를 지니고 있다는 것)
4. 클라이언트 측에서 전달받은 `토큰을 저장`해두고, 서버에 요청을 할 때마다, 해당 `토큰을 함께 서버에 전달`
5. 서버는 `토큰 검증`하고, `요청에 응답`


## JSON Web Token

JWT은 웹표준으로서 두 개체에서 JSON 객체를 사용하여 가볍고 자가수용적인(self-contained)방식으로 정보를 안전성 있게 전달해줍니다.

__자가 수용적(self contained)__
  JWT는 필요한 모든 정보를 자체적으로 지니고 있다. JWT 시스템에서 발급된 토큰은, 토큰에 대한 기본 정보, 전달 할 정보(로그인 시스템에서는 유저 정보) 그리고 토큰이 검증 됐다는 것을 증명해주는 signature를 포함하고 있다.

#### JWT의 생김새

```
aaaaaaaaaaaaaa.bbbbbbbbbbbbbbb.cccccccccccccccc
 header(헤더)      payload(내용)   signature(서명)
```


출처 : [Veloplert.Log](https://velopert.com/) - 공부목적으로 사용했습니다

