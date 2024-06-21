---
layout: post
title: "JavaScript를 이용한 데이터 출력 방법"
date: 2024-05-24 00:00:00 +0900
categories: javaScript
---

<!--
    ## 1. document.write()
    ## 2. window.alert()
    ## 3. console.log()
    ## 4. HTML 요소에 접근
-->

## 1. document.write()

메서드의 인자를 <p>태그안에 넣어 화면에 출력<br>
HTML 태그 적용

> ex

```javascript
document.write("<h3>Hello JavaScript</h3>");
```

> output

<p><h3>Hello JavaScript</h3></p>

<br>

## 2. window.alert()

메서드의 인자를 경고창을 통해 출력<br>
HTML 태그 미적용

> ex

```javascript
window.alert("Hello JavaScript");
```

<br>

## 3. console.log()

메서드의 인자를 콘솔창에 출력<br>
HTML 태그 미적용

> ex

```javascript
console.log("Hello JavaScript");
```

<br>

## 4. HTML 요소에 접근

HTML 요소의 속성에 직접 접근

> ex

```html
<div>저는 <span id="name">이름</span> 입니다.</div>
```

```javascript
document.getElementById("name").innerHTML = "홍길동";
```

> output

<div>저는 <span id="name">홍길동</span> 입니다.</div>

<br><br>
