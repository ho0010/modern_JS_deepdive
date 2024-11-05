> 실행 컨텍스트

실행 컨텍스트의 이해는 **JS가 스코프를 기반으로 식별자와 식별자에 바인딩된 값을 관리하는 방식, 호이스팅 발생 이유, 클로저의 동작 방식, 태스크 큐와 함께 동작하는 이벤트 핸들러, 비동기 처리의 동작 방식의 이해**와 이어진다.

## 소스코드의 타입

<img width="581" alt="image" src="https://github.com/user-attachments/assets/893d7f41-4c9e-4763-9789-330cf65298d8">

소스코드의 타입에 따라 실행 컨텍스트를 생성하는 과정과 관리 내용이 다르다.

1. 전역코드

   전역 코드는 전역 변수 관리를 위해 최상위 스코프인 전역 스코프를 생성해야 한다. 전역 변수(var키워드)와 전역 함수를 전역 객체의 프로퍼티와 메서드로 바인딩하고 참조하기 위해 전역 객체와 연결되어야 한다. 
2. 함수코드

   함수 코드는 지역 스코프를 생성하고 지역 변수, 매개변수, arguments 객체를 관리해야 한다. 그리고 생성한 지역 스코프를 전역 스코프에서 시작하는 스코프 체인의 일원으로 연결해야 한다. 
3. eval 코드

   strict mode에서 자신만의 독자적인 스코프를 생성한다.
4. 모듈 코드

   모듈별로 독립적인 모듈 스코프를 생성한다.

각 코드가 평가되면 각 코드에 맞는 실행 컨텍스트가 생성된다.

<img width="581" alt="image" src="https://github.com/user-attachments/assets/d3d3964b-f6cc-4f10-8e58-a74bd2e4f448">


## 소스코드의 평가와 실행

JS 엔진은 소스코드를 2개의 과정, 즉 "소스코드의 평가"와 "소스코드의 실행"과정으로 나누어 처리한다.

<img width="581" alt="image" src="https://github.com/user-attachments/assets/874f6452-2f93-45ab-8351-4617f992263a">

<img width="581" alt="image" src="https://github.com/user-attachments/assets/72d964fc-51b1-4885-84a8-be0b2dec2c88">

<img width="581" alt="image" src="https://github.com/user-attachments/assets/665dee2a-f307-4bc2-9fa2-7c63ea55aeb9">

<img width="581" alt="image" src="https://github.com/user-attachments/assets/f49be172-74f9-4c23-b882-696b9a9d5eae">


## 실행 컨텍스트의 역할

<img width="581" alt="image" src="https://github.com/user-attachments/assets/c8ee0397-abea-4bf3-9c90-95803a052dab">

1. 전역 코드 평가  

  전역 코드 평가 과정 (변수, 함수 선언문 먼저 실행)
  선언문 실행으로 생성된 전역 변수와 전역 함수가 실행 컨텍스트가 관리하는 전역 스코프에 등록된다. 즉, 전역 객체의 프로퍼티와 메서드가 된다.

2. 전역 코드 실행

   런타임이 시작되어 전역 코드가 순차적으로 실행된다. 이때 전역 변수에 값이 할당되고 함수가 호출된다. 함수가 호출되면 전역 코드의 순차적 실행을 중단하고 코드 실행 순서를 변경해 함수 내부로 진입한다.

3. 함수 코드 평가

   전역에서와 같이 선언문이 먼저 실행되고, 선언문의 결과로 생성된 것들이 지역 스코프에 등록된다. 또한, 함수 내부에서 지역 변수처럼 사용할 수 있는 arguments 객체가 생성되어 지역 스코프에 등록되고 this 바인딩도 결정된다.

4. 함수 코드 실행

   런타임이 시작되어 함수 코드가 순차적으로 실행되고 매개변수와 지역 변수에 값이 할당된다.
   <img width="581" alt="image" src="https://github.com/user-attachments/assets/67ec0d7e-cb1d-48fe-8e83-5f9f99ffb408">

**이처럼 코드가 실행되려면 다음과 같이 스코프, 식별자, 코드 실행 순서 등의 관리가 필요하다.**

<img width="581" alt="image" src="https://github.com/user-attachments/assets/1111e69c-46e0-49a8-8441-5b01f8ae38ef">

이 모든 것을 관리하는 것이 실행 컨텍스트다. **실행 컨텍스트는 소스코드를 실행하는 데 필요한 환경을 제공하고 코드의 실행 결과를 실제로 관리하는 영역이다.**

구체적으로, 식별자(변수, 함수, 클래스 등의 이름)을 등록하고 관리하는 스코프와 코드 실행 순서 관리를 구현한 내부 메커니즘으로, 모든 코드는 실행 컨텍스트를 통해 실행되고 관리된다.

식별자와 스코프는 실행 컨텍스트의 **렉시컬 환경**으로 관리하고 실행 순서는 **실행 컨텍스트 스택**으로 관리한다.

## 실행 컨텍스트 스택

<img width="575" alt="image" src="https://github.com/user-attachments/assets/46e21cf4-a1bc-4d87-a7a7-2b2d47edb040">

<img width="575" alt="image" src="https://github.com/user-attachments/assets/92f4230b-e728-4ada-ba57-4605c02ef2f5">

**전역 코드의 평가와 실행 => foo 함수 코드의 평가와 실행 => bar 함수 코드의 평가와 실행 => foo 함수 코드로 복귀 => 전역 코드로 복귀**

실행 컨텍스트 스택은 코드의 실행 순서를 관리한다. 스택의 최상위에 존재하는 실행 컨텍스트는 언제나 현재 실행 중인 코드의 실행 컨텍스트다.


## 렉시컬 환경



## 실행 컨텍스트의 생성과 식별자 검색 과정

## 실행 컨텍스트와 블록 레벨 스코프
