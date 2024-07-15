---
layout: post
title: "SQL 제약조건(Constraint)"
date: 2024-07-11 00:00:00 +0900
categories: DB
---

## 제약조건(Constraint)

-   데이터의 무결성과 일관성을 보장하기 위해 Column에 적용하는 규칙
-   DB의 데이터를 추가, 수정, 삭제할 때 조건을 반드시 지키게 함

### NOT NULL

열의 값이 null이 될 수 없음

### UNIQUE

열의 모든 값이 고유해야 함

### PRIMARY KEY

-   각 행을 고유하게 식별할 수 있게 지정
-   NOT NULL, UNIQUE 속성을 모두 가짐

> ex

```sql
-- 회원 테이블
create table MEMBER (
    member_id int primary key,
    member_name varchar(20) not null,
    member_birth date
);

-- 장르 테이블
create table GENRE (
    genre_id int,
    genre_name varchar(20) not null,
    primary key(genre_id)
);
```

### FOREIGN KEY

해당 열이 다른 테이블의 PK 또는 UNIQUE 열을 참조

> ex

```sql
-- 비디오 테이블
create table VIDEO (
    video_id int primary key,
    video_title varchar(50) not null,
    video_rating varchar(20),
    genre_id int references genre(genre_id)
);
```

### CHECK

값이 지정된 조건을 만족해야함

> ex

```sql

```

### DEFAULT

기본 값 지정

> ex

```sql

```

<br>
<hr>
<br>

## 제약조건 기술 방법

### 컬럼 단위 기술

> ex

```sql
create table VIDEO (
    video_id varchar(6) primary key,
    video_title varchar(50) not null,
    video_rating varchar(20),
    genre_id int references genre(genre_id)
);
```

### 테이블 단위 기술

> ex

```sql
create table VIDEO (
    video_id varchar,
    video_title varchar(50) not null,
    video_rating varchar(20),
    genre_id int,
    primary key(video_id),
    foreign key(genre_id) references genre(genre_id)
);
```

### 제약조건 이름 지정

constraint 키워드를 이용해 이름을 지정할 수도 있음

> ex

```sql
create table VIDEO (
    -- video_video_id_pk 제약조건 생성
    video_id varchar(6) constraint video_video_id_pk primary key,
    -- video_video_title_nn 제약조건 생성
    video_title varchar(50) constraint video_video_title_nn not null,
    video_rating varchar(20),
    genre_id int,
    -- video_genre_id_fk 제약조건 생성
    constraint video_genre_id_fk foreign key(genre_id) references genre(genre_id)
);
```

### 제약조건 옵션

Foreign Key 제약조건이 설정된 컬럼에서, 참조된 값이 변경되거나 삭제될 때의 동작을 정의

#### cascade

부모 테이블에서 행이 삭제되거나 업데이트 되는 경우, 자식 테이블에서도 해당 행이 삭제되거나 업데이트됨

> ex

```sql
create table GENRE (
    genre_id int,
    genre_name varchar(6)
);

create table VIDEO (
    video_id varchar(6),
    video_title varchar(50) not null,
    video_rating varchar(20),
    genre_id int,
    primary key(video_id),
    foreign key(genre_id) references genre(genre_id)
    on delete cascade on update cascade
);
```

#### set null

부모 테이블에서 행이 삭제되거나 업데이트 되는 경우, 자식의 외래 키 값이 null 로 설정됨

> ex

```sql
create table GENRE (
    genre_id int,
    genre_name varchar(6)
);

create table VIDEO (
    video_id varchar(6),
    video_title varchar(50) not null,
    video_rating varchar(20),
    genre_id int,
    primary key(video_id),
    foreign key(genre_id) references genre(genre_id)
    on delete set null on update set null
);
```
