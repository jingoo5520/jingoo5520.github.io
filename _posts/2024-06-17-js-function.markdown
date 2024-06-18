---
layout: post
title: "함수"
date: 2024-06-17 00:00:00 +0900
categories: javaScript
---

<!--
    ## 함수

    ### 함수와 메서드
    ### 함수 선언
    ### 함수 호출
    ### 함수의 매개변수
    #### 기본 매개변수
    #### 가변 매개변수
    ### 함수의 반환값
    ### 화살표 함수
    ### 익명 함수
    ### 즉시 실행 함수
    ### 내장 함수
    ### 재귀 함수

-->

## 함수(Function)

### 함수와 메서드

**함수(Function)**<br>

-   독립적인 코드 블록
-   주어진 매개변수를 받아 특정 작업을 수행하고 결과를 반환
-   `return` 키워드를 사용하여 값을 반환하고, 만약 사용하지 않는다면 undefined 를 반환

**메서드(Method)**<br>

-   객체에 속한 <b>함수</b>
-   객체의 동작을 정의

<br>

### 함수 선언

#### 의사 코드

```javascript
function 함수이름() {
    코드;
}
```

> ex

```javascript
// 콘솔창에 hello를 출력하는 함수
function sayHi() {
    console.log("hi");
}
```

<br>

### 함수 호출

함수 선언은 호이스팅(hoisting) 되기 때문에, 함수 선언문 이전에 호출 가능

<br>

**호이스팅(hoisting)**

-   자바스크립트의 특성 중 하나
-   변수와 함수의 선언이 스코프의 최상단으로 끌어올려지는 것 처럼 동작하는 현상
-   `var`로 선언된 변수는 호이스팅시 undefined로 초기화됨
-   `let`, `const`로 선언된 변수는 호이스팅시 초기화 되지 않으며 선언 이전에 접근 불가

<br>

> ex

```javascript
sayHi(); // hi

function sayHi() {
    console.log("hi");
}
```

<br>

### 함수의 매개변수(Parameters)

-   함수의 정의에서 전달받은 인수를 함수 내부로 전달하기 위해 사용하는 변수
-   항상 필요한 것은 아님

> ex

```javascript
// 두 숫자를 더해 콘솔창에 출력하는 함수
function sum(num1, num2) {
    let sum = num1 + num2;

    console.log(sum);
}
```

#### 기본 매개변수(Default Parameters)

-   매개변수의 기본값을 지정할 수 있음

> ex

```javascript
function sum(num1, num2 = 5) {
    let sum = num1 + num2;

    console.log(sum);
}

sum(5, 10); // 15
sum(5); // 10
```

#### 가변 매개변수(Rest Parameters)

-   함수에 전달될 인수의 수가 불확실할 때 사용

> ex

```javascript
function sum(...numbers) {
    let sum = 0;

    for (number of numbers) {
        sum += number;
    }

    console.log(sum);
}

sum(1, 2, 3, 4); // 10
sum(1, 2); // 3
sum(); // 0
```

<br>

### 함수의 반환값

<br>

### 화살표 함수(Arrow Function)

-   간결한 구문으로 함수 정의

```javascript
// 일반 함수
function sum(num1, num2) {
    let sum = num1 + num2;
    return sum;
}

// 화살표 함수
const sum = (num1, num2) => {
    let sum = num1 + num2;
    return sum;
};

// 함수의 코드에 단순 반환만 있는 경우라면 중괄호, return 키워드 생략 가능
const sum = (num1, num2) => num1 + num2;

console.log(sum(10, 20)); // 30
```

<br>

### 익명 함수(Anonymous Function)

-   이름이 없는 함수
-   변수에 함수 코드를 저장하는 방식

> ex

```javascript
let num = function (num1, num2) {
    return num1 + num2;
};

console.log(num(3, 5)); // 8
```

<br>

### 즉시 실행 함수(IIFE)

-   정의되자마자 실행되는 함수

<br>

### 내장 함수(Built-in functions)

-   언어가 기본적으로 제공하는 함수
-   직접 정의하지 않아도 사용 가능

#### 문자열을 숫자로 변환

`parseInt()` 정수 변환<br>
`parseFloat()` 실수 변환

> ex

```javascript
let str = "123";
let num = parseInt(str);

console.log(num); // 123
console.log(typeof num); // number

// 숫자로 변환할 수 있는 문자 + 변환 불가한 문자의 경우
// 숫자로 변환할 수 있는 문자만 잘라서 변환
// 반드시 숫자로 변환할 수 있는 문자 뒤에 변환 불가한 문자가 와야 함
let str2 = "18세 입니다.";
let num2 = parseInt(str2);

console.log(num2); // 18

// 변환 후 정수부분만 반환
let str3 = "3.14";
let num3 = parseInt(str3);

console.log(num3); // 3
```

#### 숫자인지 아닌지 판별

`isNan()` Nan\*인지 확인<br>

<br>

**Nan(Not a number)**<br>
숫자가 아님을 나타냄

> ex

```javascript
// 숫자인 경우 false, 숫자가 아닌 경우 true 반환
console.log(isNaN(3)); // false
console.log(isNaN("홍길동")); // true
// null 은 NaN이 아님
console.log(isNaN(null)); // false
// 숫자로 변환 가능한 문자는 변환 후 판별
console.log(isNaN("3")); // false;
console.log(isNaN("")); // false;
```

<br>

#### 유한수 인지 아닌지 판별

`isFinite()`

```javascript
console.log(isFinite(1 / 0)); // false, 무한
console.log(isFinite(3.14)); // true true
console.log(isFinite("숫자")); // false
```

<br>

#### 인코딩과 디코딩

`encodeURIComponent()` 인코딩<br>
`decodeURIComponent()` 디코딩<br>

A-Z a-z 0-9 - \_ . ! ~ \* ' ( ) 문자를 제외한 문자를 인코딩

> ex

```javascript
let str = "자바script!";

let encodedStr = encodeURIComponent(str);

console.log(encodedStr); // %EC%9E%90%EB%B0%94script

console.log(decodeURIComponent(encodedStr)); // 자바script!
```

<br>

### 재귀 함수(recursive Function)

-   함수가 자기 자신을 호출하는 함수

#### 의사 코드

```javascript
function recursiveFunc(param) {
    if (baseCondition) {
        // 끝나는 조건 설정
        return;
    }
    recursiveFunc(modifiedParam);
}
```

> ex

```javascript
function recursiveFunc(n) {
    console.log(`재귀함수 호출, ${n}`);
    if (n == 0) {
        console.log(`완료`);
        return;
    }
    recursiveFunc(n - 1);
}

recursiveFunc(10);

// 재귀함수 호출, 10
// 재귀함수 호출, 9
// 재귀함수 호출, 8
// ...
// 재귀함수 호출, 1
// 재귀함수 호출, 0
// 완료
```
