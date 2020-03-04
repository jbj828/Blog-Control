---
date: '2020/3/4 12:46:25'
tags:
  - Docker
categories:
  - Docker
thumbnail: ''
permalink: ''
title: Making MySQL container with Docker
---

Docker로 MySQL 컨테이너 만들어 보기

<!-- more -->

__MySQL은 도커허브에 존재하는 이미지이기 때문에 즉시 MySQL이미지를 다운로드 받아 사용할 수 있다__

<br>
  
* `sudo apt install mysql-client-core-5.7` : mysql 설치

* `docker run -d -p 9876:3306 -e MYSQL_ROOT_PASSWORD=password mysql:5.6`  :  9876포트와 mysql의 기본포트인 3306포트 연결. 환경변수로 mysql의 루트 패스워드를 패스워드로 설정. mysql 5.6 이미지를 다운로드 받아서 실행까지 시행. 
* `docker ps -a` 
* `docker exec -it 컨테이너아이디 /bin/bash`  : 컨테이너 접속 위해 exec명령 이용. bash명령을 시행해 해당 컨테이너에 접속한 것과 같은 효과
* `mysql -u root -p`  : mysql 실행 및 접속
* 패스워드는 `password` 그대로 복사 붙여넣기

<br>

##### Database 생성

* `CREATE DATABASE TEST;`
* `SHOW DATABASES;`
* `exit`
* `exit`

<br>

##### Docker 컨테이너의 세부정보 확인 및 컨테이너에 포함되어 있는 mysql 접속

* `docker inspect 컨테이너아이디`
* "IPAddress" 찾기
* `mysql -u root -p --host 아이피어드레스 --port 3306`

<br>

* `SHOW DATABASES;`  : 이전에 만든 test 있는지 확인

<br>

* `mysql -u root -p --host 127.0.0.1 --port 9876` : 이 방법으로도 mysql에 접속 가능

<br>

도커 컨테이너는 언제든지 제거될 수 있기 때문에 일반적으로 도커컨테이너를 mysql 서버로 사용 안함. 컨테이너와 같이 일시적인 서버로서 mysql을 사용하지 않음. 그래서 일반적으로 AWS RDS 같은 데이터베이스 기능을 많이 이용.

<br>

__Mysql 접속 이후 관리자 역할로 하나으 user 만들기__

* `CREATE USER 'test'@'%' IDENTIFIED BY 'password';`
* `GRANT ALL PRIVILEGES ON *.* TO 'test'@'%';` : 해당 유저에게 권한을 준다. test계정에 권한을 주고 외부에서 접속할 수 있도록 설정
* `FLUSH PRIVILEGES;`
* `exit`

<br>

* `docker restart 컨테이너아이디`

<br>

* AWS에서 포트 9876으로 열어준다.
* 'IPv4 퍼블릭 IP' 주소 복사해서 데이터베이스 접속 앱(HeidiSQL 등) 이용





<br>
출처 : 동빈나 youtube


