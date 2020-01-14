---
date: '2020/1/5 00:46:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: MySQL select 쿼리문
---

* select 구문
  * select 구문은 저장되어 있는 데이터를 가져올 때 사용한다.
  * select 컬럼명 from 테이블명

<!-- more -->
  * 테이블의 모든 정보 가져오기
    * select * from 테이블명
    * 사원의 모든 정보를 가져올 경우 employess 테이블에 있으므로 
      * select * from employees

  * 일부 컬럼만 가져오기
    * select 컬럼명1, 컬럼명2, 컬럼명3 from 테이블명
    * select emp_no, first_name, last_name from employees;

* 연산자 사용하기
  * 산술 연산자를 사용하면 데이터를 가져올 때 연산을 해서 가져올 수 있다.
  * select salary, salary + 1000, salary - 1000, salary *1000, salary / 1000
  from salaries;

  * select emp_no, salary, salary * 1.1, salary*0.9
  from salaries
  * 문자열은 0으로 취급함

  * distinct 연산자
    * 가져온 결과에 중복을 제거한다.
    * select distinct 컬럼명 from 테이블명


* 조건 사용하기
  * select 구문에 where 절을 사용하면 조건을 설정할 수 있다.
  * 컬럼에 저장되어 있는 데이터를 기준으로 검색하면 원하는 데이터만 가져올 수 있다.
  ```
      select emp_no, dept_no
      from dept_manager
      where dept_no = "d003";

      select emp_no, dept_no
      from dept_manager
      where dept_no <> "d003"; // <> not 이라는 뜻
  ```

* 날짜 데이터
  * 날짜 데이터를 조건절로 사용할 때도 비교 연산자를 이용하면 된다.

  ```
  select emp_no, hire_date, first_name, last_name
  from employees
  where hire_date >= '1986-01-01';

  ```

* 논리 연산자
  * 두 개 이상의 조건문을 작성할 때 사용하는 연산자
  * and, or, not
  
    ```
    select emp_no, salary, from_date
    from salaries
    where salary >= 60000 and from_date >= '1990-01-01';

    select emp_no, dept_no
    from dept_manager
    where dept_no = 'd001' or dept_no='d002';

    select dept_no, emp_no
    from dept_manager
    where dept_no <> 'd003';

    select dept_no, emp_no
    from dept_manager
    where not dept_no = 'd003';
    ```

* Between
  * 컬럼의 범위를 조건으로 사용할 때 사용한다.
  * and 대신 사용한다
  * 컬럼명 between 값 1 and 값2
  
  ```
  select emp_no, salary
  from salaries
  where salary between 60000 and 70000;
  ```

* in
  * 지정된 컬럼의 값이 특정 값에 해당되는 조건을 만들 때 사용한다.
  * or 대신 사용한다.
  * 컬럼명 in (값1, 값2, ...)
  
  ```
  select emp_no, dept_no
  from dept_manager
  where dept_no in('d001', 'd002');
  ```