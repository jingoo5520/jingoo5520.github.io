---
layout: post
title: "Java Array"
date: 2024-07-16 00:00:00 +0900
categories: JAVA
---

## 배열

-   같은 타입의 여러 데이터를 저장할 수 있는 자료구조

## 선언과 생성

> ex

```java
int[] intArr; // 선언
intArr = new int[5]; // 생성

char[] charArr = new char[5]; // 선언 및 생성
```

<br>
<hr>
<br>

## 자바스크립트 배열과의 차이점

-   자바 배열은 단일 타입의 요소만을 가질 수 있고, 이 타입은 선언시 지정해야함
-   배열 생성시 각 요소는 해당 타입의 기본값으로 초기화됨
-   배열의 크기가 고정되어 있음

<br>
<hr>
<br>

## 배열 복사

### 깊은 복사(deep copy)

-   새로운 배열을 생성하여 각 요소를 하나씩 복사하여 넣음
-   원본 배열과 완전히 독립적인 배열

> ex

```java
// Arrays.copyOf() 메서드 이용
int[] numbers1 = {1, 2, 3};
int[] numbers2 = Arrays.copyOf(numbers1, numbers1.length);

System.out.println(Arrays.toString(numbers1));
System.out.println(Arrays.toString(numbers2));

numbers2[0] = 0

System.out.println(Arrays.toString(numbers1)); // [1, 2, 3]
System.out.println(Arrays.toString(numbers2)); // [0, 2, 3]

// for문을 이용해 각 요소 복사
int[] numbers3 = {4, 5, 6};

int[] numbers4 = new int[numbers3.length];

for(int i = 0; i < numbers4.length; i++) {
    numbers4[i] = numbers3[i];
}

System.out.println(Arrays.toString(numbers3)); // [4, 5, 6]
System.out.println(Arrays.toString(numbers4)); // [4, 5, 6]

numbers2[0] = 0
System.out.println(Arrays.toString(numbers3)); // [4, 5, 6]
System.out.println(Arrays.toString(numbers4)); // [0, 5, 6]
```

### 얕은 복사(shallow copy)

-   배열 요소에 대한 참조만을 복사
-   복사된 배열의 요소가 원본 배열의 요소와 동일한 참조를 가지므로 요소 변경시 원본 배열의 요소도 변경됨

> ex

```java
int[] numbers1 = {1, 2, 3};
int[] numbers2 = numbers1;

System.out.println(Arrays.toString(numbers1)); // [1, 2, 3]
System.out.println(Arrays.toString(numbers2)); // [1, 2, 3]

// 복사한 배열의 요소 변경시 원본 배열도 변경됨
numbers2[0] = 0;

System.out.println(Arrays.toString(numbers1)); // [0, 2, 3]
System.out.println(Arrays.toString(numbers2)); // [0, 2, 3]
```

<br>
<hr>
<br>

## 예제 문제

### 문제) 최대값, 최소값 찾기

유저에게 n개의 정수를 입력받아 배열에 저장하여 최소값, 최대값을 찾아 출력

#### 해결 방법

-   유저에게 배열의 크기를 입력받고, 해당 크기만큼 정수를 입력받음
-   배열의 첫 원소의 값을 최소값, 최대값으로 설정 후 각 원소를 돌며 비교

#### 코드

```java
// 배열 선언, 생성
System.out.print("배열의 크기 >> ");
int arrayLength = sc.nextInt();
int[] intArray = new int[arrayLength];

// 배열 요소 입력
for(int i = 0; i < arrayLength; i++) {
    System.out.print(i + 1 + "번 정수: ");
    intArray[i] = sc.nextInt();
}

// 최소값, 최대값 찾기
int max = intArray[0];
int min = intArray[0];

for(int i = 1; i < arrayLength; i++) {
    if(max < intArray[i]) {
        max = intArray[i];
    }

    if(min > intArray[i]) {
        min = intArray[i];
    }
}

// 출력
System.out.print("최대값: " + max);
System.out.print("최소값: " + min);
```

#### 결과

배열의 크기 >> 5<br>
1번 정수: 4<br>
2번 정수: 15<br>
3번 정수: -2<br>
4번 정수: 0<br>
5번 정수: 10<br>
최대값: 15, 최소값: -2<br>

<br><br>
