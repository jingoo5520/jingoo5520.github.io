---
layout: post
title: "변수와 상수"
date: 2024-05-24 00:00:00 +0900
categories: javaScript
---

<!--
## 변수란
## 선언과 초기화
## 데이터 타입
## 상수
## 명명규칙
## 여러가지 표기법
## 예제문제
-->

## 변수

변할 수 있는 값을 저장하기 위한 저장소

## 선언과 초기화

`let` 키워드를 사용하여 변수 선언

> ex

```javascript
// number 변수를 선언
let number;

// number 변수의 값을 3으로 초기화
number = 3;

// 선언과 동시에 초기화
let name = "홍길동";

// 변수에 새로운 값 할당
number = 5;
```

`var` 키워드는 더이상 사용하지 않음

<br>

## 데이터 타입

다른 프로그래밍 언어와 달리 변수 타입을 선언할 필요가 없음

> ex

```javascript
// 숫자
let age = 28;
let number = 3; // 숫자 3

// 문자열
let name = "홍길동";
let myNumber = "3"; // 문자 3

// 불리언
let isReal = true;
let test = 10 > 20;
console.log(test); // false

// 배열
let array = [1, 2, 3, 4, 5];
console.log(array[0]); // 1

// 객체
let person = { name: "홍길동", age: 25 };
console.log(person.name); // 홍길동

// null
let number = null; // 명시적으로 아무것도 없음을 나타냄
```

<br>

## 상수

-   변하지 않는 값을 저장하는 저장소<br>
-   선언과 동시에 초기화해야함<br>
-   초기화 후에는 새로운 값 할당 불가<br>
-   가능하다면 `const`를 사용하고 필요한 경우 `let`사용을 권장<br>

> ex

```javascript
// 선언과 동시에 초기화
const PI = 3.14;

PI = 5; // 재할당 불가, 에러발생
```

<br>

## 변수, 상수 명명 규칙

-   영문자나 숫자, '밑줄 문자(\_), '$' 문자를 사용

-   첫 글자는 숫자로 시작할 수 없음

-   포함된 데이터를 설명할 수 있도록 직관적으로 만들어야 함

-   영문자는 대, 소문자를 구분함

-   카멜 표기법(Camel Case)을 따름

-   상수는 대문자만으로 쓰되, 두 단어 이상 결합하는 경우 밑줄 문자(\_)를 사용

-   예약어(키워드)는 사용할 수 없음

-   공백은 포함할 수 없음

<br>

## 여러가지 표기법

### 카멜 표기법(Camel Case)

첫 단어는 소문자로 시작하고, 이후 단어들의 첫 글자는 대문자로 시작

> ex

```javascript
let userName;
let phoneNumber;
```

### 파스칼 표기법(Pascal Case)

모든 단어의 첫 글자를 대문자로 시작

> ex

```javascript
let UserName;
let PhoneNumber;
```

### 케밥 표기법(Kebab Case)

모든 단어를 소문자로 작성하되 단어 사이를 하이픈(-)로 구분

> ex

```javascript
let user-name;
let phone-number;
```

### 스네이크 표기법 (Snake Case)

모든 단어를 소문자로 작성하되 단어 사이를 밑줄(\_)로 구분

> ex

```javascript
let user_name;
let phone_number;
```

<br>
<hr>
<br>

## 예제 문제

### 문제) 직사각형 넓이 출력

가로 3cm, 세로 5cm인 직사각형의 넓이를 구해 화면에 출력하라.

#### 해결 방법

-   가로, 세로 변수를 선언 및 초기화
-   넓이 변수를 선언하고 가로 \* 세로 값으로 초기화
-   단위 추가 후 출력

#### 코드

```javascript
let width = 3;
let height = 5;

let squareArea = width * height;

document.write(`넓이: ${squareArea}cm<sup>2</sup>`);
```

#### 결과

넓이: 15cm<sup>2</sup>

<br><br>

### 문제) 원의 넓이 출력

-   반지름이 5cm인 원의 넓이를 구해 화면에 출력하라.
-   원주율은 3.14로 계산한다.

#### 해결 방법

-   반지름, 원주율(π) 변수 선언 및 초기화
-   넓이 변수를 선언하고 반지름 \* 반지름 \* 원주율 값으로 초기화
-   단위 추가 후 출력

#### 코드

```javascript
let radius = 5;
const PI = 3.14;

let circleArea = radius * radius * PI;

document.write(`넓이: ${circleArea}cm<sup>2</sup>`);
```

#### 결과

넓이: 78.5398cm<sup>2</sup>

<br><br>

### 문제) 두 변수의 값 변경하기

-   두 변수가 각각 3, 5로 초기화 되어있다.
-   두 변수의 값을 각각 바꾸어 저장하고 화면에 출력하라.

#### 해결 방법

-   임시 공간으로 사용할 temp 변수 생성
-   temp 변수에 첫 번째 변수의 값을 , 첫 번째 변수에 두 번째 변수의 값을 할당
-   두 번째 변수에 temp 변수의 값을 할당
-   출력

#### 코드

```javascript
let num1 = 3;
let num2 = 5;

let temp;

document.write(`변경 전 num1: ${num1}, num2: ${num2} <br>`);

let temp = num1;
num1 = num2;
num2 = temp;

document.write(`변경 후 num1: ${num1}, num2: ${num2}`);
```

#### 결과

변경 전 num1: 3, num2: 5<br>
변경 후 num1: 5, num2: 3

<br>
