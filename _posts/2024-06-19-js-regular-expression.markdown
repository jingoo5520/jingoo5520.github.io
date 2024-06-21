---
layout: post
title: "정규식"
date: 2024-06-19 01:00:00 +0900
categories: javaScript
---

## 정규식(Regular Expression: RegExp)

### 정규식 용도

-   특정 패턴과 일치하는 문자열 찾기
-   패턴을 기반으로 문자열 대체
-   문자열이 특정 형식을 따르는지 검사

### 정규식 생성

#### 리터럴 방식

> ex

```javascript
const regex = /pattern/flags;
```

#### 정규식 생성자 호출

> ex

```javascript
const regex = new RegExp("pattern", "flags");
```

#### 패턴

`.` 모든 단일 문자와 일치<br>
`\d` 숫자와 일치(0-9)<br>
`\w` 단어 문자와 일치(a-z, A-Z, 0-9, \_)<br>
`\s` 공백 문자와 일치(공백, 탭, 줄바꿈)<br>
`^` 문자열의 시작과 일치<br>
`$` 문자열의 끝과 일치 <br>
`[...]` 대괄호 안의 문자 중 하나와 일치<br>
`[^...]` 대괄호 안에 없는 문자와 일치<br>
...

#### 반복 수량자

`*` 0회 이상 반복 <br>
`+` 1회 이상 반복 <br>
`?` 0회 또는 1회 <br>
`{n}` 정확히 n회 반복 <br>
`{n,}` n회 이상 반복 <br>
`{n,m}` n회 이상 m회 이하 반복 <br>

#### 플래그

`g` 전역 검색<br>
`i` 대소문자 무시<br>
...

<br>

### 정규식 메서드

#### 문자열이 정규식과 일치하는지 검사

`test()`

> ex

```javascript
// 정규식 패턴 "hi"
// 대소문자 무시
const regex = /hi/i;

let str = "Hi, my name is gilDong.";

console.log(regex.test(str)); // true

// 이메일 검증 정규식
const regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

// 패턴 풀이
// ^: 문자열의 시작
// [a-zA-Z0-9._%+-]+: 하나 이상의 허용된 문자로 구성
// @: 로컬 파트, 도메인 파트 구분
// [a-zA-Z0-9.-]+
// \.: 마침표 이스케이프(정규식에서 `.`은 모든 문자를 의미하므로 마침표 자체로 해석 필요)
// [a-zA-Z]{2,}: 최소 2개 이상의 문자로 구성
// $: 문자열의 끝

console.log(regex.test("gil-dong@ex.com")); // true
console.log(regex.test("gil-dong@ex.co.kr")); // true
console.log(regex.test("gildong123@ex.net")); // true
console.log(regex.test("@ex.com")); // false
console.log(regex.test("gildong@")); // false
```

#### 정규식과 일치하는 부분을 다른 문자열로 대체

`replace()`

> ex

```javascript
const regex = /hi/i;

let str = "Hi, my name is gilDong.";

console.log(str.replace(regex, "Hello")); // Hello, my name is gilDong.
```
