---
layout: post
title: "Variables and DataTypes"
date: 2024-07-16 00:00:00 +0900
categories: JAVA
---

<style>
    #dataTypeTable {
        width: 80%;
    }

    #dataTypeTable td {
        width: 20%;
    }
</style>

## 변수

-   데이터를 저장할 수 있는 메모리 공간
-   데이터 타입과 변수 이름을 지정해 선언 가능

> ex

```java
int korScore; // 변수 선언
korScore = 95; // 변수 초기화

int engScore = 90; // 선언과 초기화
```

### 명명 규칙

-   대소문자 구분, 길이제한은 없음
-   예약어(키워드) 사용 불가
-   첫 번째 글자는 소문자, 이후는 문자, 숫자, 특수문자('\_', '$') 사용 가능
-   상수의 이름은 대문자로 표기하고, 여러 단어로 이루어진 경우 언더스코어('\_') 로 구분
-   카멜 표기법(Camel Case)를 따르고 의미를 포함시켜 작명

<br>
<hr>
<br>

## 데이터타입

### 기본형

-   자바에서 제공하는 기본적인 데이터타입으로, 총 8가지가 있음
-   각 데이터 타입은 고정된 크기를 가짐
-   선언시 스택 영역에 공간을 예약하고 초기화시 해당 공간에 값을 저장

<br>

<table id="dataTypeTable">
    <tr>
        <td></td>
        <td>1 byte</td>
        <td>2 byte</td>
        <td>4 byte</td>
        <td>8 byte</td>
    </tr>
    <tr>
        <td>논리형</td>
        <td>boolean</td>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>문자형</td>
        <td></td>
        <td>char</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>정수형</td>
        <td>byte</td>
        <td>short</td>
        <td>int</td>
        <td>long</td>
    </tr>
    <tr>
        <td>실수형</td>
        <td></td>
        <td></td>
        <td>float</td>
        <td>double</td>
    </tr>
</table>

<br>

`char`<br>
내부적으로 2바이트 유니코드의 정수로 저장되므로, 정수형 또는 실수형 데이터와 연산도 가능

> ex

```java
char a = 'a';
System.out.println(a); // 98
System.out.println(a + 1); // 68
```

### 참조형

-   객체의 주소를 저장하는 변수
-   클래스, 배열, 인터페이스 등
-   선언시 스택영역에 공간을 예약
-   생성시 해당 영역에 주소값을 저장하고 힙 영역의 해당 주소에 타입에 따른 기본값 저장

> ex

```java
String name = "Jingoo";

int[] scores = {90, 95, 89};
```

<br>
<hr>
<br>

## 형변환(Type Casting)

### 묵시적 형변환(자동 형변환)

-   작은 범위의 데이터 타입이 큰 범위의 데이터 타입으로 자동 변환
-   서로 다른 타입간의 연산은 큰 범위로 자동 형변환이 일어남

> ex

```java
int a = 100;
double b = a;

System.out.println(b); // 100.0

// 연산시 자동 형변환
// int보다 작은 타입간 연산
byte b = 2;
short s = 3;
System.out.println(b + 3); // int형 5

int i = 1;
System.out.println(i + s); // int형 4

// float, double 연산
float f = 1.5f;
double d = 2.2;

System.out.println(f + d); // double형 3.7
```

### 명시적 형변환(강제 형변환)

-   큰 범위의 데이터 타입을 작은 범위의 데이터 타입으로 변환시 명시적으로 변환
-   데이터 손실이 발생할 수 있음

> ex

```java
double b = 1.5;
int a = (int)b;

System.out.println(a); // 1
```
