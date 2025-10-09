---
title: "학교 Java 시험 벼락치기 튜토리얼 (1)"
date: 2025-08-11 13:01:36
categories:
- Tutorial
tags:
- Java
- 튜토리얼
---

# IntelliJ 다운로드 및 설치

https://www.jetbrains.com/idea/download/?section=windows

위 링크를 통해 IntelliJ Community Edition을 다운받는다. (페이지 아래로 스크롤하면 있다!) 인터넷에 검색하면 사용법이 많이 나와 있으니, 이 글에서는 사용법을 생략한다.

# 기본 출력

IntelliJ에서 새로운 Java 프로젝트를 만들고 샘플 코드 추가를 활성화한다. 자동으로 Main.java 파일이 생성될 것이다.

이제부터 `public static void main(String[] args)`의 두 중괄호 `{ }` 사이에 코드를 작성할 것이다. 현재 중괄호 안에 있는 코드를 지우고, 아래 코드를 입력한다.

```java
System.out.print("Hello, world");
```

그 후, 상단에 있는 초록색 화살표 버튼을 눌러 코드를 실행한다.

**출력:**

```
Hello, world
```

Java에서는 `System.out.print()`를 이용해 화면에 글자를 출력한다. 출력하고자 하는 내용을 소괄호 안에 넣으면 된다.

## print와 println의 차이

- `System.out.print()` : 값을 출력하고 **줄바꿈을 하지 않음**
- `System.out.println()` : 값을 출력하고 **줄바꿈을 함**

예를 들어 보겠다.

**코드:**

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world!");
        System.out.print("Hello ");
        System.out.print("world!");
    }
}
```

**출력:**

```
Hello world!
Hello world!
```

## 계산 결과 출력하기

소괄호 안에서 사칙연산(+, -, *, /)을 하는 것도 가능하다.

**코드:**

```java
public class Main {
    public static void main(String[] args) {
        System.out.print("1 + 1 = ");
        System.out.print(1 + 1);
    }
}
```

**출력:**

```
1 + 1 = 2
```

# 변수

코딩을 하다 보면 정보를 저장해야 하는 경우가 있는데, 그런 정보들을 저장할 수 있는 공간을 **변수**라고 한다.

변수를 사용하려면 먼저 변수를 선언해야 한다.

## 변수 선언 방법

```java
변수타입 변수이름;
```

## 변수의 개념 이해하기

실생활에 비유하여 설명하겠다. 물건들을 상자에 저장한다고 생각해보자.

- 큰 물건은 큰 상자에, 작은 물건은 작은 상자에 넣어야 한다
- 깨지기 쉬운 물건은 완충제를 함께 넣어야 한다
- 상자에 내용물 이름을 적은 스티커를 붙여야 나중에 찾을 수 있다

Java의 변수도 마찬가지다:

- 정보의 크기와 형태에 따라 적절한 **변수타입**이 필요하다
- 무엇이 저장되어 있는지 알 수 있도록 **변수이름**을 붙여야 한다

## 정수형 변수 사용 예시

정수(integer)를 저장하는 변수는 `int` 타입을 사용한다.

```java
int 변수이름;
```

변수에 값을 저장하거나 변경하려면:

```java
변수이름 = 저장할값;
```

**예시 코드:**

```java
public class Main {
    public static void main(String[] args) {
        int x = 5;
        System.out.println(x);
        x = 3;
        System.out.print(x);
    }
}
```

**출력:**

```
5
3
```

## 변수를 이용한 계산

**예시 코드:**

```java
public class Main {
    public static void main(String[] args) {
        int x = 4;
        int y = 2;
        System.out.println(x + y);
        System.out.println(x - y);
        System.out.println(x * y);
        System.out.println(x / y);
    }
}
```

**출력:**

```
6
2
8
2
```

# 변수 타입 기본 (중요!)

가장 많이 사용되는 변수 타입들에 대해 알아보자.

## 주요 변수 타입

|타입               |설명           |비고                          |
|-----------------|-------------|----------------------------|
|`int`, `long`    |정수 저장        |20억 초과 시 long 사용            |
|`float`, `double`|실수(소수) 저장    |float은 7자리, double은 15자리 정밀도|
|`char`           |문자 하나 저장     |작은따옴표 사용: ‘a’               |
|`String`         |여러 문자(문자열) 저장|큰따옴표 사용: “hello”            |

# 변수의 활용 (중요!)

변수 타입에 따라 값에 **접미사**가 붙는 경우가 있다. 이것은 암기가 필수다!

## 접미사 규칙

|타입    |접미사         |예시           |
|------|------------|-------------|
|long  |`L` 또는 `l`  |100L         |
|8진수   |`0`         |077          |
|16진수  |`0x` 또는 `0X`|0xFF         |
|float |`f` 또는 `F`  |3.14f        |
|double|`d` 또는 `D`  |3.14d (생략 가능)|

**참고:** 큰 숫자는 가독성을 위해 중간에 `_`(언더스코어)를 넣을 수 있다.

```java
int million = 1_000_000;
```

## 변수의 활용 - 간단한 예시

각 타입별 실제 사용 예시:

|타입 |예시               |비고                  |
|---|-----------------|--------------------|
|논리형|`false`, `true`  |접미사 없음              |
|정수형|`12`, `100L`     |L 접미사는 long         |
|실수형|`3.14`, `3.0f`   |f는 float, 없으면 double|
|문자형|`'a'`, `'A'`     |작은따옴표, 문자 1개        |
|문자열|`"AB"`, `"hello"`|큰따옴표, 여러 문자         |

**참고:** 논리형(boolean)은 조건문에서 다루므로 지금은 참고만 하자.

-----

이제 Java의 기본 문법을 이해했다면, 다음 단계로 입력 받기, 조건문, 반복문 등을 배울 준비가 되었다!

# 오류제보
C++ 메인으로 코딩을 하다 보니, 실수를 하는 경우가 많다.
만약 오류 제보를 하고 싶다면 디스코드 아이디 _wha7y_를 통해 제보하시길 바란다.