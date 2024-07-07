---
layout: post
title: "SQL Function"
date: 2024-07-03 00:00:00 +0900
categories: DB
---

<!--


-->

**dual Table**: 단순 입력에 대한 출력 결과를 확인하기 위한 가상의 테이블

## 단일 행 함수

## 문자열 함수

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

`instr(string, substring, [position])`
**substring**: 해당 문자의 위치를 반환<br>
**position**: 시작 인덱스<br>

> ex

```sql
select instr('Database', 'b') from dual; -- 5

-- 처음 발견된 문자의 index만 반환
select instr('Database', 'a') from dual; -- 2

-- 5번 인덱스부터 탐색
select instr('Database', 'a', 5) from dual; -- 6
```

#### 문자열 앞, 뒤 특정 문자 정리

`trim([{leading | trailing | both}} char from] source)`
**leading**: 왼쪽 제거<br>
**trailing**: 오른쪽 제거<br>
**both**: 양쪽 제거<br>

`ltrim(char, [set])`
`rtrim(char, [set])`
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
**search_string**: 찾을 문자열 <br>
**replace_string**: 변경 할 문자열 <br>

#### 문자열 빈공간 채우기

`lpad(expr1, n, [expr2])` 문자열 왼쪽 채우기<br>
`rpad(expr1, n, [expr2])` 문자열 오른쪽 채우기<br>
**expr1**: 베이스 문자열<br>
**n**: 목표 문자열 길이<br>
**expr2**: 빈 공간을 채울 문자<br>

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

```

#### 두 날짜 사이의 달(개월) 간격

`months_between(date1, date2)`

#### 특정 날짜로 부터 가장 가까운 요일의 날짜 반환

`next_day(date, char)`
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
**fmt**: <br>

<!-- 여기서부터 -->

`trunc()` 기준을 정해 날짜 내림<br>

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

`to_char()`

#### 날짜로 변환

`to_date()`

#### 숫자로 변환

`to_number()`
<br>

### 기타 함수

#### null이라면?

`nvl()`

#### 다중 조건문

`decode()`
`case`
<br>

<hr>
<br>

## 그룹 함수

### 집계 함수

#### 계산

`sum()`
`avg()`
`count()`

#### 최대, 최소값

`max()`
`min()`

#### 표준편차와 분산

`stddev()`
`variance()`

<br>
