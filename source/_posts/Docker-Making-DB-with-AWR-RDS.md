---
date: '2020/3/4 15:46:25'
tags:
  - Docker
  - AWS
categories:
  - Docker
  - AWS
thumbnail: ''
permalink: ''
title: Making DB with AWS RDS
---

AWS RDS를 이용한 데이터베이스 구축

<!-- more -->

__AWS RDS를 이용해 한 번 기록 된 데이터를 컨테이너가 꺼지더라도 남아있도록 하기 위해 이용__

<br>

__한글 데이터 삽입이 가능한 데이터베이스를 위해 한글 설정 관련 파라미터 그룹 생성__

* RDS에서 파라미터 생성
* `char` 검색해서 전부 utf8로 바꿈
* `collation` 검색 -> 전부 utf8_general_ci

<br>

* 데이터베이스 -> 연결 & 보안 ->　vpc 보안그룹 링크 들어감 -> 인바운드 -> 편집
* 실습이기 때문에 언제 어디서나 접속가능하게 만든다
    * 0.0.0.0/0
* 이렇게 하면 접속주소만 알면 누구나 접속가능하게 됨

<br>

* 연결&보안 -> 엔드포인트(해당 mysql에 접속하기 위한 접속주소) 복사
* php file에서 호스트 주소로 엔드포인트 붙여넣기
* 사용자 이름도 mysql 내용대로 수정
* 포트번호도 3306으로(mysql 포트번호)

<br>

* aws ec2안에 설치된 mysql컨테이너는 지워도 됨
* `docker rm -f 컨테이너아이디`



<br>
출처 : 동빈나 youtube

