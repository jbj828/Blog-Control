---
date: '2020/1/15 12:46:25'
tags:
  - database, MySQL
categories:
  - Database, MySQL
thumbnail: ''
permalink: ''
title: Join문, 서브쿼리, Set
---

* join
  * 데이터의 중복을 최소화 하기 위해 테이블을 분리 시킨 후 데이터를 가져올 때 여러 테이블을 하나의 결과로 가져올 때 join문을 사용한다

<!-- more -->
  * join문을 사용하면 여러 테이블의 데이터를 한 번에 가져올 수 있다
  * join 문을 사용하면 다 대 다의 관계로 가져온다. 이 때문에 잘못된 데이터가 구성될 수 있는데 이를 위해 join조건문을 작성해야 한다.

```

select a2.emp_no, a2.dept_no, a1.dept_no, a1.dept_name
from departments a1, dept_emp a2
where a1.dept_no = a2.dept_no
order by a2.emp_no;


select a1.emp_no, a1.first_name, a2.dept_no 
from employees a1, dept_emp a2
where a1.emp_no = a2.emp_no;

select a1.emp_no, a1.first_name, a2.salary
from employees a1, salaries a2
where a1.emp_no = a2.emp_no
	and a2.to_date = '9999-01-01';
    
    
select a1.emp_no, a1.first_name, a2.dept_name
from employees a1, departments a2, dept_emp a3
where a3.emp_no = a1.emp_no and a3.dept_no = a2.dept_no;

```

* 서브쿼리
  * 쿼리문 안에 쿼리문이 있는 것을 서브쿼리라고 부른다
  * 조건문 등을 만들 때 값을 직접 지정하지 못하고 쿼리문을 통해 구해야와 할 경우 서브쿼리를 통해 값을 구해와 조건문을 완성 할 수 있다

```
-- 현재 받는 급여의 평균보다 많이 받는 사람들의 사원번호, 급여액을 가져온다

select emp_no, salary
from salaries
where salary > (select avg(salary) from salaries where to_date="9999-01-01")
				and to_date="9999-01-01";
                
-- d001부서에 근무하고 있는 사원들의 사원번호와 first_name을 가져온다
select emp_no, first_name
from employees
where emp_no in(select emp_no from dept_emp where  dept_no='d001');

-- 1960년 이후에 태어난 사원들이 근무하고 있는 사원들의 사원번호, 근무 부서 번호를 가져온다
select emp_no, dept_no
from dept_emp
where emp_no in(select emp_no from employees where birth_date >= '1960-01-01');
```

* set
  * 두 select 문을 통해 얻어온 결과를 집합 연산을 통해 하나의 결과로 만드는 것을 set이라고 한다.
  * 합집합, 교집합, 차집합 등 집합 연산을 할 수 있다
  * 집합 연산을 하기 위해서는 두 select문을 통해 가져오는 컬럼이 같아야 한다.

  * 합집합
    * 두 select문의 결과를 모두 포함하는 최종 결과 반환
    * union : 중복되는 데이터는 하나만 가져옴
    * union all: 중복되는 데이터도 모두 가져옴

```
select emp_no from titles where title='Senior Staff'
union
select emp_no from titles where title='Staff';
```

  * 교집합
    * join문을 사용한다

  * 차집합
    * 차집합은 서브쿼리를 이용한다

