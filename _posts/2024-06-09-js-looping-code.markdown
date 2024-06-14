---
layout: post
title: "반복문"
date: 2024-06-09 00:00:00 +0900
categories: javaScript
---

## 반복문

### for 반복문

-   어떤 조건이 거짓으로 판별될 때 까지 반복
-   초기화식, 종료 조건, 증감식을 가진 괄호와 바디로 구성
-   초기화식: 반복문 카운터 설정
-   종료 조건: 언제 반복을 멈춰야 하는지 조건 정의
-   증감식: 반복문이 1회 수행될 때마다 실행

#### 의사코드

```javascript
for(초기화식; 종료 조건; 증감식){
    반복 실행할 코드
}
```

> ex

```javascript
// 1부터 100까지 더하기
let sum = 0;

for (let i = 1; i < 101; i++) {
    sum += i;
}

console.log(sum); // 5050
```

<br>

### while 반복문

-   어떤 조건이 참이기만 하면 계속 반복
-   for 반복문의 요소들이 존재

#### 의사코드

```javascript
초기화식
while (종료 조건) {
    반복 실행할 코드

    증감식
}
```

> ex

```javascript
let sum = 0;

let i = 1;
while (i < 101) {
    sum += i;
    i++;
}

console.log(sum); // 5050
```

<br>

### do-while 반복문

-   조건이 거짓으로 판별될 때 까지 반복
-   먼저 실행하고, 조건을 확인

#### 의사코드

```javascript
초기화식
do {
    반복 실행할 코드
} while (종료 조건);
```

> ex

```javascript
let sum = 0;

let i = 1;
do {
    sum += i;
    i++;
} while (i < 101);

console.log(sum); // 5050
```

<br>

### for-in 반복문

-   배열의 경우 모든 요소의 인덱스에 대하여 반복

-   객체의 경우 모든 속성에 대하여 반복

#### 의사 코드

```javascript
for (반복요소 in 객체) {
    반복 수행할 코드
}
```

> ex

```javascript
let arr = [10, 20, 30];

for (index in arr) {
    console.log(index); // 0, 1, 2
}

let student = {
    name: "홍길동",
    korScore: 80,
    engScore: 90,
    mathScore: 88,
};

for (property in student) {
    console.log(property); // name, korScore, engScore, mathScore
}
```

<br>

### for-of 반복문

-   배열의 경우 모든 요소에 대하여 반복

-   객체의 경우 모든 속성값에 대하여 반복

#### 의사 코드

```javascript
for (반복요소 of 객체) {
    반복 수행할 코드
}
```

> ex

```javascript
let arr = [10, 20, 30];

for (element of arr) {
    console.log(element); // 10, 20, 30
}

let student = {
    name: "홍길동",
    korScore: 80,
    engScore: 90,
    mathScore: 88,
};

for (property of student) {
    console.log(property); // "홍길동", 80, 90, 88
}
```

<br>

### 반복문 중첩

#### 의사코드

```javascript
for(초기화식; 종료 조건; 증감식){
    반복 실행할 코드
    ...
    for(초기화식2; 종료 조건; 증감식) {
        반복 실행할 코드2
    }
    ...
}
```

> ex

```javascript
for (let i = 2; i < 10; i++) {
    for (let j = 1; j < 10; j++) {
        console.log(`${i} * ${j} = ${i * j}`);
    }
}
```

> 결과

2 \* 1 = 2<br>
2 \* 2 = 4<br>
2 \* 3 = 6<br>
...<br>
9 \* 8 = 72<br>
9 \* 9 = 81<br>

<br>
<hr>
<br>

## 반복문 제어

### continue

-   반복문에서 현재 반복을 중단하고 다음 반복을 시작하기 위해서 사용

> ex

```javascript
// 1부터 100까지의 숫자 중 짝수들의 합
let sum = 0;

for (let i = 1; i < 101; i++) {
    if (i % 2 != 0) {
        // 홀수 인 경우 다음 반복 실행
        continue;
    }
    sum += i;
}

console.log(sum); // 5050
```

<br>

### break

-   반복을 종료하고 다음 코드로 넘어감

> ex

```javascript
let i = 0;
while (i < 10) {
    // i 가 5인 경우 반복문 종료
    if (i == 5) {
        break;
    }
    console.log(`${i + 1}번 째 반복중`);

    i++;
}
```
