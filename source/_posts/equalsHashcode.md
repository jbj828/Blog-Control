---
date: '2020/1/6 20:11:25'
tags:
  - java
categories:
  - Java
thumbnail: ''
permalink: ''
title: equals()메소드와 hashcode()메소드
---

## equals() 메서드와 비교연산자 == 의 차이

{% codeblock lang:java %}
String a = new String("java");
String b = new String("java");

a == b  //false
a.equals(b)  //true
{% endcodeblock %}
equals() 메서드는 는 값의 동등성만 확인한다.

## hashcode()

"return a hashcode value for the object.
This method is supported for the benefit of hash tables 
such as those provided by HashMap."

Object 클래스에 있는 메서드

HashTable 과 HashMap은 hashcode() 메서드를 이용해서 객체를 저장하는 다른 
도구들(ex ArrayList)에 비해 장점을 가진다
=> key의 hashcode()를 통해 value 값을 더 쉽게 찾을 수 있다. 
(보통 key 값엔 어떤 객체든 올 수 있다. 다양한 종류의 객체를 찾는 것보다 int 값(hashcode)를 찾는게 편하다)


일반 class를 정의할 때 hashcode 메서드는 오버라이드하여 변경을 안했기 때문에 Object 클래스에서 정의 된
그대로의 메서드

하지만 String의 경우 hashcode가 주소값과 관련이 없다.
String 클래스의 hashcode는 오버라이드 과정에서 새롭게 정의된다.
=> 같은 문자열은 같은 hashcode 값 가짐.
왜냐하면 hashcode를 활용해서 Map이나 Set에 저장 된 key 값 찾아야 되는데 같은 값인데도 불구하고 hashcode 값이 다르면 제대로 못찾기 때문에

hashcode 메서드 재정의 : 같은 String 객체(equals() 리턴값 true) => hashcode 같아지도록 만듦



### equals(object) 메서드가 true이면 두 객체의 hashcode 값 같아야 한다.
### equals(object) 메서드가 false이면 두 객체의 hashcode 가 꼭 다를 필요는 없다.
### 하지만 서로 다른 hashcode 값이 나오면 hashTable의 성능이 향상될 수 있다는 점은 알아야 한다.





<!-- excerpt -->
<!-- toc -->