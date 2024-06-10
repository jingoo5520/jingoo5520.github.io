---
layout: post
title: "변수와 상수 문제"
date: 2024-05-24 01:00:00 +0900
categories: javaScript
---

## 문제) 직사각형 넓이 출력

-   가로 3cm, 세로 5cm인 직사각형의 넓이를 구해 화면에 출력하라.

### 해결 방법

-   가로, 세로 변수를 선언 및 초기화
-   넓이 변수를 선언하고 가로 \* 세로 값으로 초기화
-   단위 추가 후 출력

### 코드

```javascript
let width = 3;
let height = 5;

let squareArea = width * height;

document.write(`넓이: ${squareArea}cm<sup>2</sup>`);
```

### 결과

넓이: 15cm<sup>2</sup>

<br>
<hr>

## 문제) 원의 넓이 출력

-   반지름이 5cm인 원의 넓이를 구해 화면에 출력
-   원주율은 3.14로 계산

### 해결 방법

-   반지름, 원주율(π) 변수 선언 및 초기화
-   넓이 변수를 선언하고 반지름 \* 반지름 \* 원주율 값으로 초기화
-   단위 추가 후 출력

### 코드

```javascript
let radius = 5;
const PI = 3.14;

let circleArea = radius * radius * PI;

document.write(`넓이: ${circleArea}cm<sup>2</sup>`);
```

### 결과

넓이: 78.5398cm<sup>2</sup>

<br>
<hr>

## 문제) 두 변수의 값 변경하기

-   두 변수가 각각 3, 5로 초기화 되어있다.
-   두 변수의 값을 각각 바꾸어 저장하고 화면에 출력하라.

### 해결 방법

-   임시 공간으로 사용할 temp 변수 생성
-   temp 변수에 첫 번째 변수의 값을 , 첫 번째 변수에 두 번째 변수의 값을 할당
-   두 번째 변수에 temp 변수의 값을 할당
-   출력

### 코드

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

### 결과

변경 전 num1: 3, num2: 5<br>
변경 후 num1: 5, num2: 3

<br>
