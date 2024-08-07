---
layout: post
title: "SQL 명령어"
date: 2024-07-10 00:00:00 +0900
categories: DB
---

## ORACLE DATATYPE

`char(size)` 고정길이 문자 데이터<br>
`varchar2(size)` 가변길이 문자 데이터<br>
`date` 날짜<br>
`number(w, d)` 숫자형<br>
**w**: 숫자 전체 길이(max 38)<br>
**d**: 소수점 이하 자리수<br>

<br>
<hr>
<br>

## DDL(Data Definition Language)

DB 객체(테이블, 인덱스, 뷰)를 생성, 수정, 삭제하는 명령어

### CREATE

DB 객체 생성

> pseudo

```sql
create table 테이블명 (
    컬럼명1 데이터타입,
    컬럼명2 데이터타입,
    ...
    컬럼명3 데이터타입
);
```

> ex

```sql
create table member (
    userid varchar2(12),
    passwd varchar2(16),
    name varchar2(12)
);
```

### ALTER

DB 객체 수정

`add` 컬럼 추가<br>
`modify` 컬럼 수정<br>

-   해당 컬럼에 데이터가 없는 경우 데이터 타입과 크기 변경 모두 가능
-   해당 컬럼에 데이터가 있는 경우 데이터 타입 변경과 크기를 늘리는 것만 가능

`drop` 컬럼 삭제<br>
`rename` 컬럼명 변경<br>

> pseudo

```sql
alter table 테이블명
add 컬럼명;

alter table 테이블명
modify 컬럼명 데이터타입;

alter table 테이블명
drop column 컬럼명;

alter table 테이블명
rename column 컬럼명 to 변경할 컬럼명;
```

> ex

```sql
-- email 컬럼 추가
alter table member
add email;

-- userid 컬럼 데이터 크기 변경
alter table member
modify userid varchar2(16);

-- email 컬럼 삭제
alter table member
drop column email;

-- name 컬럼 이름 username 으로 변경
alter table member
rename column name to username;
```

### DROP

DB 객체 삭제

> pseudo

```sql
drop table 테이블명;
```

> ex

```sql
drop table member;
```

### TRUNCATE

테이블 데이터 모두 삭제, 구조만 남김

> pseudo

```sql
truncate table 테이블명;
```

> ex

```sql
truncate table member;
```

### RENAMETO

테이블 이름 변경

> pseudo

```sql
rename 테이블명 to 변경할 테이블명;
```

> ex

```sql
rename member to members;
```

<br>
<hr>
<br>

## DML(Data Manipulate Language)

> member table

<img src="/public/img/db/member_0.png">

<!-- DB 객체(테이블, 인덱스, 뷰)를 생성, 수정, 삭제하는 명령어 -->

DB 데이터를 추가, 수정, 삭제하는 명령어

### INSERT INTO

테이블에 데이터 추가

> pseudo

```sql
insert into 테이블명([컬럼명1, 컬럼명2, ...]) values(컬럼값1, 컬럼값2, ...);
```

> ex

```sql
insert into member values('kildong123', '1234', '홍길동');

-- 이 경우 name 컬럼에는 null 값이 들어감
insert into member(userid, passwd) values('ddochi123', '2222');
```

> output

<img src="/public/img/db/member_insert_into.png">

### UPDATE

테이블의 데이터 수정

> pseudo

```sql
update 테이블명 set
    컬럼명1 = 값1,
    컬럼명2 = 값2,
    ...
[where 조건식];
```

> ex

```sql
-- 모든 행의 name 컬럼값을 null로 변경
update member set name = null;

-- 조건 설정
update member set name = '길동'
where userid = 'kildong123';
```

### DELETE

-   테이블의 데이터 삭제
-   보통의 경우, 직접 행을 삭제하는 것 보다는 탈퇴 여부와 관련된 컬럼을 이용함

> pseudo

```sql
delete from 테이블명
[where 조건식];
```

> ex

```sql
-- 모든 행 삭제
delete from member;

-- 조건 설정
delete from member
where userid = 'jingoo';
```

<br>

## DCL(Data Control Language)

데이터에 접근, 및 사용을 제어하기위한 명령어

<br>

## DQL(Data Query Language)

DB 데이터를 조회하는 명령어(SELECT 문)

## TCL(Transaction Control Language)

DB 에서 트랜잭션의 시작, 종료, 제어를 위해 사용되는 명령어

**트랜잭션**: DB에서 데이터를 처리하는 논리적인 작업의 단위

### COMMIT

-   트랜잭션 작업 내용을 DB에 영구히 저장
-   오라클이 정상 종료되는 경우나, DDL문이 수행된 이후에 자동으로 실행됨

> ex

```sql
-- member 추가 트랜잭션
insert into member values('dooly',12345, '둘리');

-- 영구히 저장
commit;
```

### ROLLBACK

-   현재 트랜잭션의 작업을 모두 취소하고 DB를 트랜잭션 시작 전의 단계로 되돌림
-   오라클이 비정상 종료되거나, 컴퓨터가 shutdown 된 경우 자동으로 실행됨

> ex

```sql
insert into member values('dooly',12345, '둘리');

-- 트랜잭션 취소, member 추가 전으로 되돌아감
rollback;
```

### SAVEPOINT

트랜잭션 내에서 특정 시점을 설정

> ex

```sql
insert into member values('dooly',12345, '둘리');

-- afterInsert 세이브포인트 생성, 'dooly' 멤버 추가 후
savepoint afterInsert;

insert into member values('huidong', 3434, '희동');

-- afterInsert 세이브포인트로 롤백,
-- 'huidong' 멤버 추가 트랜잭션 취소
rollback to afterInsert;
```
