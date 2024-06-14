---
layout: post
title: "반복문 예제문제"
date: 2024-06-09 01:00:00 +0900
categories: javaScript
---

## 문제) 1부터 n까지 홀수끼리의 합, 짝수끼리의 합

-   사용자에게 숫자를 입력받아 1부터 입력받은 숫자까지의 홀수끼리의 합, 짝수끼리의 합을 구하라.

### 해결 방법

-   홀수끼리의 합에 대한 변수 sumOdd, 짝수끼리의 합에 대한 변수 sumEven 선언후 둘 다 0으로 초기화
-   i를 1부터 1씩 증가시켜가며 n번 반복수행
-   반복마다 i가 짝수인 경우 sumEven += i, i가 홀수인 경우 sumOdd += i

### 코드

```javascript
let num = window.prompt("숫자를 입력하세요.");

let sumOdd = 0;
let sumEven = 0;
for (let i = 1; i <= num; i++) {
    if (i % 2 == 0) {
        // i가 짝수인 경우
        sumEven += i;
    } else {
        // i가 홀수인 경우
        sumOdd += i;
    }
}

console.log(`sumOdd: ${sumOdd}, sumEven: ${sumEven}`);
```

### 결과

ex) 100 입력<br>
sumOdd: 2500, sumEven: 2550

<br>
<hr>

## 문제) 1 ~ n 누적합이 1000을 넘길 때?

1부터 임의의 숫자 n까지 더하는데, 누적합이 1000을 딱 넘어가는 n을 구하라.

### 해결 방법

-   누적 합에 대한 변수 sum 선언
-   n 을 1부터 1씩 증가시키며 sum += n 반복
-   sum 이 1000을 넘는 순간 반복 중지
-   n값 출력

### 코드

```javascript
let n = 1;
let sum = 0;

// sum이 1000보다 크면 중단
while (sum < 1000) {
    // n을 1 증가시키고 sum에 더함
    n++;
    sum += n;
}

console.log(n); // 45
```
