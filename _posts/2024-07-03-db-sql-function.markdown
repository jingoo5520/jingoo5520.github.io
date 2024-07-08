---
layout: post
title: "SQL Function"
date: 2024-07-03 00:00:00 +0900
categories: DB
---

<!--


-->

**dual Table**: 단순 입력에 대한 출력 결과를 확인하기 위한 가상의 테이블

> emp Table

<img src="/public/img/db/select_0.png" />

## 단일 행 함수

### 문자열 함수

#### 소문자, 대문자 변환

`lower(char)` 소문자 변환<br>
`upper(char)` 대문자 변환<br>
`initcap(char)` 첫 글자만 대문자로, 나머지 글자는 소문자로 변환<br>

> ex

```sql
select lower('Database') from dual; -- database

select upper('Database') from dual; -- DATABASE

select initcap('smith') from dual; -- Smith
```

#### 문자열 연결

`concat(char1, char2, [ char3, char4, ... ])`

> ex

```sql
select concat('Data', 'base') from dual; -- Database
```

#### 문자열의 길이

`length(char)`

> ex

```sql
select length('Database') from dual; -- 8
```

#### 문자열 일부 추출

`substr(char, position, [length])`
**position**: 시작 인덱스<br>
**length**: 시작 인덱스로 부터 추출할 만큼의 길이

> ex

```sql
-- 오라클은 index가 1부터 시작
select substr('Database', 1) from dual; -- Database
select substr('Database', 1, 4) from dual; -- Data

-- 음수는 뒤에서부터 index 시작
select substr('Database', -4, 4) from dual; -- base
```

#### 특정 문자 위치 반환

`instr(string, substring, [position])`<br>
**substring**: 검색 문자<br>
**position**: 검색 시작 인덱스<br>

> ex

```sql
select instr('Database', 'b') from dual; -- 5

-- 처음 발견된 문자의 index만 반환
select instr('Database', 'a') from dual; -- 2

-- 5번 인덱스부터 탐색
select instr('Database', 'a', 5) from dual; -- 6
```

#### 문자열 앞, 뒤 특정 문자 정리

`trim([{leading | trailing | both} char from] source)`<br>
**leading**: 왼쪽 제거<br>
**trailing**: 오른쪽 제거<br>
**both**: 양쪽 제거<br>

`ltrim(char, [set])`<br>
`rtrim(char, [set])`<br>
**set**: 제거할 문자

> ex

```sql
-- 양쪽 공백 제거
select trim(' Database ') from dual; -- Database

-- 양쪽의 '_' 문자 제거
select trim('_' from '__Database__') from dual; -- Database

-- 왼쪽의 '_' 문자 제거
select trim(leading '_' from '__Database__') from dual; -- Database__
select ltrim('__Database__', '_') from dual; -- Database__

-- 오른쪽의 공백 제거
select rtrim('Database  ') from dual; -- Database
```

#### 문자열 대체

`replace(char, search_string, [replace_string])` <br>
**char**: 베이스 문자열 <br>
**search_string**: 변경할 문자열 <br>
**replace_string**: 대체 문자열 <br>

> ex

```sql
select replace('24/07/08', '/', '. ') from dual; -- 24. 07. 08

-- 대체문자가 없다면 빈 문자열로 대체
select replace('010-5555-1234', '-') from dual; -- 01055551234
```

#### 문자열 빈공간 채우기

`lpad(expr1, n, [expr2])` 문자열 왼쪽 채우기<br>
`rpad(expr1, n, [expr2])` 문자열 오른쪽 채우기<br>
**expr1**: 베이스 문자열<br>
**n**: 목표 문자열 길이<br>
**expr2**: 빈 공간을 채울 문자<br>

> ex

```sql
select lpad('2', 2, '0') from dual; -- 02
```

<br>

### 수학 함수

#### 절대값

`abs(n)`

#### 소수점

`floor(n)` 소수점 버림(절삭)<br>
`ceil(n)` 소수점 올림<br>
`round(n, [integer])` 소수점 반올림<br>
**integer**: integer 자리수 아래에서 반올림

`trunc(n1, [n2])` 소수점 내림
**n2**: n2 자리수 아래에서 내림

> ex

```sql
select floor(3.141592) from dual; -- 3
select ceil(3.141592) from dual; -- 4
select round(3.141592, 2) from dual; -- 3.14
select round(3.141592, 3) from dual; -- 3.142

-- 100의 자리 아래에서 반올림
select round(314, -2) from dual; -- 300

select trunc(3.141592, 2) from dual; -- 3.14
```

#### 나머지

`mod(n2, n1)`
**n2 / n1** 나머지<br>

#### 양수, 음수, 0 분류

