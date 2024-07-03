---
layout: post
title: "SQL, SELECT"
date: 2024-07-01 01:00:00 +0900
categories: DB
---

## SELECT 문

관계형 데이터베이스의 데이터 조회

## 구성 요소

> emp Table

<img src="/public/img/db-sql-select/select_0.png" />

`SELECT` 조회할 컬럼 지정 <br>
`FROM` 데이터를 조회할 테이블 지정 <br>

> ex

```sql
-- emp 테이블 모든 데이터 조회
SELECT * FROM emp;

-- emp 테이블에서 empno, ename 컬럼 데이터 조회
SELECT empno, ename FROM emp;
```

<br>

`WHERE` 조건을 지정하여 데이터 필터링 <br>

> ex

```sql
-- emp 테이블에서 deptno = 10 인 emp, ename 컬럼 데이터 조회
SELECT emp, ename
FROM emp
WHERE deptno = 10;
```

<br>

`GROUP BY` 특정 컬럼을 기준으로 데이터를 그룹화 <br>
`HAVING` 그룹화된 데이터에 조건을 지정하여 필터링 <br>

> ex

```sql
-- deptno 별로 행의 수를 출력
SELECT deptno, count(*)
FROM emp
GROUP BY deptno;

-- deptno 별로 행의 수를 출력하는데, 10 이상만 출력
SELECT deptno, count(*)
FROM emp
GROUP BY deptno
HAVING count(*) > 10;
```

<br>

`ORDER BY` 결과 정렬 <br>
**ASC**: 오름 차순<br>
**DESC**: 내림 차순<br>

> ex

```sql
-- sal 기준 오름차순(ASC) 정렬
SELECT empno, ename, sal
FROM emp
ORDER BY sal ASC;
```

<br>

## 키워드

`distinct` 중복 제거<br>

> ex

```sql
-- emp 테이블에서 job_id를 중복없이 출력
SELECT distinct job FROM emp;
```

<br>

`as` 별칭 설정<br>

> ex

```sql
-- emp 테이블에서 ename 컬럼의 이름을 name으로 설정하여 출력
SELECT ename as name FROM emp;
```

<br>

## 연산자

### 비교 연산자

`=` 같음 <br>
`!=`, `<>` 같지 않음<br>
`>`, `>=`, `<`, `<=` 크기 비교<br>
`BETWEEN a AND b` 지정된 범위(a, b) 내에 포함됨<br>

> ex

```sql
-- emp 테이블에서 급여가 3000이상, 7000이하인 사원들의 이름과 급여 출력
SELECT ename, sal
FROM emp
WHERE sal BETWEEN 3000 AND 7000;

-- emp 테이블에서 입사년도가 1980년에서 1981년 사이인 사원들의 모든 정보 출력
SELECT *
FROM emp
WHERE hiredate BETWEEN '80/01/01' AND '81/01/01';
```

<br>

`IN` 지정된 목록 중 하나에 포함<br>

> ex

```sql
-- 부서번호가 10번 또는 20번인 사원들의 모든 정보 출력
SELECT * FROM emp WHERE deptno IN (10, 20);
```

<br>

`LIKE` 지정된 패턴과 일치<br>
**%**: 문자가 없거나 어떤 값이든 상관없이 하나 이상의 문자가 있음<br>
**\_**: 어떤 값이든 상관 없이 하나의 문자가 있음<br>

> ex

```sql
-- emp 테이블에서 이름이 'S'로 시작하는 모든 사원들의 정보를 출력
SELECT *
FROM emp
WHERE ename LIKE 'S%';

-- emp 테이블에서 이름의 끝에서 두 번째 글자가 'E'인 모든 사원들의 정보를 출력
SELECT *
FROM emp
WHERE ename LIKE '%E_';
```

<br>

`IS NULL` 값이 null임<br>

> ex

```sql
-- 커미션을 받는 사원들의 모든 정보 출력
SELECT *
FROM emp
WHERE comm IS NOT NULL;
```

<br>

### 논리 연산자

여러 조건을 조합하거나 반전할 때 사용

`AND`<br>

> ex

```sql
-- 82년 이전에 입사하였고, 급여가 2000 초과인 사원들의 사번, 이름, 급여 출력
SELECT empno, ename, sal
FROM emp
WHERE hiredate < '82/01/01' AND sal > 2000;
```

<br>

`OR`<br>

> ex

```sql
-- 부서번호가 10번이거나 20번인 사원들의 모든 정보 출력
SELECT *
FROM emp
WHERE deptno = 10 or deptno = 20;
```

<br>

`NOT`<br>

> ex

```sql
-- 부서번호가 20번이 아닌 사원들의 모든 정보 출력
SELECT *
FROM emp
WHERE deptno != 20;
```
