---
layout: post
title: "자바스크립트 내장 객체"
date: 2024-06-18 01:00:00 +0900
categories: javaScript
---

<!--
배열 객체(Array Object)
문자열(String Object)

-->

## Array Object

### 속성

#### 배열의 크기(요소 개수)

`length`<br>

> ex

```javascript
let arr = new Array(5);

for (let i = 0; i < arr.length; i++) {
    arr[i] = i;
}

console.log(arr); // [0, 1, 2, 3, 4]
```

<br>

### 메서드

#### 배열의 끝에 요소 추가

`push(item1, [item2, item3, ...])`

> ex

```javascript
let arr = [0, 1, 2, 3, 4];

arr.push(5, 6, 7);

console.log(arr); // [0, 1, 2, 3, 4, 5, 6, 7]
```

#### 배열의 특정 위치에 요소 추가, 제거, 교체

`splice(index, [count, item1, item2, ...])`<br>
**index**: 요소 추가 시작 인덱스<br>
**count**: index번 부터 제거할 요소의 개수<br>
**item**: 추가할 요소<br>
<br>

**index** 번에서 부터 **count** 개수만큼의 요소를 제거하고 **item** 요소들을 추가

> ex

```javascript
let arr = [0, 1, 2, 3, 4];

arr.splice(3, 0, 2.5);

console.log(arr); // [0, 1, 2, 2.5, 3, 4]

arr.splice(2, 2);

console.log(arr); // [0, 1, 3, 4]
```

#### 배열의 마지막 요소 제거

`pop()`

> ex

```javascript
let arr = [0, 1, 2, 3, 4];

arr.pop();

console.log(arr); // [0, 1, 2, 3]
```

#### 특정 index 의 요소 구하기

`at([index])`<br>
**index**: (default: 0)<br>

> ex

```javascript
let arr = [0, 1, 2, 3, 4];

console.log(arr.at()); // 0
console.log(arr.at(3)); // 3
```

#### 배열 뒤집기

`reverse()`<br>

> ex

```javascript
let arr = [0, 1, 2, 3, 4];

arr.reverse();

console.log(arr); // [4, 3, 2, 1, 0]
```

#### 배열의 일부 복사본 만들기

`slice([start, end])`<br>
**start**: 시작 인덱스(default: 0)<br>
**end**: 끝 인덱스(default: last index)<br>

<br>

-   start 인덱스부터 end 인덱스 전 인덱스 까지의 배열을 잘라 새로운 배열 객체 반환
-   원본은 변하지 않음

> ex

```javascript
let arr = [0, 1, 2, 3, 4];

let arr2 = arr.slice(1, 4);

console.log(arr); // [0, 1, 2, 3, 4] -> 원본 유지
console.log(arr2); // [1, 2, 3]
```

#### 배열의 각 요소에 접근

`forEach(function(currentValue, [index, arr]), [thisValue])`<br>
**function(currentValue, [index, arr])**: 각 요소 차례 마다 실행할 함수<br>
**thisValue**

> ex

```javascript
let arr = [0, 1, 2, 3, 4];
let sum = 0;

// 배열의 각 요소를 더한 값 출력
arr.forEach(function (item) {
    sum += item;
});

console.log(sum); // 10

// 배열의 각 요소에 곱하기 2
arr.forEach(function (item, index, array) {
    array[index] = item *= 2;
});

console.log(arr); // [0, 2, 4, 6, 8]
```

<br>
<hr>
<br>

## String Object

-   문자열은 배열이 아니지만 배열처럼 다룰 수 있음
-   문자열의 개별 문자를 수정할 수 없음
-   인덱스를 이용하여 각 문자에 접근 가능

### 속성

#### 문자열 길이

`length`<br>

> ex

```javascript
const name = "jingoo";

console.log(str.length); // 6
```

<br>

### 메서드

#### n 번째 문자 찾기

`charAt([index])`

> ex

```javascript
const name = "jingoo";

const char0 = charAt(0);
console.log(char0); // j

const char3 = charAt(3);
console.log(char3); // g

// 인덱스를 이용하여 각 문자에 접근 가능
console.log(name[0]); // j
console.log(name[3]); // g
```

#### 문자열 붙이기

`concat(string1, [string2, string3 ...])`

> ex

```javascript
let str = new String("우리나라");

let newStr = str.concat(" 대한민국", " 만세");

console.log(newStr); // 우리나라 대한민국 만세
```

#### 하위 문자열 index 찾기

`indexOf(searchValue, [start])`

> ex

```javascript
let str = "우리나라 대한민국 만세";

let index = str.indexOf("라");

console.log(index); // 3
```

#### 대/소문자 변경

`toLowerCase()`<br>
`toUpperCase()`<br>

> ex

```javascript
let str = "I am a student";

console.log(str.toUpperCase()); // I AM A STUDENT
console.log(str.toLowerCase()); // i am a student
```

