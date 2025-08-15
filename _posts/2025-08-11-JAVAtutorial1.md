---
title: "학교 Java 시험 벼락치기 튜토리얼"
date: 2025-08-11 13:01:36
categories:
- Tutorial
tags:
- Java
---

# Intellij 다운로드
https://www.jetbrains.com/idea/download/?section=windows

위 링크를 통해 Intellij community edition을 다운받는다. (페이지 아래로 스크롤하면 있어요!)
인터넷에 검색하면 사용법이 많이 알려져 있으니, 이 글에서는 사용법을 생략한다.

# 기본 출력
Intellij에서 새로운 Java 프로젝트를 만들고 샘플 코드 추가를 활성화한다.
자동으로 Main.java 파일에 있을 것이다.

이제부터 public static void main(String[] args)의 두 중괄호 사이에 코드를 작성할 것이다.
현재 public static void main(String[] args)의 두 중괄호 안에 있는 코드를 지우고, 아래 코드를 입력한다.
```
System.out.print("Hello, world");
```
그 후, 상단에 있는 초록색 화살표 버튼을 눌러 코드를 실행한다.

출력:
```
Hello, world
```

Java에서는 System.out.print()를 이용해 화면에 글자를 출력한다.
출력하고자 하는 내용을 두 소괄호 사이에 넣으면 된다.

System.out.print()처럼 System.out.println()이 있는데, 
System.out.print()은 소괄호 안의 값을 출력하고 줄바꿈을 하지 않지만, 
System.out.println()은 소괄호 안의 값을 출력하고 줄바꿈을 한다.

예를 들어 보겠다.
코드:
```
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world!");
        System.out.print("Hello ");
        System.out.print("world!");
    }
}
```

출력:
```
Hello world!
Hello world!
```

또, 소괄호 안에 사칙연산(+, -, *, /)을 하는 것이 가능하다.
코드:
```
public class Main {
    public static void main(String[] args) {
        System.out.print("1 + 1 = ");
        System.out.print(1 + 1);
    }
}
```

출력:
```
1 + 1 = 2
```

# 변수
코딩을 하다 보면 정보를 저장해야 하는 경우가 있는데, 그런 정보들을 저장할 수 있는 공간을 변수라고 한다.

변수가 필요하다면, 변수를 선언해야 한다. 아래는 변수를 선언하는 방법이다.

변수타입 변수이름;

이해를 돕기 위해, 실생활에 적용하여 예시를 들어 보겠다.
물건들을 상자들에 저장할 것이다.
효율적으로 물건들을 저장하려면, 큰 물건은 큰 상자, 작은 물건은 작은 상자에 넣어야 한다.
또, 어떤 물건들은 깨지거나 부러질 수 있어, 완충제를 같이 넣어야 한다.
만약 모든 물건들을 상자에 알맞게 넣었다고 해보자.
어떤 상자 안에 무슨 물건이 있는지 모르면 의미가 없어진다.
그렇기 때문에, 내용물의 이름이 적힌 스티커를 붙일 것이다.

Java도 다름없다. 
정보가 크고 작은 것에 따라 필요한 저장공간이 다르며, 정보의 형태에 따른 저장이 필요하다. 
그렇기 때문에 변수타입이 존재하는 것이다.
내용물이 무엇인지 알 수 있도록, 변수를 선언할때, 변수 이름을 만들어야 하는 것이다.

예를 들어 정수, 영어로 integer여서 정수를 저장하기 위한 변수는 아래처럼 선언한다.

int (변수이름);

만약 변수가 저장하는 값을 바꾸고 싶다면 아래와 같이 하면 된다.

(변수이름) = (바꾸려고 하는 값)

예시 코드:
```
public class Main {
    public static void main(String[] args) {
        int x = 5;
        System.out.println(x);
        x = 3;
        System.out.print(x);
    }
}
```

출력:
```
5
3
```

예시 코드:
```
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

출력:
```
6
2
8
2
```

# 변수 타입 기본(중요)
int, long : 정수를 저장하기 위한 타입(20억을 넘을 땐 long 사용)
float, double : 실수(소수)를 저장하기 위한 타입 (float는 오차없이 7자리, double은 15자리)
char : 문자 하나를 저장하기 위한 타입
String : 여러 문자를 저장하기 위한 타입
bool : 참 또는 거짓을 저장하는 타입딩을 하다 보면 정보를 저장해야 하는 경우가 있는데, 그런 정보들을 저장할 수 있는 공간을 변수라고 한다.

변수가 필요하다면, 변수를 선언해야 한다. 아래는 변수를 선언하는 방법이다.

변수타입 변수이름;

이해를 돕기 위해, 실생활에 적용하여 예시를 들어 보겠다.
물건들을 상자들에 저장할 것이다.
효율적으로 물건들을 저장하려면, 큰 물건은 큰 상자, 작은 물건은 작은 상자에 넣어야 한다.
또, 어떤 물건들은 깨지거나 부러질 수 있어, 완충제를 같이 넣어야 한다.
만약 모든 물건들을 상자에 알맞게 넣었다고 해보자.
어떤 상자 안에 무슨 물건이 있는지 모르면 의미가 없어진다.
그렇기 때문에, 내용물의 이름이 적힌 스티커를 붙일 것이다.

Java도 다름없다. 
정보가 크고 작은 것에 따라 필요한 저장공간이 다르며, 정보의 형태에 따른 저장이 필요하다. 
그렇기 때문에 변수타입이 존재하는 것이다.
내용물이 무엇인지 알 수 있도록, 변수를 선언할때, 변수 이름을 만들어야 하는 것이다.

예를 들어 정수, 영어로 integer여서 정수를 저장하기 위한 변수는 아래처럼 선언한다.

int (변수이름);

만약 변수가 저장하는 값을 바꾸고 싶다면 아래와 같이 하면 된다.

(변수이름) = (바꾸려고 하는 값)

예시 코드:
```
public class Main {
    public static void main(String[] args) {
        int x = 5;
        System.out.println(x);
        x = 3;
        System.out.print(x);
    }
}
```

출력:
```
5
3
```

예시 코드:
```
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

출력:
```
6
2
8
2
```

# 변수 타입 기본(중요)
가장 많이 사용되는 변수 타입들에 대해 간단히 배워보겠다.

int, long : 정수를 저장하기 위한 타입(20억을 넘을 땐 long 사용)

float, double : 실수(소수)를 저장하기 위한 타입 (float는 오차없이 7자리, double은 15자리)

char : 문자 하나를 저장하기 위한 타입

String : 여러 문자를 저장하기 위한 타입

# 변수의 활용(중요)
변수 타입에 따라 정보에 접미사가 붙는 경우가 있다.
아쉽게도 이것은 암기가 필수이다.

long : 접미사가 'l' 혹은 'L'

8진수 : 접미사 '0'

16진수 : 접미사 '0x' 혹은 '0X'

float : 접미사 'f' 혹은 'F'

double : 접미사 'd' 혹은 'D'

참고 : 상수는 중간에 '_'을 넣어서, 큰 숫자를 읽게 편하게 하는 것이 가능하다.

# 변수의 활용 단축 버전
간단한 예시로 더 이해하기 쉽게 하겠다.

논리형 : false, true (접미사 없음)

참고로 논리형은 아직 배우지 않았으니 참고만 하면 된다.

정수형 : 12, 100L (접미사 L)

실수형 : 3.14, 3.0 (접미사 f, d)

문자형 : 'a', 'A' (접미사 없음)

문자열 : "AB", "a" (접미사 없음)

