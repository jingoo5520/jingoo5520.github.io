---
layout: post
title: "변수와 상수"
date: 2024-05-24 00:00:00 +0900
categories: javaScript
---

## JavaScript 변수와 상수

### 변수

변할 수 있는 값을 저장하기 위한 저장소

#### 변수 선언과 초기화

`let` 키워드를 사용하여 변수 선언

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

#### 변수 타입

다른 프로그래밍 언어와 달리 변수 타입을 선언할 필요가 없음

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

### 상수

-   변하지 않는 값을 저장하는 저장소<br>
-   선언과 동시에 초기화해야함<br>
-   초기화 후에는 새로운 값 할당 불가<br>
-   가능하다면 `const`를 사용하고 필요한 경우 `let`사용을 권장<br>

```javascript
// 선언과 동시에 초기화
const PI = 3.14;

PI = 5; // 재할당 불가, 에러발생
```

<br>

### 변수, 상수 명명 규칙

-   영문자나 숫자, '밑줄 문자(\_), '$' 문자를 사용

-   첫 글자는 숫자로 시작할 수 없음

-   포함된 데이터를 설명할 수 있도록 직관적으로 만들어야 함

-   영문자는 대, 소문자를 구분함

-   카멜 표기법(Camel Case)을 따름

-   상수는 대문자만으로 쓰되, 두 단어 이상 결합하는 경우 밑줄 문자(\_)를 사용

-   예약어(키워드)는 사용할 수 없음

-   공백은 포함할 수 없음

<br>

### 여러가지 표기법

#### 카멜 표기법(Camel Case)

```javascript
// 첫 단어는 소문자로 시작하고, 이후 단어들의 첫 글자는 대문자로 시작
let phoneNumber;
```

#### 파스칼 표기법(Pascal Case)

```javascript
// 모든 단어의 첫 글자를 대문자로 시작
let PhoneNumber;
```

#### 케밥 표기법(Kebab Case)

```javascript
// 모든 단어를 소문자로 작성하되 단어 사이를 하이픈(-)로 구분
let phone-number;
```

#### 스네이크 표기법 (Snake Case)

```javascript
// 모든 단어를 소문자로 작성하되 단어 사이를 밑줄(_)로 구분
let phone_number;
```

<br>
