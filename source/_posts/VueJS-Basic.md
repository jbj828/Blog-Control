---
date: '2020/3/25 22:46:25'
tags:
  - VueJS
categories:
  - VueJS
thumbnail: ''
permalink: ''
title: The basic of VueJS
---

basic of vueJS

<!-- more -->

### What is VueJS?

MVVM 패턴의 ViewModel 레이어에 해당하는 화면단 라이브러리

  - 데이터 바인딩과 화면 단위를 컴포넌트 형태로 제공하며, 관련 API를 지원한는 데 궁극적 목적이 있다.
  - 양방향 데이터 바인딩 제공
  - 컴포넌트 간 통신은 단방향 데이터 흐름(부모 -> 자식)

{% asset_img "vue.png" 500 300 "Vue" %}

### MVVM Pattern?

Backend 로직과 Client의 마크업 & 데이터 표현단을 분리하기 위한 구조로 전통적인 MVC 패턴의 방식에서 기인하였다. 간단하게 생각해서 화면 앞단의 화면 동작 관련 로직과 뒷단의 DB 데이터 처리 및 서버 로직을 분리하고, 뒷단에서 넘어온 데이터를 Model에 담아 View로 넘겨주는 중간 지점이라고 보면 된다.


출처 : [Captain Pangyo](https://joshua1988.github.io/)