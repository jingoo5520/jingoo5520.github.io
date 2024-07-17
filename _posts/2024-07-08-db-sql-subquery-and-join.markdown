---
layout: post
title: "SQL Subquery and Join"
date: 2024-07-08 00:00:00 +0900
categories: DB
---

<!-- ## 서브쿼리

### 단일형 서브쿼리

### 다중행 서브쿼리
### 다중열 서브쿼리

## 조인

### 교차 조인
### 등가 조인
### 비등가 조인
### 셀프조인
### 외부조인

## 안시조인

### 내부 조인
### 외부 조인
### 교차 조인
### 자연 조인 -->

> emp Table

<img src="/public/img/db/select_0.png" />

## 서브쿼리

-   SQL 문장 내에 포함된 또 다른 SQL 문장
-   데이터의 조건 설정이나 필터링에 사용
-   두 번의 요청을 합쳐 서버 부하를 줄일 수 있음

> ex

```sql
-- empno = 7782 인 사원이 소속되어 있는 부서의 부서명 출력
-- 1) empno = 7782 인 사원이 소속되어 있는 부서 찾기
select deptno
from emp
where empno = 7782; -- 10

-- 2) 찾아낸 부서의 이름을 출력
select dname
from dept
where deptno = 10;

-- 3) 서브쿼리 사용
select dname
from dept
where deptno = (select deptno from emp where empno = 7782);
```

### 단일형 서브쿼리

-   서브쿼리가 한 행만 반환할 때 사용
-   서브쿼리에 대해 =, <, <=, >, >=, != 등의 연산자 사용

> ex

```sql
-- 평균 이상의 급여를 받는 사원의 사번, 이름, 급여 출력
select empno, ename, sal
from emp
where sal > (select avg(sal) from emp);
```

### 다중행 서브쿼리

-   서브쿼리가 여러 행을 반환할 때 사용
-   서브쿼리에 대해 in, any, all 연산자 사용

**in**: 서브쿼리의 결과 중 하나라도 일치하면 참<br>
**any**: 서브쿼리의 결과중 하나 이상과 비교 <br>
**all**: 서브쿼리의 결과와 모든 값이 일치하면 참<br>

> ex

```sql
-- in
-- 급여를 1000 이하로 받는 사원이 소속된 부서에서 근무하는 사원들의 정보 출력
select empno, ename, deptno
from emp
where deptno in (select deptno from emp where sal <= 1000);

-- < any
-- 서브쿼리의 결과 증 하나보다 작은 값이라면 참
-- = 서브쿼리의 결과 중 가장 큰 값보다 작다면 참
-- MANAGER 직업을 가진 사원들 중 급여가 가장 높은 사원 보다 낮은 급여를 받는 사원들 출력
select empno, ename, job, sal
from emp
where sal < any(select sal from emp where job = 'MANAGER');

-- > any,
-- 서브쿼리의 결과 증 하나보다 큰 값이라면 참
-- = 서브쿼리의 결과 중 가장 작은 값보다 크다면 참

-- = any 이 경우는 사실상 in 연산자와 동일

-- > all
-- 서브쿼리의 모든 결과보다 크다면 참
-- 30번 부서에 소속된 모든 사원들 보다 급여를 많이 받는 사원 정보 출력
select empno, ename, sal
from emp
where sal > all(select sal from emp where deptno = 30);

-- all 연산자를 사용하지 않고, 위 코드와 동일
select empno, ename, sal
from emp
where sal > (select max(sal) from emp where deptno = 30);

-- < all
-- 서브쿼리의 모든 결과보다 작다면 참
```

### 다중열 서브쿼리

서브쿼리가 여러 열을 반환

> ex

```sql
-- 부서별로 가장 급여가 많은 사원의 모든 정보 출력
select * from emp
where (deptno, sal)
in (select deptno, max(sal) from emp group by deptno);
```

<br>
<hr>
<br>

## 조인

두 개 이상의 테이블을 결합하여 하나의 결과 집합을 만드는 연산

### 교차 조인(Cross Join)

-   단순하게 두 개 이상의 테이블을 곱연산 하여 출력
-   테이블 행의 개수끼리 곱한 값이 총 행의 개수가 됨

### 등가 조인(Equi Join)

두 테이블 간의 특정 열의 값이 동일한 행만 결합

> ex

```sql
-- 사번이 7844인 사원의 정보와 그가 속한 부서명 까지 출력
select e.empno, e.ename, e.deptno, d.dname
from emp e join dept d on e.deptno = d.deptno
where e.empno = 7844;
```

> output

<img src="/public/img/db/equi_join_0.png">

### 비등가 조인(Bib-Equi Join)

-   등가 조건이 아닌 조건을 사용하는 조인
-   '>', '>=', '<', '<=' 등을 사용

> ex

```sql
-- 사원들의 정보와 급여 등급을 출력
select e.empno, e.ename, e.sal, s.grade
from emp e join salgrade s
on e.sal between s.losal and s.hisal;
```

> output

<img src="/public/img/db/non_equi_join_0.png">

### 셀프조인(Self Join)

-   동일 테이블 사이의 조인
-   한 행에 있는 값을 다른 행에 있는 다른 값과 비교하기 위해 사용
-   반드시 테이블에 별칭을 주어야 함

> ex

```sql
-- 사원의 정보와 매니저 이름을 출력
select e.empno, e.ename, e.mgr, m.ename as mname
from emp e join emp m
on e.mgr = m.empno;
```

> output

<img src="/public/img/db/self_join_0.png">

### 외부조인

-   행이 조인 조건에 만족하지 않는 경우(null 등)
-   조인 조건에 만족하지 않는 행들도 나타내고 싶을 때 사용
-   기준 컬럼에 따라 오른쪽, 왼쪽 외부 조인이 가능

> ex

```sql
-- 사원과 소속 부서를 출력하되, 소속된 사원이 없는 부서도 출력
-- 부서 테이블 기준이므로 right join
select e.ename, d.dname
from emp e right join dept d
on e.deptno = d.deptno;
```

<br>
<hr>
<br>

## 안시조인

### 내부 조인

### 외부 조인

### 교차 조인

### 자연 조인
