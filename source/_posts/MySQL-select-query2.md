---
date: '2020/1/15 10:46:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: MySQL select 쿼리문2
---

* like
  * 조건식을 만들어 줄 때 문자열과 비교 시 사용한다.
  * 문자열 값을 비교할 때 = 을 이용하면 지정된 문자열이 저장되어 있는 로우를 가져 올 수 있다.

<!-- more -->

  * like는 이를 보다 확장해서 조건을 만들어 줄 때 사용한다.
  * like는 와일드 카드라는 개념을 사용하는데 와일드 카드는 모든 글자를 의미하는 특수 기호이다.
  * _ : 글자 하나를 의미한다
  * % : 글자 수와 상관없이 모든 글자를 의미한다.

```
-- 이름이 A로 시작하는 사원의 사원번호, 이름을 가져온다
select emp_no, first_name
from employees
where first_name like 'A%';

-- 이름에 o가 포함되어 있는 사원의 사원번호, 이름을 가져온다
select emp_no, first_name
from employees
where first_name like '%o%';

-- 이름에 o가 포함되어 있는 사원의 사원번호, 이름을 가져온다
-- 단 마지막 글자가 o가 아닌 사원만 가져온다
select emp_no, first_name
from employees
where first_name like "%o%" and not first_name like '%o';
```

* 정렬
  * 데이터를 가져올 때 오름차순 혹은 내림차순으로 정렬하여 가져올 수 있다.
  * Order by 컬럼명 asc : 오름차순 정렬, asc는 생략 가능하다.
  * Order by 컬럼명 desc : 내림차순 정렬
  * 정렬 기준은 숫자, 문자열, 날짜 등 모든 컬럼이 가능하다.

```
select emp_no, salary
from salaries
order by salary desc;

select emp_no, first_name
from employees
order by first_name asc;
```

* 숫자 함수
  * 숫자와 관련된 작업을 하는 함수이다.
  * ABS(숫자) : 절대값을 구한다.
  * CEIL(숫자) : 값보다 큰 정수 중 가장 작은 정수. 소수점 이하 올림
  * FLOOR(숫자) : 값보다 작은 정수 중 가장 큰 정수. 소수점 이하 버림
  * ROUND(숫자, 자릿수) : 자릿수를 기준으로 반올림
  * TRUNCATE(숫자, 자릿수) : 자릿수를 기준으로 버림
  * POW(X, Y) or POWER(X, Y) : X의 Y승
  * MOD(분자, 분모) : 분자를 분모로 나눈 나머지를 구한다
  * GREATEST(숫자1, 숫자2, 숫자3) : 주어진 숫자 중에 가장 큰 값을 반환
  * LEAST(숫자1, 숫자2, 숫자3) : 주어진 숫자 중 가장 작은 값 반환

```
-- 절대값
select abs(100), abs(-100);

-- 소수점 이하 올림
select ceil(10.1), ceil(10.6);

-- 소수점 이하 버림
select floor(10.1), floor(10.8);

-- 반올림
select round(10.1), round(10.7);
select round(166.555, 0), round(166.555, 1), round(166.555, -1); 
	-- 167, 166.6, 170
    
-- 버림
select truncate(166.555, 0), truncate(166.555, 1), truncate(166.555, -1); 
	-- 166, 166.5, 160
    
-- x의 y승
select pow(10,2);

-- 나머지 구하기
select mod(10,3);

-- 최대 숫자 구하기
select greatest(10, 4, 20, 1);

-- 최소 숫자 구하기
select least(10, 4, 20, 1);

select emp_no, salary * 1.1, ceil(salary * 1.1),
		floor(salary * 1.1), round(salary * 1.1, 0)
from salaries;
```

* 문자열 함수
  * 컬럼에 저장되어 있는 문자열에 대한 작업을 할 수 있는 함수
  * concat(문자열1, 문자열2, 문자열3) : 문자열을 합친다
  * insert(문자열, 시작위치, 길이, 새로운 문자열) : 문자열의 시작 위치부터 길이만큼의 문자열을 제거하고 그 자리에 새로운 문자열을 삽입한다.
  * replace(문자열, 기존문자열, 새로운 문자열) : 문자열에서 기존 문자열을 찾아 제거하고 그 자리에 새로운 문자열을 삽입한다.
  * instr(문자열1, 문자열2) : 문자열1에서 문자열2를 찾아 위치를 반환한다. 위치는 1부터 시작하여 문자열 2를 찾지 못하면 0을 반환한다.
  * left(문자열, 개수) : 문자열의 좌측부터 개수만큼 가져온다
  * right(문자열, 개수) : 문자열의 우측부터 개수만큼 가져온다
  * mid(문자열, 시작위치, 개수) : 문자열에서 시작위치에서 개수만큼 가져온다.
  * substring(문자열, 시작위치, 개수) : 문자열에서 시작위치에서 개수만큼 가져온다
  * ltrim(문자열) : 문자열의 좌측 공백을 제거한다
  * rtrim(문자열) : 문자열의 우측 공백을 제거한다
  * trim(문자열) : 문자열의 좌우측 공백을 제거한다
```


