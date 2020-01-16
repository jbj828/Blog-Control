---
date: '2020/1/16 00:40:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: 테이블 변경하기
---

* rename 명령문 : 테이블 이름을 변경
* alter 명령문 : 테이블의 컬럼을 추가, 변경, 삭제
* drop table 명령문 : 테이블 삭제
<!-- more -->

```
show tables;
-- rename
rename table test_table1 to test_table3;
show tables;

-- 속성변경
desc test_table3;
alter table test_table3 modify data1 int(100);
desc test_table3;

-- 컬럼변경
alter table test_table3 change data1 data10 int(200);
desc test_table3;

-- 컬럼추가
alter table test_table3 add data4 int(10);
desc test_table3;

-- 컬럼삭제
alter table test_table3 drop data4;
desc test_table3;

-- 테이블 삭제
drop table test_table3;
show tables;
```






