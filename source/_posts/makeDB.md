---
date: '2020/1/15 15:46:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: Making DataBase
---

* 데이터 베이스 만들기
  * 데이터베이스 생성은 create database 구문을 사용
  * create database 이름
<!-- more -->
  * 생성한 데이터베이스는 use 문을 이용하여 선택해야 한다
  * utf-8 인코딩 타입의 한글을 저장하려면 다음과 같이 언어 타입을 지정해준다
    * create database 이름
      character set = 'utf8'
      collate = 'utf8_general_ci';

* 테이블 만들기
  * 데이터베이스를 선택 후 create table 명령문을 이용해 테이블 생성
  * create table 이름(
    컬럼이름 자료형 제약조건,
    컬럼이름 자료형 제약조건,
    );

    * char(n) : 고정길이 문자열(속도빠름)
    * varchar(n) : 가변길이 문자열
    * int(n) : 정수형 타입
    * bigint(n) : 정수형 타입
    * float(n,m) : 부동소수점 타입
    * double(n,m) : 부동소수점 타입
    * date : 날짜
    * time : 시간
    * datetime : 날짜와 시간
```
create database test_db
character set = 'utf8'
collate = 'utf8_general_ci';

use test_db;

create table test_table1(
data1 int(10),
data2 varchar(10),
data3 float(10,2)
);

desc test_table1;
```

  * 서브쿼리를 이용한 테이블 생성하기
    * select문을 통해 가져온 결과를 이용해 테이블을 생성할 때 사용한다
    * create table 테이블명
      as
      select문

```
use employees;

select * from departments;

create table dept1
as
select * from departments;

desc dept1;

select * from dept1;

-- 구조는 생성하지만 데이터는 넣지 않을 때 
create table dept2
as
select * from departments where 1=0;

desc dept2;

select * from dept2;

```

* 데이터 저장하기
  * insert 문을 활용하면 데이터를 저장할 수 있다
  * 이 때, 로우 단위로 저장된다
  * insert into 테이블명 (컬럼명) values (값)
  * insert into 테이블명 values (값)
  * 컬럼에 저장될 값을 지정하지 않으면 null이 저장된다.
  
```
show databases;

use test_db;

show tables;

desc test_table1;

insert into test_table1 (data1, data2, data3) values (100, '문자열1', 12.2);

select * from test_table1;

insert into test_table1 value (300, "another", 12.4);

select * from test_table1;

create table test_table2
as
select * from test_table1 where 1=0;

desc test_table2;
select * from test_table2;

insert into test_table2
select data1, data2, data3 from test_table1;

select * from test_table2;
```

* 데이터 수정하기
  * update 문을 활용하면 데이터를 수정할 수 있다
  * update 테이블명 set 컬럼명=값, 컬럼명=값 where 조건식

```
update test_table1 set data2="neence", data3=77.77;
select * from test_table1;

select * from test_table2;
update test_table2 set data1="100", data2="newWord"
where data1=700;
select * from test_table2;
```

* 데이터 삭제하기
  * delete 문을 활용하면 데이터를 삭제할 수 있다.
  * delete from 테이블명 where 조건식

```
delete from test_table1;
select * from test_table1;

delete from test_table2 where data1=100;
select * from test_table2;
```