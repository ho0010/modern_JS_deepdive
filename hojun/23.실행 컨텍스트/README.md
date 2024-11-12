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

렉시컬 환경은 식별자와 식별자에 바인딩된 값, 그리고 상위 스코프에 대한 참조를 기록하는 자료구조로 실행 컨텍스트를 구성하는 컴포넌트다. 렉시컬 환경은 키와 값을 갖는 객체 형태의 스코프(전역, 함수, 블록 스코프)를 생성해 식별자를 키로 등록하고 식별자에 바인딩된 값을 관리한다. 즉, 렉시컬 환경은 스코프를 구분해 식별자를 등록하고 관리하는 저장소 역할을 하는 렉시컬 스코프의 실체다.

<img width="441" alt="image" src="https://github.com/user-attachments/assets/57f36e6f-6dcf-46eb-abbe-aa5ef583a726">

<img width="549" alt="image" src="https://github.com/user-attachments/assets/2e2f4362-d513-42bd-ae3a-e689051dc999">

## 실행 컨텍스트의 생성과 식별자 검색 과정

<img width="549" alt="image" src="https://github.com/user-attachments/assets/fb371a61-4d72-43c1-949a-83d517f83b19">

- 전역 객체 생성
  
   전역 객체에는 빌트인 전역 프로퍼티와 빌트인 전역 함수, 표준 빌트인 객체가 추가되며 동작 환경에 따라 CS Web API 또는 특정 환경을 위한 호스트 객체를 포함한다. 전역 객체도 Object.prototype을 상속받는다. 즉, 전역 객체도 프로토타입 체인의 일원이다.
- 전역 코드 평가

   <img width="573" alt="image" src="https://github.com/user-attachments/assets/076c5855-7f54-4f33-87b2-4c32c90d5a50">

- 전역 코드 실행

   변수 할당문이 실행되어 전역 변수 x, y에 값이 할당된다. 그리고 foo함수가 호출된다. 할당문을 실행하기 전에 선언되었는지 확인해야한다. 더불어 어느 스코프의 식별자를 참조하면 되는지 결정해야 한다. 이를 **식별자 결정**이라 한다.
  식별자 결정을 위해 식별자를 검색할 때는 실행 중인 실행 컨텍스트에서 식별자를 검색하기 시작한다. 선언된 식별자는 실행 컨텍스트의 실행 컨텍스트의 렉시컬 환경의 환경 레코드에 등록되어 있다. 스코프 체인의 동작 원리에 따라 식별자를 검색한다.
  
- foo 함수 코드 평가

   <img width="573" alt="image" src="https://github.com/user-attachments/assets/0f6bf2a6-70eb-47b3-a3ad-2f9a8dfdc49b">

- foo 함수 코드 실행

  매개변수에 인수가 할당되고, 변수 할당문이 실행되어 지역 변수 x, y에 값이 할당되고 함수 bar가 호출된다.
  **식별자 결정을 위해 실행 중인 실행 컨텍스트의 렉시컬 환경에서 식별자를 검색하기 시작한다.**
- bar 함수 코드 평가

  <img width="573" alt="image" src="https://github.com/user-attachments/assets/65699ab3-aa5e-41a4-874f-3e6bd8b85338">

- bar 함수 코드 실행

  매개변수에 인수가 할당되고, 변수 실행문이 실행되어 지역 변수 z에 값이 할당된다.
  
  <img width="573" alt="image" src="https://github.com/user-attachments/assets/2f8bdb0d-e1de-40e0-a58c-d2e9856c0f9e">
  
  console 식별자 검색 => log 메서드 검색 => 표현식 a + b + x + y + z의 평가 => console.log 메서드 호출

- bar 함수 코드 실행 종료

  <img width="573" alt="image" src="https://github.com/user-attachments/assets/e325992a-9bbf-47f0-9dcf-39f385055bb4">

   실행 컨텍스트 스택에서 bar 함수 실행 컨텍스트가 제거되었다고 해서 bar 함수 렉시컬 환경까지 즉시 소멸하는 것은 아니다. 렉시컬 환경은 실행 컨텍스트에 의해 참조되기는 하지만 독립적인 개체다. 객체를 포함한 모든 값이 그러하듯 참조되지 않을 때 가비지 컬렉터에 의해 소멸한다.

- foo 함수 코드 실행 종료

  <img width="573" alt="image" src="https://github.com/user-attachments/assets/6f8e12b4-bc5a-42e2-838b-aa73518e63db">

- 전역 코드 실행 종료

  foo 함수가 종료되면 더는 실행할 전역 코드가 없으므로 전역 코드의 실행이 종료되고 전역 실행 컨텍스트도 실행 컨텍스트 스택에서 팝되어 실행 컨텍스트 스택에는 아무것도 남아있지 않게 된다.

## 실행 컨텍스트와 블록 레벨 스코프

**var 키워드**로 선언한 변수는 오로지 함수의 코드 블록만 지역 스코프로 인정하는 **함수 레벨 스코프**를 따른다.

**let, const 키워드**로 선언한 변수는 모든 코드 블록을 지역 스코프로 인정하는 **블록 레벨 스코프**를 따른다.

<img width="573" alt="image" src="https://github.com/user-attachments/assets/e2cb2956-5c4e-48ba-9837-08fb5d5113c0">

if 문의 코드 블록에 주목하자. if 문의 코드 블록이 실행되면 if문의 코드 블록을 위한 블록 레벨 스코플르 생성해야 한다. 이를 위해 선언적 환경 레코드를 갖는 렉시컬 환경을 새롭게 생성해 기존의 전역 레시컬 환경을 교체한다. 이때 새롭게 생성된 if문의 코드 블록을 위한 렉시컬 환경의 외부 렉시컬 환경에 대한 참조는 if문이 실행되기 이전의 전역 렉시컬 환경을 가르킨다.

<img width="573" alt="image" src="https://github.com/user-attachments/assets/04b18aaa-3954-4578-977f-55203d387d19">

이는 if 문뿐 아니라 블록 레벨 스코프를 생성하는 모든 블록문에 적용된다. 

for 문의 변수 선언문에 let 키워드를 사용한 for문은 코드 블록을 위한 새로운 렉시컬 환경을 생성한다. 이것은 24장의 클로저와 관련된다.
