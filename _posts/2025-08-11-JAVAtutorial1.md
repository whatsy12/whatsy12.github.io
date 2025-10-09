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

# 입력 받기

지금까지는 정보를 출력하는 방법을 배웠다. 이제는 사용자로부터 정보를 입력받는 방법을 알아보겠다.

Java에서 입력을 받으려면 `Scanner`라는 클래스를 사용해야 한다. 먼저 코드 맨 위에 다음과 같이 작성한다.

```java
import java.util.Scanner;
```

그 다음, `main` 메소드 안에서 Scanner 객체를 생성한다.

```java
Scanner sc = new Scanner(System.in);
```

## 입력 받기의 기본

Scanner를 사용하면 다양한 타입의 데이터를 입력받을 수 있다.

- `sc.nextInt()` : 정수 입력받기
- `sc.nextLong()` : long 타입 정수 입력받기
- `sc.nextFloat()` : float 타입 실수 입력받기
- `sc.nextDouble()` : double 타입 실수 입력받기
- `sc.next()` : 공백 전까지의 문자열 입력받기
- `sc.nextLine()` : 한 줄 전체를 문자열로 입력받기

예시 코드:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("정수를 입력하세요: ");
        int num = sc.nextInt();
        System.out.println("입력한 정수: " + num);
        
        System.out.print("이름을 입력하세요: ");
        String name = sc.next();
        System.out.println("안녕하세요, " + name + "님!");
    }
}
```

출력 예시:

```
정수를 입력하세요: 10
입력한 정수: 10
이름을 입력하세요: 홍길동
안녕하세요, 홍길동님!
```

## 주의사항

`nextLine()`을 사용할 때는 주의가 필요하다. 다른 next 메소드들을 사용한 후에 `nextLine()`을 사용하면, 남아있는 개행문자(\n)를 읽어버려 빈 문자열이 입력될 수 있다.

예시:

```java
Scanner sc = new Scanner(System.in);
int num = sc.nextInt();
sc.nextLine(); // 버퍼에 남은 개행문자 제거
String str = sc.nextLine();
```

# 조건문 (if문)

프로그래밍을 하다 보면 특정 조건에 따라 다른 동작을 해야 하는 경우가 많다. 이럴 때 사용하는 것이 조건문이다.

## if문의 기본 구조

```java
if (조건) {
    // 조건이 참일 때 실행되는 코드
}
```

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        int score = 85;
        
        if (score >= 80) {
            System.out.println("합격입니다!");
        }
    }
}
```

출력:

```
합격입니다!
```

## if-else문

```java
if (조건) {
    // 조건이 참일 때 실행
} else {
    // 조건이 거짓일 때 실행
}
```

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        int age = 15;
        
        if (age >= 18) {
            System.out.println("성인입니다.");
        } else {
            System.out.println("미성년자입니다.");
        }
    }
}
```

출력:

```
미성년자입니다.
```

## if-else if-else문

여러 조건을 검사해야 할 때 사용한다.

```java
if (조건1) {
    // 조건1이 참일 때
} else if (조건2) {
    // 조건2가 참일 때
} else if (조건3) {
    // 조건3이 참일 때
} else {
    // 모든 조건이 거짓일 때
}
```

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        int score = 85;
        
        if (score >= 90) {
            System.out.println("A학점");
        } else if (score >= 80) {
            System.out.println("B학점");
        } else if (score >= 70) {
            System.out.println("C학점");
        } else {
            System.out.println("F학점");
        }
    }
}
```

출력:

```
B학점
```

## 비교 연산자

조건문에서 사용되는 주요 비교 연산자들:

- `==` : 같다
- `!=` : 같지 않다
- `>` : 크다
- `<` : 작다
- `>=` : 크거나 같다
- `<=` : 작거나 같다

## 논리 연산자

여러 조건을 조합할 때 사용:

- `&&` : AND (그리고) - 모든 조건이 참이어야 함
- `||` : OR (또는) - 하나라도 참이면 됨
- `!` : NOT (부정) - 참을 거짓으로, 거짓을 참으로

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        int age = 20;
        boolean hasLicense = true;
        
        if (age >= 18 && hasLicense) {
            System.out.println("운전할 수 있습니다.");
        } else {
            System.out.println("운전할 수 없습니다.");
        }
    }
}
```

출력:

```
운전할 수 있습니다.
```

# 반복문

같은 작업을 여러 번 반복해야 할 때 반복문을 사용한다.

## for문

정해진 횟수만큼 반복할 때 주로 사용한다.

```java
for (초기식; 조건식; 증감식) {
    // 반복할 코드
}
```

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i + "번째 반복");
        }
    }
}
```

출력:

```
1번째 반복
2번째 반복
3번째 반복
4번째 반복
5번째 반복
```

## while문

조건이 참인 동안 계속 반복한다.

```java
while (조건) {
    // 반복할 코드
}
```

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        int count = 1;
        
        while (count <= 5) {
            System.out.println("카운트: " + count);
            count++;
        }
    }
}
```

출력:

```
카운트: 1
카운트: 2
카운트: 3
카운트: 4
카운트: 5
```

## do-while문

최소 한 번은 실행하고, 그 후 조건을 검사한다.

```java
do {
    // 반복할 코드
} while (조건);
```

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        int num = 10;
        
        do {
            System.out.println("숫자: " + num);
            num--;
        } while (num > 5);
    }
}
```

출력:

```
숫자: 10
숫자: 9
숫자: 8
숫자: 7
숫자: 6
```

## break와 continue

- `break` : 반복문을 즉시 종료
- `continue` : 현재 반복을 건너뛰고 다음 반복으로

예시 코드:

```java
public class Main {
    public static void main(String[] args) {
        // break 예시
        for (int i = 1; i <= 10; i++) {
            if (i == 5) {
                break;
            }
            System.out.println(i);
        }
        
        System.out.println("---");
        
        // continue 예시
        for (int i = 1; i <= 5; i++) {
            if (i == 3) {
                continue;
            }
            System.out.println(i);
        }
    }
}
```

출력:

```
1
2
3
4
---
1
2
4
5
```

다음 내용에서는 배열, 메소드, 클래스와 객체 등 더 심화된 내용을 다룰 예정이다.​​​​​​​​​​​​​​​​

# 오류제보
C++ 메인으로 코딩을 하다 보니, 실수를 하는 경우가 많다.
만약 오류 제보를 하고 싶다면 디스코드 아이디 _wha7y_를 통해 제보하시길 바란다.