---
date: '2020/1/16 23:30:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: 제약조건
---

* 제약조건
  * 컬럼에 저장 될 데이터의 조건을 설정하는 것
  * 제약 조건을 설정하면 조건에 위배되는 데이터는 저장할 수 없다.
<!-- more -->
  * 데이터베이스 내의 테이블은 여러 개발자가 사용하므로 제약 조건 설정이 중요하다.

  * primary key : 컬럼에 중복으로 데이터를 저장할 수 없으며, null 값을 허용하지 않는다. 주로 각 로우를 구분하기 위한 유일한 값을 저장하는 컬럼에 사용한다. 기본키라고도 부른다.

  * foreign key : 특정 테이블의 primary key 컬럼에 저장되어 있는 값만 저장할 수 있도록 한다. 흔히 참조키, 외래키라고 부르며 지정된 테이블의 기본키 컬럼을 참조하여 참조하는 기본키 컬럼에 저장되어 있는 값만 저장할 수 있다. null 값을 허용한다.

  * not null : 컬럼에 null 값을 저장할 수 없으며 쿼리문을 통해 반드시 값이 지정되어야 한다.
```
create table test_table10(
data1 int not null
);

insert into test_table10 (data1) value (1);
insert into test_table10 (data1) value (2);
insert into test_table10 (data1) value (3);

select * from test_table10;

insert into test_table10 (data1) value (null); -- 에러메시지 뜸


create table test_table20(
data1 int,
data2 int not null,
constraint pk1 primary key(data1)
);

insert into test_table20 (data1, data2) values (10, 100);
insert into test_table20 (data1, data2) values (20, 200);
insert into test_table20 (data1, data2) values (30, 300);

select * from test_table20;

insert into test_table20 (data1, data2) values (10, 100); -- 에러메시지 뜸
insert into test_table20 (data1, data2) values (10, null); -- 에러메시지 뜸


create table test_table30(
data1 int,
data2 int,
constraint pk2 primary key (data1),
constraint fk2 foreign key (data2) references test_table20 (data1)
);

select * from test_table20;
insert into test_table30 (data1, data2) values (1,10);

insert into test_table30 (data1, data2) values (1, 40); -- 에러메시지 (data1에는 40 이라는 값이 없음)
insert into test_table30 (data1, data2) values (2, null);
insert into test_table30 (data1) values (6);

select * from test_table30;
```

  * unique : 컬럼에 중복된 값을 저장할 수 없다. null은 허용한다

  * check : 값의 범위나 종류를 지정하여 조건에 맞는 값만 저장할 수 있도록 한다. check 제약조건은 mysql에서 지원하지 않는다.

  * default : null이 들어올 경우 기본 설정되는 값을 지정한다. default를 설정할 경우 컬럼에 null을 저장할 수 없다.

```
create table test_table40(
data1 int,
data2 int not null,
constraint uk1 unique (data1),
constraint uk2 unique (data2)
);

insert into test_table40 (data1, data2) values (1, 10);
insert into test_table40 (data1, data2) values (2, 20);
select * from test_table40;
insert into test_table40 (data1, data2) values (1, 30); -- error
insert into test_table40 (data1, data2) values (3, 10); -- error

insert into test_table40 (data1, data2) values (null, 40);
insert into test_table40 (data1, data2) values (null, 50);

select * from test_table40;


create table test_table50(
data1 int not null,
data2 int not null,
constraint chk1 check (data1 > 10), -- 10보다 큰 것만 넣어라
constraint chk2 check (data2 in(10, 20, 30)) -- 10,20,30 만 넣어라
);

create table test_table60(
data1 int not null default 1,
data2 int not null default 10
);
insert into test_table60 (data1, data2) values (null, null);

select * from test_table60; -- null 지정한건 생략해버림

insert into test_table60 (data1) values (100); -- 100 10 
insert into test_table60 (data2) values (200); -- 1 200
select * from test_table60; 
```
