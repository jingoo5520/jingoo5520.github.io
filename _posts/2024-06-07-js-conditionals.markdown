---
layout: post
title: "조건문"
date: 2024-06-08 00:00:00 +0900
categories: javaScript
---

## 조건문

### if

#### 의사코드

```javascript
if(조건) {
    조건이 참인 경우 실행할 코드
}
```

> ex

```javascript
let num = 3;

if (a < 5) {
  num++;
}
```

<br>

### if-else

#### 의사코드

```javascript
if(조건) {
    조건이 참인 경우 실행할 코드
} else {
    조건이 참이 아닌 경우 실행할 코드
}
```

> ex

```javascript
let num = 3;
let type;

if (num % 2 == 0) {
  type = "짝수";
} else {
  type = "홀수";
}

console.log(type); // "홀수"
```

<br>

### if-else if-else

#### 의사코드

```javascript
if(조건1) {
    조건1이 참인 경우 실행할 코드
} else if(조건2) {
    조건1이 참이 아니고, 조건2가 참인 경우 실행할 코드
} else if(조건3) {
    조건1, 조건2가 참이 아니고, 조건3이 참인 경우 실행할 코드
} else {
    조건1, 조건2, 조건3이 참이 아닌 경우 실행할 코드
}
```

> ex

```javascript
let average = 72;
let grade;

if (average >= 90) {
  grade = "A";
} else if (average < 90 && average >= 80) {
  grade = "B";
} else if (average < 80 && average >= 70) {
  grade = "C";
} else if (average < 70 && average >= 60) {
  grade = "D";
} else {
  grade = "E";
}

console.log(average); // C
```

<br>

### switch-case

- 변수(조건)의 값에 따라 시작하는 코드가 달라짐

- break; 를 입력하지 않으면 해당 값의 코드부터 default 값의 코드까지 순차적으로 실행

- 변수(조건)의 값에 따라 각각 다른 코드가 실행 되어야 한다면 break; 를 사용

#### 의사코드

```javascript
switch(변수) {
    case 값1:
        변수의 값이 값1일 때 수행할 코드
        break;
    case 값2:
        변수의 값이 값2일 때 수행할 코드
        break;
    ...
    case 값n:
        변수의 값이 값n일 때 수행할 코드
        break;
    default:
        변수의 값이 위의 어느 것도 아닌 경우 수행할 코드
}
```

> ex

```javascript
let average = 72;
let grade;

switch (average / 10) {
  case 10:
  case 9:
    grade = "A";
    break;
  case 8:
    grade = "B";
    break;
  case 7:
    grade = "C";
    break;
  case 6:
    grade = "D";
    break;
  default:
    grade = "F";
}

console.log(grade); // "C"

// 만약 break문이 없다면?
// 경우가 average / 10 = 7 이므로 case 7: 코드부터 끝까지 실행하므로 최종적으로 grade = "F" 가 됨
```

###