#### 문자열 분해

구분자를 기준으로 문자열을 각각 나누어 배열로 저장

`split([seperator, limit])`<br>

> ex

```javascript
const str = "I am a student";

// seperator 매개변수를 넣지 않는 경우
console.log(str.split()); // ['I am a student']
console.log(str.split(" ")); // ['I', 'am', 'a', 'student']
```

#### 문자열 일부 분리

`substring(start, [end])`<br>

> ex

```javascript
const str = "I am a student";

console.log(str.substring(7)); // student
console.log(str.substring(2, 4)); // am
```

#### 문자열 대체하기

`replace(searchValue, newValue)`<br>

> ex

```javascript
const str = "I am a student";

console.log(str.replace("a student", "Iron Man")); // I am Iron Man
```

#### 문자열 채우기

-   문자열의 특정 부분부터 목표 길이를 만족할 때 까지 지정한 문자열로 채움

`padStart(length, [string])` 앞에서부터 채움<br>
`padStart(length, [string])` 뒤에서부터 채움<br>

**length**: 목표 길이<br>
**string**: 빈 공간을 채울 문자열(default: " ")<br>

> ex

```javascript
let num = "3";

console.log(num.padStart(2, "0")); // 03
console.log(num.padEnd(3, "0")); // 300
```

<br>
<hr>
<br>

## Date Object

날짜와 시간을 다루는 객체

### 정적 메서드

#### 1970년부터 특정 날짜까지의 시간

`now()` 지금 까지의 시간<br>
`parse(dateString)` 특정 날짜 까지의 시간<br>

> ex

```javascript
let day = new Date(2024, 6, 1);

console.log(day); // Mon Jul 01 2024 00:00:00 GMT+0900 (한국 표준시)

console.log(Date.now()); // 1970년 1월 1일 00:00:00(UTC)로 부터 지난 시간을 밀리초 단위의 숫자 값으로 반환

console.log(Date.parse(day)); // 1970년 1월 1일 00:00:00(UTC)로 부터 특정 날짜 까지의 시간을 밀리초 단위의 숫자 값으로 반환
```

### 인스턴스 메서드

#### 현지 시간 반환

`getDate()` 현지 시간 기준 일(1~31) 반환<br>
`getDay()` 현지 시간 기준 요일(0~6) 반환<br>
`getFullYear()` 현지 시간 기준 연도 반환<br>
`getMonth()` 현지 시간 기준 월(0~11) 반환<br>
`getHours()` 현지 시간 기준 시(0~23) 반환<br>
`getMinutes()` <br>
`getSeconds()` <br>
...

> ex

```javascript
let day = new Date(2024, 5, 1); // 2024년 6월 1일

console.log(day); // Thu Jun 01 2024 00:00:00 GMT+0900 (한국 표준시)

let year = day.getFullYear();
let month = day.getMonth();
let date = day.getDate();

console.log(`${year}년 ${month + 1}월 ${date}일`); // 2024년 6월 1일
```

#### 시간 설정

`setDate()` 현지 시간 기준 일 설정<br>
`setFullYear()` 현지 시간 기준 연도 설정<br>
`setMonth()` 현지 시간 기준 월 설정<br>
`setHours()` 현지 시간 기준 시 설정<br>
`setMinutes()` <br>
`setSeconds()` <br>
...

> ex

```javascript
let day = new Date(2024, 5, 1); // 2024년 6월 1일

console.log(day); // Thu Jun 01 2024 00:00:00 GMT+0900 (한국 표준시)

day.setFullYear(2023);
day.setMonth(0);
day.setDate(20);

console.log(day); // Fri Jan 20 2023 00:00:00 GMT+0900 (한국 표준시)
```

<br>
<hr>
<br>

## Math Object

### 정적 속성

#### 원의 둘레와 지름의 비율. 약 3.14159

`PI`

> ex

```javascript
console.log(Math.PI); // 3.141592653589793
```

### 정적 메서드

#### 난수 반환

`random()`

> ex

```javascript
let randNum1 = Math.random(); // 0 < randNum1 < 1

let randNum2 = Math.random() * 10; // 0 < randNum2 < 10

let randNum3 = Math.random() * 10 + 1; // 1 < randNum3 < 11

// 1부터 100까지의 숫자 중 하나를 랜덤으로 뽑기
console.log(Math.floor(Math.random() * 100 + 1));
```

#### 소수점 정리

`ceil()` 소수점 올림<br>
`floor()` 소수점 내림<br>
`round()` 소수점 반올림

> ex

```javascript
const PI = 3.14;

console.log(Math.ceil(PI)); // 4
console.log(Math.floor(PI)); // 3
console.log(Math.round(PI)); // 3

const num = -1.4;

console.log(Math.ceil(num)); // -1
console.log(Math.floor(num)); // -2
console.log(Math.round(num)); // -1
```