`sign(n)`

#### 제곱

`power(n2, n1)` 제곱<br>
**n2<sup>n1</sup>**<br>

`sqrt(n)` 제곱근<br>

<br>

### 날짜(시간) 함수

#### 현재 시간 반환

`sysdate` <br>
동적 시스템 변수 처럼 작동하며, 괄호 없이 호출 가능

> ex

```sql
select sysdate as 오늘 from dual; -- 24/07/08
```

#### 두 날짜 사이의 달(개월) 간격

`months_between(date1, date2)`

> ex

```sql
select sysdate from dual; -- 24/07/08
select floor(months_between(sysdate, '24/01/01')) from dual; -- 6
```

#### 특정 날짜로 부터 가장 가까운 요일의 날짜 반환

`next_day(date, char)`<br>
**date**: 날짜<br>
**char**: 요일<br>

> ex

```sql
-- 지금부터 가장 가까운 금요일의 날짜 반환
select sysdate, next_day(sysdate, '금요일') from dual;
```

#### 개월수 추가

`add_months(date, integer)`

#### 해당 달의 마지막 날짜 반환

`last_day(date)`

#### 날짜 올림, 내림

`round(date [, fmt])` 기준을 정해 날짜 반올림<br>
`trunc(date, [, fmt])` 기준을 정해 날짜 내림<br>
**fmt**: 기준<br>

> ex

```sql
-- 달을 기준으로 반올림
-- 이번달 1일에 가까우면 이번달 1일, 다음달 1일에 가까우면 다음달 1일 반환
select sysdate, round(sysdate, 'month') from dual;

-- 년을 기준으로 반올림
-- 이번년도 1월 1일 or 다음 년도 1월 1일 반환
select sysdate, round(sysdate, 'year') from dual;

-- 이번달 1일 반환
select sysdate, trunc(sysdate, 'month') from dual;

-- 이번 년도 1월 1일 반환
select sysdate, trunc(sysdate, 'year') from dual;
```

### 변환 함수

#### 문자열로 변환

`to_char(n [,fmt [, nlsparam]])` number to char<br>
`to_char(datetime | interval [,fmt [, nlsparam]])` datetime to char<br>

> ex

```sql
-- number to char
select to_char(500) from dual; -- 숫자 500을 문자 '500' 으로 변경
select to_char(5000, 'L999,999') as sal from dual; --￦5,000

-- datetime to char
select sysdate, to_char(sysdate, 'yyyy-mm-dd') from dual; -- 24/07/07
select sysdate, to_char(sysdate, 'yyyy. mm. dd. dy') from dual; -- 24. 07. 07. 일
select sysdate, to_char(sysdate, 'yyyy-mm-dd day am hh24:mi:ss') from dual; -- 2024-07-07 일요일 오후 15:59:40
```

#### 날짜로 변환

`to_date(char [, fmt [, nlsparam]] )`

#### 숫자로 변환

`to_number(char [, fmt [, nlsparam]] )`

<br>

### 기타 함수

#### null이라면?

`nvl(expr1, expr2)`<br>
**expr1**: 값<br>
**expr2**: expr1 = null인 경우 대체 값<br>

> ex

```sql
select null from dual; -- (null)
select nvl(null, 0) from dual; -- 0
```

#### 다중 조건문

`decode(expr, search, result [, search, result]... [, default])`<br>
**expr**: 값
**search**: 특정 값
**result**: 값 = 특정 값인 경우 출력 값

> ex

```sql
select decode(2,
    1, 'one',
    2, 'two',
    3, 'three')
from dual; -- two
```

`case 문`

> ex

```sql
-- ename, deptno를 출력
-- deptno의 값에 따라 부서명 column에서 보여줄 데이터를 지정
select ename, deptno,
case when deptno = 10 then 'Administration'
     when deptno = 20 then 'Marketing'
     when deptno = 30 then 'Purchasing'
     else 'default'
end as "부서명"
from emp;
```

<br>

<hr>
<br>

## 다중행 함수

### 집계 함수

#### 계산

`sum([distinct | all] expr)`<br>
`avg([distinct | all] expr)`<br>
`count({* | [distinct | all] expr})`<br>

> ex

```sql
-- 직원 급여 총합
select sum(sal) from emp;

-- 직원 급여 평균
select avg(sal) from emp;

-- 직원 수
select * from emp;
```

#### 최대, 최소값

`max([distinct | all] expr)`<br>
`min([distinct | all] expr)`<br>

> ex

```sql
-- 최대 급여와 최소 급여
select max(sal), min(sal) from emp;
```

#### 표준편차와 분산

`stddev()`<br>
`variance()`<br>

<br>
