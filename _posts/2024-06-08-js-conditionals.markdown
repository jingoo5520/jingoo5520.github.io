---
layout: post
title: "조건문"
date: 2024-06-08 00:00:00 +0900
categories: javaScript
---

<!--
    ## if 문
    ## if - else 문
    ## if - else if - else 문
    ## switch - case 문
    ## 예제 문제
-->

## if 문

> pseudocode

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

## if - else 문

> pseudocode

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

## if- else if -else 문

> pseudocode

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

## switch-case

-   변수(조건)의 값에 따라 시작하는 코드가 달라짐

-   break; 를 입력하지 않으면 해당 값의 코드부터 default 값의 코드까지 순차적으로 실행

-   변수(조건)의 값에 따라 각각 다른 코드가 실행 되어야 한다면 break; 를 사용

> pseudocode

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

<br>
<hr>
<br>

## 예제 문제

### 문제) 성적 출력

-   HTML, CSS, JS 세 과목의 점수를 입력받아 합격 여부를 출력하라.
-   과목당 40점 이상이고 평균이 60점 이상인 경우만 합격으로 인정한다.

#### 해결 방법

-   각 과목에 대한 변수를 선언
-   window.prompt() 메서드를 이용해 세 과목의 점수를 입력받음
-   평균 점수에 대한 변수 선언, 초기화
-   조건문을 이용해 점수에 따라 합격 여부 출력

#### 코드

```javascript
// window.prompt() 메서드의 반환 타입은 문자열이기 때문에 숫자 타입으로 변환
let html = Number(window.prompt("html 과목의 점수를 입력하세요"));
let css = Number(window.prompt("css 과목의 점수를 입력하세요"));
let js = Number(window.prompt("js 과목의 점수를 입력하세요"));

let total = html + css + js; // 세 과목의 합산 점수
let avg = total / 3; // 평균 점수
let result; // 합격 여부

if (avg >= 60) {
    if (html >= 40 && css >= 40 && js >= 40) {
        result = "합격";
    } else {
        result = "불합격";
    }
} else {
    result = "불합격";
}

document.write(
    `html: ${html}, css: ${css}, js: ${js}, avg: ${avg}, result: ${result}`
);
```

#### 결과

html: 80, css: 90, js: 84, avg: 84.66666666666667, result: 합격

<br><br>

### 문제) 랜덤 메뉴 추천

1 ~ 7 랜덤한 숫자를 뽑아서 숫자에 따라 다른 음식의 이름과 사진을 출력하라.

#### 해결 방법

-   Math.random() 메서드를 이용해 랜덤 숫자 뽑기
-   음식명, 음식사진에 대한 변수 선언
-   뽑은 숫자에 따라 음식명, 음식사진 변수에 값 할당후 출력

#### 코드

```javascript
// Math.random() 메서드는 0 < x < 1 범위 내의 랜덤한 숫자를 반환
// 반환값에 7을 곱해주면 범위가 0 < x < 7
// 여기에 1을 더해주면 1 < x < 8
// 최종적으로 Math.floor() 메서드를 이용해 소수점을 때버리면 1 ~ 7의 랜덤한 정수값을 얻을 수 있음
let randNum = Math.floor(Math.random() * 7 + 1);

let foodName; // 음식 이름
let foodImg; // 음식 사진

// 숫자 따라 다른 값 할당
if (randNum == 1) {
    foodName = "짜장면";
    foodImg = "img/foods/jajangmyeon.jpg";
} else if (randNum == 2) {
    foodName = "짬뽕";
    foodImg = "img/foods/jjambbong.jpg";
} else if (randNum == 3) {
    foodName = "비빔밥";
    foodImg = "img/foods/bibimbap.jpg";
} else if (randNum == 4) {
    foodName = "돈가스";
    foodImg = "img/foods/dongaseu.jpg";
} else if (randNum == 5) {
    foodName = "김치전";
    foodImg = "img/foods/gimchijeon.jpg";
} else if (randNum == 6) {
    foodName = "유부초밥";
    foodImg = "img/foods/tofu-sushi.jpg";
} else {
    foodName = "떡볶이";
    foodImg = "img/foods/tteokbokki.jpg";
}

// script 코드가 먼저 읽히기 때문에
// 페이지가 로드되고 자동으로 호출되는 window.onload 메서드를 재정의
window.onload = function () {
    document.getElementById("foodName").innerHTML = foodName;
    document.getElementById("foodImg").src = foodImg;
};
```

```html
<h1>오늘의 추천 메뉴</h1>
<div id="foodName"></div>
<img id="foodImg" src="" width="400px" height="400px" />
```

