---
date: '2020/1/16 23:46:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: sequence, limit, view
---

* sequence
  * 로우를 추가할 때 자동으로 증가하는 값이 저장되는 것을 시퀀스라고 부른다
  * 시퀀스는 데이터베이스 별 사용하는 방법이 다르므로 반드시 파악
 <!-- more -->
  * mysql은 auto_increment 키워드를 설정해주면 된다.
  * 데이터를 insert 할 때 auto_increment를 설정한 컬럼은 제외한다

```
create table test_table100(
data1 int auto_increment,
data2 int not null,
data3 int not null,
constraint pk1 primary key (data1)
);

insert into test_table100 (data2, data3) values (100, 200);
insert into test_table100 (data2, data3) values (101, 201);
insert into test_table100 (data2, data3) values (102, 202);

select * from test_table100;
```

* limit
  * select 해서 가져온 로우에서 원하는 범위의 로우만 가지고 올 때 사용한다.
  * 게시판 등에서 사용하는 페이징 기법을 구현할 때 사용한다.
  * 데이터베이스 별 구현 방법 다르다
  * select 문 limit 시작인덱스, 개수

```
use employees;
select * from employees;

select * from employees order by emp_no;
select * from employees order by emp_no limit 0, 10;
select * from employees order by emp_no limit 10, 10;
```

* view
  * view 는 가상의 테이블을 의미한다
  * 두 개 이상의 테이블을 조인하거나 서브쿼리를 사용하는 select 문은 쿼리문이 복잡해지게 되는데 이를 매번 사용하게 되면 개발자의 불편함이 따르게 된다.
  * 이 때 조인이나 서브쿼리를 사용해 얻어진 결과를 뷰로 만들어 놓으면 개발자는 뷰를 통해 결과를 얻어올 수 있다.
  * 사실 뷰는 select문을 통해 얻어진 결과를 가지고 있는 것이 아니라 select문 자체를 가지고 있어 뷰를 select하면 이전에 사용한 쿼리문이 실행되어 결과를 가져오게 된다.

  * create view 뷰이름 as select 쿼리문
  * drop view 뷰이름

```
create table test_table4000(
data1 int,
data2 int not null,
constraint pk1 primary key (data1)
);

create table test_table5000(
data1 int not null,
data3 int not null,
constraint fk10 foreign key (data1) references test_table4000 (data1)
);

insert into test_table4000 (data1, data2) values (1,10);
insert into test_table4000 (data1, data2) values (2,20);
insert into test_table4000 (data1, data2) values (3,30);

insert into test_table5000 (data1, data3) values (1, 100);
insert into test_table5000 (data1, data3) values (2, 200);
insert into test_table5000 (data1, data3) values (3, 300);

select a1.data1, a1.data2, a2.data3
from test_table4000 a1, test_table5000 a2
where a1.data1 = a2.data1;

create view test_view
as 
select a1.data1, a1.data2, a2.data3
from test_table4000 a1, test_table5000 a2
where a1.data1 = a2.data1;

select * from test_view;

drop view test_view;

select * from test_view;
```


