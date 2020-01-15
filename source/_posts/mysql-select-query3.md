---
date: '2020/1/15 11:46:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: 날짜함수, group by, having
---

* 날짜에 대한 작업을 하는 함수
  * now(), sysdate(), current_timestamp() : 현재 날짜와 시간을 반환한다

<!-- more -->

  * curdate(), current_date() : 현재 날짜를 반환한다
  * curtime(), current_time() : 현재 시간을 반환한다
  * date_add(날짜, interval 기준값) : 날짜에서 기준값만큼 더한다
    (year, month, day, hour, minute, second)
  * date_sub(날짜, interval 기준값) : 날짜에서 기준값만큼 뺀다
    (year, month, day, hour, minute, second)

```
select hire_date, date_add(hire_date, interval 100 day)
from employees;

select count(*) from employees;

select count(*)
from employees
where gender="M";

select count(*)
from dept_emp
where dept_no='d005' and to_date='9999-01-01';


select avg(salary)
from salaries
where to_date='9999-01-01';

-- 사원의 수를 성별로 구분하여 가져온다
select gender, count(*)
from employees
group by gender;

-- 각 부서에 근무하고 있는 사원의 수
select dept_no, count(*)
from dept_emp
where to_date='9999-01-01'
group by dept_no;


-- 각 부서별 과거의 매니저의 수를 구한다
select dept_no, count(*)
from dept_manager
where not to_date='9999-01-01'
group by dept_no;

-- 급여수령 시작일 별 급여 총합을 구한다
select from_date, sum(salary)
from salaries
group by from_date;

-- 10만명 이상이 사용하고 있는 직함의 이름과 직원의 수를 가져온다
select title, count(emp_no)
from titles
group by title
having count(emp_no) >= 100000;

-- 5만명 이상이 근무하고 있는 부서의 부서 번호와 부서 소속 사원의 수를 가져온다
select dept_no, count(*)
from dept_emp
group by dept_no
having count(*) >= 50000;
```