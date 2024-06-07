---
layout: post
title: "데이터 출력 방법"
date: 2024-05-24 00:00:00 +0900
categories: javaScript
---

## JavaScript를 이용한 데이터 출력 방법

### 1. document.write()

메서드의 인자를 <p>태그안에 넣어 화면에 출력<br>
HTML 태그 적용

> input

```javascript
document.write("<h3>Hello JavaScript</h3>");
```

> output

<p><h3>Hello JavaScript</h3></p>

<br>

### 2. window.alert()

메서드의 인자를 경고창을 통해 출력<br>
HTML 태그 사용 미적용

> input

```javascript
window.alert("Hello JavaScript");
```

<br>

### 3. console.log()

메서드의 인자를 콘솔창에 출력<br>
HTML 태그 사용 미적용

> input

```javascript
console.log("Hello JavaScript");
```

<br>

### 4. HTML 요소에 접근

HTML 요소의 속성에 직접 접근

> input

```html
<div>저는 <span id="name">이름</span> 입니다.</div>
```

```javascript
document.getElementById("name").innerHTML = "홍길동";
```

> output

<div>저는 <span id="name">홍길동</span> 입니다.</div>

<br><br>

## 관련 에러들

### script 적용 안됨

script 태그 내에서 HTML 요소에 접근하여 속성 값을 변경시켰으나 적용이 안됨

> ex

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        ...
        <script>
            document.getElementById("name").innerHTML = "홍길동";
        </script>
    </head>
    <body>
        <div>저는 <span id="name">이름</span> 입니다.</div>
    </body>
</html>
```

<br>

> output

<div>저는 <span id="name">이름</span> 입니다.</div>

> error

```
Uncaught TypeError: Cannot set properties of null (setting 'innerHTML')
```

<br>

> 에러 발생 이유

코드는 위에서 부터 읽힘<br>
body 태그에 있는 id="name" 인 요소를 읽기 전에 document.getElementById("name") 코드로 해당 요소를 읽으려 함

<br>

> 해결 방법 1)

script 코드를 요소 아래에 위치

```html
<body>
    <div>저는 <span id="name">이름</span> 입니다.</div>
    <script>
        document.getElementById("name").innerHTML = "홍길동";
    </script>
</body>
```

<br>

> 해결 방법 2)

window.onload() 메서드 오버라이드(재정의)<br>
페이지 로드시 자동으로 실행되는 전역 콜백함수

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        ...
        <script>
            window.onload = function () {
                document.getElementById("name").innerHTML = "홍길동";
            };
        </script>
    </head>
    <body>
        <div>저는 <span id="name">이름</span> 입니다.</div>
    </body>
</html>
```
