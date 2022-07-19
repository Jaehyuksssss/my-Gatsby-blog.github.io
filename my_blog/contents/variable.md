---
date: '2022-06-02'
title: 'JavaScript'
categories: ['TIL','Deep_Dive']
summary: '3장 변수'
thumbnail: './deep-dive.png'
---



# 3장 변수
## 변수
- 변수란 무엇인가? 왜 필요한가?
- 식별자
- 변수 선언
- 변수 선언의 실행 시점과 변수 호이스팅
- 값의 할당
- 값의 재할당
- 식별자 네이밍 규칙

## 1. 변수란 무엇인가? 왜 필요한가?
### 메모리
- 컴퓨터는 CPU를 사용해 연산하고, 메모리를 사용해 데이터를 기억한다.
- 각 셀은 고유의 메모리 주소를 갖는다.
- 메모리 공간에 직접 접근하는 것은 위험하므로 변수를 사용한다.
### 변수
- 값의 위치(값이 저장된 메모리 공간)를 가리키는 상징적인 이름

## 2. 식별자
- 어떤 값을 구별해서 식별할 수 있는 고유한 이름, 변수의 이름
- 식별자는 값이 아니라 메모리 주소를 기억하고 있다.
- 식별자가 기억하고 있는 메모리 주소를 통해 메모리 공간에 저장된 값에 접근할 수 있다.

## 3. 변수 선언
- 변수를 생성하는 것

- 값을 저장하기 위한 메모리 공간을 확보하고, 변수 이름과 메모리 공간의 주소를 연결해서 값을 저장할 수 있게 준비하는 것

- 변수 선언 키워드 : var, const, let

- 확보된 메모리 공간에는 자바스크립트 엔진에 의해 undefined라는 값이 암묵적으로 할당되어 초기화된다.

- let, const는 시간상 사각지대로 인해 초기화하기 전에는 읽거나 쓸 수 없다.

## 4.변수 선언의 실행 시점과 변수 호이스팅

## 변수 선언의 실행 시점

```
console.log(score); // undefined

var score; // 변수 선언문
```
- 위 예제는 변수 선언문보다 변수를 참조하는 코드가 앞에 있다.
- 자바스크립트 코드는 인터프리터에 의해 한 줄씩 순차적으로 실행되므로 변수 선언문이 아래에 있기 때문에 참조 에러가 발생한다고 생각할 수 있다.
- 참조 에러가 발생하지 않고 undefined가 출력된다.

>참조 에러가 발생하지 않은 이유
: 변수 선언이 소스코드가 한 줄씩 순차적으로 실행되는 시점, 즉 런타임이 아니라 그 이전 단계에서 먼저 실행되기 때문이다.
- 소스코드 실행을 위한 준비 단계인 소스코드의 평가 과정에서 자바스크립트 엔진은 변수 선언을 포함한 모든 선언문을 소스코드에서 찾아내 먼저 실행한다.

### 변수 호이스팅
- 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 고유의 특징
- 변수 선언뿐 아니라 var, let, const, function, function*, class 키워드를 사용해서 선언하는 모든 식별자는 호이스팅된다.
- 모든 선언문은 런타임 이전 단계에서 먼저 실행되기 때문이다.
- 단, let, const는 호이스팅되지만 TDZ로 인해 참조 에러가 발생한다.

## 5. 값의 할당
- 변수에 값을 할당할 때는 할당 연산자 =를 사용한다.
- 변수 선언과 값의 할당을 하나의 문으로 단축 표현해도 변수 선언과 값의 할당을 2개의 문으로 나누어 각각 실행한다.
- 이때 변수 선언과 값의 할당 실행 시점이 다르다.
>변수 선언 : 런타임 이전에 먼저 실행
>값의 할당 : 런타임에 실행

## 6. 재할당
-이미 값이 할당되어 있는 변수에 새로운 값을 또다시 할당하는 것
- var 키워드로 선언한 변수는 선언과 동시에 undefined로 초기화되기 때문에 변수에 처음 값을 할당하는 것도 재할당이다.
- 변수와 상수
>변수 : 값을 재할당해서 저장된 값을 다른 값으로 변경할 수 있음
>상수 : 값을 대할당할 수 없어 변수에 저장된 값을 변경할 수 없음
- 새로운 메모리 공간을 확보하고 그 메모리 공간에 새로운 값을 저장한다.

### 가비지 콜렉터
- 애플리케이션이 할당한 메모리 공간을 주기적으로 검사하여 더이상 사용하지 않는 메모리를 해제하는 기능
- 가비지 콜렉터를 통해 메모리 누수를 방지한다.
- 변수에 값을 계속 할당하게 되면 이전 메모리 공간을 둔 채 새로운 메모리 공간을 확보하고 새로운 값을 저장한다.
>이때 이전 메모리 공간을 쓰레기 값이라고 하며, 이 쓰레기 값을 정리하는 기능이 가비지 콜렉터이다.
## 7. 식별자 네이밍 규칙
- 식별자는 특수문자를 제외한 문자, 숫자, 언더스코어(_), 달러 기호($)를 포함할 수 있다.
- 숫자로 시작하는 것은 허용하지 않는다.
- 예약어는 식별자로 사용할 수 없다.
- 변수 이름은 변수의 존재 목적을 쉽게 이해할 수 있도록 의미를 명확히 표현해야 한다.
## 네이밍 컨벤션
- 하나 이상의 영어 단어로 구성된 식별자를 만들 때 가독성 좋게 단어를 한 눈에 구분하기 위해 규정한 명명 규칙
>카멜 케이스 :var firstName
> 스네이크 케이스 : var first_name
>파스칼 케이스 :var FirstName
>헝가리언 케이스 :var strFirstName : type + identifier
>일반적으로 변수나 함수의 이름에는 카멜 케이스를 사용하고, 생성자 함수, 클래스의 이름에는 파스칼 케이스를 사용한다.