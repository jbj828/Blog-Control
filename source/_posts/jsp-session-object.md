---
date: '2020/1/8 23:36:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: JSP Session object
---

## Session Object

1. JSP session is created once for user's browser session unique for this user.
2. Commonly used when you need to keep track of the user's actions. ex)shopping cart, online banking.

<!-- excerpt -->

* cookie : 웹 브라우저에 사용자의 상태를 유지하기 위한 정보 저장
* session : 웹 서버쪽의 웹 컨테이너에 상태를 유지하기 위한 정보 저장

### session의 속성

* 세션 설정은 세션 객체의 setAttribute() 메서드 사용
* 세션 저장하여 유지할 수 있도록 함
{% codeblock lang:java %}
session.setAttribute("name", "value");
{% endcodeblock %}

* 세션의 속성을 사용하려면 getAttribute() 메서드 사용
* getAttribute()사용 시 형 변환을 해야함 - 기본 Object 타입으로
{% codeblock lang:java %}
String id = (String) session.getAttribute("id");
{% endcodeblock %}

