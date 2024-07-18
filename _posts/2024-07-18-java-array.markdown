---
layout: post
title: "Java Array"
date: 2024-07-16 00:00:00 +0900
categories: JAVA
---

## 배열

-   같은 타입의 여러 데이터를 저장할 수 있는 자료구조

## 선언과 생성

> ex

```java
int[] intArr; // 선언

intArr = new int[5]; // 생성
// int 배열의 초기화 없이 생성시 경우 모든 원소가 0으로 자동 초기화
System.out.println(Arrays.toString(intArr)); // [0, 0, 0, 0, 0]


char[] charArr = new char[5]; // 선언 및 생성
// char 배열의 초기화 없이 생성시 경우 모든 원소가 '\u0000'(유니코드의 null문자)로 자동 초기화
System.out.println(Arrays.toString(charArr)); // [ , , , , ]
```

### 참조타입 데이터 생성시 자바 변수 타입에 따른 기본값

## 자바스크립트 배열과의 차이점

## 배열 복사

### 깊은 복사

### 얕은 복사

## main메서드의 String[] args
