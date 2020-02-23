---
date: '2020/2/23 15:46:25'
tags:
  - language
categories:
  - Language
thumbnail: ''
permalink: ''
title: Regular Expression
---

regular expression

<!-- more -->

### Regular Expression

  * 정규표현식(正規表現式, Regular Expression)은 문자열을 처리하는 방법 중의 하나로 특정한 조건의 문자를 '검색'하거나 '치환'하는 과정을 매우 간편하게 처리 할 수 있도록 하는 수단이다.


<br>

__정규표현식의 특징__

  * Case sensitive(대소문자 구분) 
      `options : "i"` 하면 대소문자 구분 없이 검색 가능

<br>

__정규표현식의 패턴__

  * ^ : Character ^ matches the beginning of the line.
  * $ : Dollar sign matches the end of the line
  * \ : Escaping the pattern to the normal text.
      * `\$` : this means normal text of "$"
  * . : Point . mathces any character   
  * [] : Insid square brackets "[]" a list of characters can be provided. The expression matches if any of these characters is found. The order of character is insignificant.
  * [x-y] : A range of characters can be specified with [-] syntax. ex) [c-k] : c부터 k까지 모두 선택
  * [^ ] : If a character class starts with ^, then specified characters will not be selected.

__서브 패턴__

  * (on|ues|rida) : Alternating text can be enclosed in parentheses and alternatives separated with |
  

  
<br>
출처 : 생활코딩

