---
layout: post
title: "연산자"
date: 2024-06-07 00:00:00 +0900
categories: javaScript
---

## 연산자

### 산술 연산자

#### 종류

`+` 더하기 연산자<br>
`-` 빼기 연산자<br>
`*` 곱하기 연산자<br>
`/` 나누기 연산자<br>
`%` 나머지 연산자<br>
`**` 지수 연산자<br>

> ex

```javascript
let a = 10;
let b = 5;

console.log(a + b); // 15
console.log(a - b); // 5
console.log(a * b); // 50
console.log(a / b); // 2
console.log(a % b); // 0
console.log(a ** 2); // 100
console.log(a + 2 * 3); // 16
console.log((a + 2) * 3); // 36
```

#### 우선순위

`**` > `*` = `/` = `%` > `+` = `-`

<br>

### 증감 연산자

- 반복해서 숫자 변수의 값을 1씩 더하거나 빼고 싶을 때 사용
- 숫자에 직접 사용할 수는 없음
- 연산자의 위치에 따라 전치, 후치연산 을 실행

#### 종류

`++` 증가 연산자<br>
`--` 감소 연산자

#### 전치연산과 후치연산

**전치연산**: 선증감 후대입, 변수 뒤에 연산자가 위치하며 변수를 증감 후 대입<br>
**후치연산**: 선대입 후증감, 변수 앞에 연산자가 위치하며 변수를 대입 후 증감

> ex

```javascript
let a = 10;
let b = 5;

// 전치연산
// a 값을 1 증가 시킨 후 출력
console.log(++a); // 11
// 재출력시 증감 확인
console.log(a); // 11

// 후치연산
// a 값을 출력한 뒤 1 증가
console.log(a++); // 11
// 재출력시 증감 확인
console.log(a); // 12

console.log(a--); // 12
console.log(a); // 11

console.log((b++) ** 2); // 25
console.log(b); // 6
```

<br>

### 비교 연산자

피연산자들을 비교하여 결과에 따라 true, false 반환

#### 종류

`==` Eqaul<br>
`!=` Not equal<br>
`===` Strict equal<br>
`!==` Strict not equal<br>
`>` Greater than or equal<br>
`>=` Greater than or equal<br>
`<` Less than<br>
`<=` Less than or equal<br>

> ex

```javascript
let a = 3;
let b = 5;

console.log(a > b); // false
console.log(a == b); // false
console.log(a != b); // true
console.log(a++ == b); // false, a = 4
console.log(++a == b); // true
console.log(b % 2 == 0); // false
```

<br>

### 논리 연산자

#### 종류

`&&` Logical AND<br>
두 피연산자가 참인 경우 true, 외에는 false 반환

<br>

`||` Logical OR<br>
두 피연산자중 하나라도 참인 경우 true, 모두 거짓인 경우 false 반환

<br>

`!` Logical NOT<br>
단일 피연산자가 참인 경우 false, 거짓인 경우 true 반환

> ex

```javascript
let a = 3;
let b = 5;

console.log(a == 3 && b == 5); // true
console.log(a > b && b == 3); // false
console.log(a == 3 && a < b && b % 2 == 1); // true

console.log(a > 2 || b == 6); // true
console.log(a < 0 || b > 0); // true
console.log(a == 5 || b == 3); // false
console.log(a < 0 || b < 0); // false

// 0, null, NaN, 빈 문자열(""), undefined 를 제외한 모든 숫자, 문자는 true 반환
console.log(!a); // false
console.log(!0); // true
console.log(!3.2); // false
console.log(!null); // true
```

<br>

### 할당 연산자

#### 종류

`=` Assignment<br>
`+=` Addition assignment<br>
`-=` Subtraction assignment<br>
`*=` Multiplication assignment<br>
`/=` Division assignment<br>
`%=` Remainder assignment<br>
...

> ex

```javascript
let num = 3;

num += 3; // num = num + 3;
console.log(num); // 6

num *= 2; // num = num * 2;
console.log(num); // 12

num %= 2; // num = num % 2;
console.log(num); // 0
```

<br>

### 삼항 연산자

세 개의 피연산자를 받음
주어진 조건에 따라 두 값중 하나를 반환

`condition ? val1 : val2`

> ex

```javascript
let a = 10;
let result;

// a % 2 == 0 이 참이면 "짝수", 거짓이면 "홀수" 반환
result = a % 2 == 0 ? "짝수" : "홀수";

console.log(`a는 ${result}입니다.`); // a는 짝수입니다.
```

<br>

### 비트 연산자

<br>

### 연산자 우선순위

**증감 연산자(후위연산)** > **논리 연산자 NOT** > **증감 연산자(전위연산)** > **산술 연산자** > **비교 연산자** > **논리 연산자 AND** > **논리연산자 OR** > **삼항 연산자** > **할당 연산자**
