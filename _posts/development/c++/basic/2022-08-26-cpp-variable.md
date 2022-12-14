---
title: C++-변수
author: kimjeahyun
date: 2022-08-26 20:00:00 +0900
categories: [Languages for development,Cpp]
tags: [Languages for development,Cpp]
---

# 변수 (Variable)

우리는 일상생활에서 돈이라는 지폐를 지갑이라는 물체에 넣어 보관하고
옷은 옷장에 신발은 신발장에 
그럼 프로그램 내부에서도 저장하는 공간이 존재할까?

그에대한 대답은 당연히 존재하며 그것을 변수라 부른다.
변수는 하나의 타입의 하나의 값을 저장 할 수 있는 공간이다.

<br>

>변수는 어떻게 사용할까?

<br>

변수의 선언 -> 변수 호출 

```java
  type 변수이름 = 값;
```
여기에서 변수에 대해서 값을 넣지 않아도 될까?
변수에 값을 넣지 않아도 상관은 없지만 모든 변수가 값을 할당할때는 메모리를 사용하게 된다. 이 시점에서 값(초기화) 과정이 발생하지 않는다면 값은 쓰레기값(-12392930) 의 형태로 저장하게 된다. 때문에 변수를 선언하고 초기화를 해주는 것이 좋다.

변수의 공간은 변수타입에 맞게 알맞은 저장공간이 확보된다. 이 저장공간만큼 저장 할 수 있는 수의 크기도 정해진다.

변수로 나의 이름과 성별 키 말하기
```cpp
std::string MyName = "김재현";
std::string MyGender = "남";
int MyAge = 28;

const std::string result = "나의 이름,성별,이름은 "+MyName+","+MyGender+","+MyAge+" 입니다.";

std::cout << result << std::endl;

```

여기서 타입과 변수이름, 값 이외에 final라는 키워드가 보일것이다.
result는 반환 메세지가 변하지 않는다는 가정하에 상수(final)로 표시하여 변수를 선언해 보았다. 그리고 여기서 가장 중요한 것은 변수의 이름이다.
다음과 같이 MyName , MyGender는 직관적으로 무슨 변수인지 파악이 가능하다.
만약 변수이름이 A라고 명시된다면 개발자는 A라는 변수가 도대체 무엇인지 어떤 용도에 사용되는지 알 수가 없다. 때문에 변수 선언시 변수이름을 중요하게 여기자.


변수는 다음 두가지로 나눌 수 있다.

- 기본형
  - 논리형,문자형,정수형,실수형 값을 저장하는 변수

- 참조형
  - 객체의 주소를 저장하는 변수 

<br>

# 기본형 

기본형에는 논리형,문자형,정수형,실수형으로 구분된다. 

|분류|타입|
|-----|:-----|
|논리형|boolean|
|문자형|char|
|정수형|byte,short,int,long|
|실수형|float,double|

<br>

# boolean 타입

우리 방에 존재하는 불을 키고 끄는 스위치는 on/off 로 구성되어있다. 
이와 마찬가지로 boolean 타입도 true/false 존재하는데 진실 혹은 거짓을 표현하는 값을 
저장할때 유용하게 쓰인다. 

# char 타입
단일 문자를 저장할 때 사용된다. 그리고 char에서 재밌는 부분이 있는데
외관적으로 보면 문자열이 저장되는 것 처럼 보이지만 사실은 유니코드로 저장된다.
때문에 아스키코드를 이용하여 숫자 값 을 저장 할 경우 문자로 표현되어 저장 할 수 있다.

<br>

# byte,short,int,long 타입

숫자를 저장하는 타입이다. 각 타입별로 저장 할 수 있는 크기가 정해지는데 해당 크기에 맞춰
유의하여 사용 하여야 한다.

<br>

# float , double 타입

해당 타입은 실수를 저장하는 타입이다. 정수형 타입과 마찬가지로 타입별로 저장 할 수 있는 크기가 
정해진다. 해당 크기에 맞춰 유의하여 사용하자.

<br>

# 자료형

앞서 말한 것 과 같이 변수를 선언할 때에는 타입의 크기 만큼 메모리가 설정되는데
다음 표에 대해서 타입에 따른 저장 범위값을 볼 수 있다.

|자료형|저장 가능한 값의 범위|크기(byte)|
|------|:-------------------:|---------|
|boolean|false, true | 1|
|char|0~2<sup>16</sup>-1,0~65535|2|
|byte|-128 ~ 127 (-2<sup>7</sup> ~ 2<sup>7</sup>-1)|1|
|short|-32,768 ~ 32,767 (-2<sup>15</sup> ~ 2<sup>15</sup>-1)|2|
|int|-2,147,483,648 ~ 2,147,483,647 (-2<sup>31</sup> ~ 2<sup>31</sup>-1)|4|
|long|-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 (-2<sup>63</sup> ~ 2<sup>63</sup>-1)|8|
|float| 1.4E-45  ~ 3.4E38 (1.4x10<sup>-45</sup>~3.4x10<sup>38</sup>)|4|
|float| 4.9E-324  ~ 1.8E308 (4.9x10<sup>-324</sup>~1.8x10<sup>308</sup>)|8|

해당 자료형에 대해서 값이 초과 할 경우에는 프로그램 오류가 발생한다. 그러므로 자신이 
선언한 타입게 맞게 값이 벗어나지 않도록 주의하자.

<br>

# 형변환

그렇다면 여기서 궁금한점은 만약 저장된 데이터를 타입을 변경할 수는 없을까? 
자바에서는 타입을 변경 할 수 있는 형변환 문법이 존재한다.

형변환 하는 방법은 다음과 같다.

~~~
(타입) 피연산자
~~~

>작은 타입에서 큰 타입으로 가는 경우는 문제가 없지만 큰 타입에서 작은 타입으로 갈 경우 데이터가 유실 될 수 있다.