<br><br>

### 문제) switch-case 문을 이용한 랜덤 메뉴 추천

#### 코드

```javascript
switch (randNum) {
    case 1:
        foodName = "짜장면";
        foodImg = "img/foods/jajangmyeon.jpg";
        break;
    case 2:
        foodName = "짬뽕";
        foodImg = "img/foods/jjambbong.jpg";
        break;
    case 3:
        foodName = "비빔밥";
        foodImg = "img/foods/bibimbap.jpg";
        break;
    case 4:
        foodName = "돈가스";
        foodImg = "img/foods/dongaseu.jpg";
        break;
    case 5:
        foodName = "김치전";
        foodImg = "img/foods/gimchijeon.jpg";
        break;
    case 6:
        foodName = "유부초밥";
        foodImg = "img/foods/tofu-sushi.jpg";
        break;
    case 7:
        foodName = "떡볶이";
        foodImg = "img/foods/tteokbokki.jpg";
        break;
}
```

<br><br>

### 문제) 가위바위보

-   컴퓨터와 가위바위보를 한다.
-   컴퓨터는 랜덤하게 가위, 바위, 보를 낸다.
-   유저는 가위, 바위, 보 셋중 하나를 선택하여 [선택] 버튼을 눌러 게임을 시작한다.
-   한 게임당 게임 결과와 누적 승률을 출력한다.

#### 해결 방법

-   1: 바위, 2: 보, 3: 가위로 가정
-   컴퓨터가 낸 것은 1 ~ 3 의 랜덤 숫자로 결정
-   선택 버튼의 onclick 속성에 게임 시작 함수 추가
-   경우에 따라 승패를 결정하고 승리 수 / 무승부를 제외한 게임 수를 이용해 승률 출력

#### 코드

```javascript
let game = 0; // 게임 수
let win = 0; // 승리
let lose = 0; // 패배
let draw = 0; // 무승부
let rate; // 승률

function playGame() {
    // user: select 태그의 값( 1 ~ 3 )
    let user = Number(document.getElementById("userSelectVal").value);
    // computer: 1 ~ 3 의 랜덤 숫자
    let computer = Math.floor(Math.random() * 3 + 1);


    if (user == computer) {
        // 무승부인 경우
        result = "무승부";
        draw += 1;
    } else {
        // 승패가 결정난 경우
        if (
            (user == 1 && computer == 2) ||
            (user == 2 && computer == 3) ||
            (user == 3 && computer == 1)
        ) {
            result = "컴퓨터승";
            lose += 1;
        } else {
            result = "유저승";
            win += 1;
        }
    }
    // 게임 횟수 증가
    game++;

    // 승률 계산
    rate = (win / (win + lose)) * 100;

    // 문서 수정
    ...
}
```

```html
<!-- 유저 선택, 게임 실행 -->
<select id="userSelectVal">
    <option value="1">바위</option>
    <option value="2">보</option>
    <option value="3">가위</option>
</select>
<input type="button" value="선택" onclick="playGame()" />
```

<br><br>

### 문제) 체질량 지수(BMI: Body mass index) 구하기

-   input 태그를 이용해 키와 몸무게를 입력받아 체질량 지수를 계산하라.
-   체질량 지수와, 비만 여부를 출력하라.
-   BMI = 체중(kg) / 신장(m)

#### 해결 방법

-   input 태그의 value 를 가져와 키, 몸무게에 대한 변수 초기화
-   bmi와 bmi 수치에 따른 비만 여부 계산후 출력

#### 코드

```javascript
function calBMI() {
    // input 태그로 부터 height, weight 값을 받아옴
    let height = Number(document.getElementById("height").value);
    let weight = Number(document.getElementById("weight").value);

    let bmi = (weight / (height / 100) ** 2).toFixed(2);

    let result;
    if (bmi < 18.5) {
        result = "저체중";
    } else if (bmi <= 22.9) {
        result = "정상";
    } else if (bmi <= 24.9) {
        result = "비만전단계";
    } else if (bmi <= 29.9) {
        result = "1단계 비만";
    } else if (bmi <= 34.9) {
        result = "2단계 비만";
    } else {
        result = "3단계 비만";
    }

    document.getElementById("bmi").innerHTML = bmi;
    document.getElementById("result").innerHTML = result;
}
```

```html
<input id="height" type="text" placeholder="키를 입력하세요(cm)" /><br />
<input id="weight" type="text" placeholder="몸무계를 입력하세요(kg)" />

<div>BMI: <span id="bmi"></span></div>
<div>분류: <span id="result"></span></div>
```
