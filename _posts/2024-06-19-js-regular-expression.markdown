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

### 정규식 메서드
