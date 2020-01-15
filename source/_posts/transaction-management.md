---
date: '2020/1/16 00:12:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: Transaction
---

* 트랜젝션
  * 데이터베이스에서 데이터 처리의 한 단위를 트랜젝션이라고 한다.
  * 데이터 저장, 수정, 삭제 등 일련의 활동은 즉시 하드디스크에 반영되지 않는다.
  <!-- more -->
  * 커밋을 하기 전에 발생한 변화는 메모리 상에서만 동작한다. 커밋을 하면 하드디스크에 적용된다.
  * 개발자가 데이터 작업을 위해 입력하는 명령문의 시작부터 커밋까지의 과정을 트랜젝션이라고 부른다.

  * rollback
    * 데이터 저장, 삭제, 수정 작업을 한 뒤에 원래 형태로 되돌리는 작업
    * 커밋을 한 후 RollBack 작업을 해도 원래 상태로 되돌리지 못한다.
    * workbench와 같은 프로그램에서는 자동으로 커밋작업이 발생하므로 RollBack을 해도 작동되지 않는다.

```
select * from test_table2;

delete from test_table2;
select * from test_table2;

rollback;
select * from test_table2;

```

  * savepoint
    * savepoint를 지정하면 rollback 시 지정된 위치로 복원 가능
    * savepoint 명령어로 지점을 지정하고 rollback 명령어로 복원한다

```
insert into test_table2 (data1, data2, data3) values (100, "lang1", 11.1);
insert into test_table2 (data1, data2, data3) values (200, "lang2", 22.1);
insert into test_table2 (data1, data2, data3) values (300, "lang3", 33.1);

commit;	

select * from test_table2;
update test_table2 set data2="newlang", data3=44.4 where data1=100;
savepoint aa;
delete from test_table2 where data1=100;
rollback to aa;
select * from test_table2;
```

  * truncate
    * truncate를 사용하면 지정된 테이블의 모든 로우를 삭제한다.
    * delete문은 데이터베이스에 바로 반영하지
    * 않으므로 rollback이 가능하지만, truncate는 바로 데이터베이스에 반영하므로 rollback이 불가능

```
truncate test_table2;
rollback;
select * from test_table2;

//복원되지 않음
```

