## 클래스는 프로토타입의 문법적 설탕인가?

JS는 프로토타입 기반 객체지향 언어이기 때문에 클래스가 필요 없는 객체지향 프로그래밍 언어다.

ES5에서는 클래스 없이도 생성자 함수와 프로토타입을 통해 객체지향 언어의 상속을 구현할 수 있다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/f1c069ef-d5ae-429e-bc9a-f1644650cb1d">

다만 이러한 특징이 기존 클래스 기반 언어에 익숙한 프로그래머들에게 벽이 될 수 있기에 ES6에서 도입된 클래스는 클래스 기반 객체지향 프로그래밍 언어와 유사한 새로운 객체 생성 메커니즘을 제시한다.

단, 클래스와 생성자 함수는 모두 프로토타입 기반의 인스턴스를 생성하지만 정확히 동일하게 동작하지는 않는다. 아래와 같은 차이가 있다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/97789ae4-786b-41cd-8fb1-74f234cc1b8c">

생성자 함수와 클래스는 프로토타입 기반의 객체지향을 구현했다는 점에서 유사하다. 하지만 클래스는 생성자 함수 기반의 객체 생성 방식보다 견고하고 명료하다.(우월하다는 의미가 아니다) 특히 클래스의 extends와 super키워드가 상속 관계 구현에서 하는 역할이 그러하다.

따라서 단순 문법적 설탕이라기 보다는 **새로운 객체 생성 메커니즘**으로 보는 것이 좀 더 합당하다.

## 클래스 정의

class 키워드를 사용해 정의한다. 생성자 함수와 마찬가지로 파스칼 케이스를 사용하는 것이 일반적이다. 파스칼 케이스가 아니라도 에러가 발생하지는 않는다.

일반적이지는 않지만 함수와 마찬가지로 표현식으로 클래스를 정의할 수 있다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/11d81644-3688-4226-91e8-7059fe2b0b06">

클래스를 표현식으로 정의할 수 있다는 것은 클래스가 값으로 사용할 수 있는 일급 객체라는 것을 의미한다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/25a063fe-7de2-4a9f-965b-77e65b9d2c94">

클래스 몸체에는 0개 이상의 메서드만 정의할 수 있다. 클래스 몸체에는 0개 이상의 메서드만 정의할 수 있다. 클래스 몸체에서 정의할 수 있는 메서드는 constructor(생성자), 프로토타입 메서드, 정적 메서드의 세 가지가 있다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/fe9c5f5f-fbdb-4137-b391-17fa9e167d9a">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/a1201edd-f939-40cf-9d3e-a81a596cc793">


## 클래스 호이스팅

클래스는 함수로 평가된다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/1d509ac3-354e-4ed7-879a-921df3cdda84">

클래스 선언문으로 정의한 클래스는 함수 선언문과 같이 소스코드 평가 과정, 즉 런타임 이전에 먼저 평가되어 함수 객체를 생성한다. 이때 클래스가 평가되어 생성된 함수 객체는 생성자 함수로서 호출할 수 있는 함수, 즉 constructor이다. 생성자 함수로서 호출할수 있는 함수는 함수 정의가 평가되어 함수 객체를 생성하는 시점에 프로토타입도 더불어 생성된다. 프로토타입과 생성자 함수는 단독으로 존재할 수 없고 언제나 쌍으로 존재하기 때문이다. 단, 클래스 정의 이전에는 참조할 수 없다.

> 클래스 선언문도 변수 선언, 함수 정의와 마찬가지로 호이스팅이 발생한다. var, let, const, function, function*, class 키워드를 사용해 선언된 모든 식별자는 호이스팅된다. 모든 선언문은 런타임 이전에 먼저 실행되기 때문이다.

## 인스턴스 생성

클래스는 생성자 함수이며 new 연산자와 함께 호출되어 인스턴스를 생성한다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/34756833-b8b9-40db-bb21-7a9c9d9418d0">

함수는 new 연산자의 사용 여부에 따라 일반 함수로 호출되거나 인스턴스 생성을 위한 생성자 함수로 호출되지만 클래스는 인스턴스를 생성하는 것이 존재 이유이므로 반드시 new 연산자와 함께 호출해야 한다.

## 메서드

클래스 몸체에는 0개 이상의 메서드만 정의할 수 있다. 클래스 몸체에는 0개 이상의 메서드만 정의할 수 있다. 클래스 몸체에서 정의할 수 있는 메서드는 constructor(생성자), 프로토타입 메서드, 정적 메서드의 세 가지가 있다.

---

### constructor

constructor는 인스턴스를 생성하고 초기화하기 위한 특수한 메서드다. 이름 변경은 불가능하다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/dfc196fa-b8e9-4f44-a53b-ee4c67df500c">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/e973885a-f3ec-4e6c-8f22-0ee52981fd58">

모든 함수 객체가 가진 prototype 프로퍼티가 가르키는 프로토타입 객체의 constructor 프로퍼티는 클래스 자신을 가르키고 있다. 이는 클래스가 인스턴스를 생성하는 생성자 함수라는 것을 의미한다. 즉, new 연산자와 함께 클래스를 호출하면 클래스는 인스턴스를 생성한다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/bf391f37-34df-488f-ad28-86f66f3aaebd">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/900cf004-3766-4154-96eb-ba29769b9bb4">

constructor 메서드가 생성된 함수 객체나 생성한 인스턴스에 없는 것으로 보아 **단순한 메서드가 아닌 클래스가 평가되어 생성한 함수 객체 코드의 일부**라는 것에 주목하자. 다시 말해, 클래스 정의가 평가되면 constructor의 기술된 동작을 하는 함수 객체가 생성된다.

> 참고 - 클래스의 constructor 메서드와 프로토타입의 constructor 프로퍼티는 다르다.

constructor는 생성자 함수와 달리 클래스 내에 최대 한 개만 존재할 수 있다. 만약 클래스가 2개 이상의 constructor를 포함하면 문법 에러가 발생한다.

constructor는 별도의 반환문을 갖지 않아야 한다. new 연산자와 함께 클래스가 호출되면 생성자 함수와 동일하게 암묵적으로 this, 즉 인스턴스를 반환하기 때문이다. 내부에서 명시적으로 this가 아닌 다른 값을 반환하는 것은 클래스의 기본 동작을 훼손한다. 

만약 this가 아닌 다른 객체를 반환하면 this, 즉 인스턴스가 반환되지 않고 return에 명시한 객체가 반환된다. 원시값을 반환하면 무시되고 this가 반환된다.

---

### 프로토타입 메서드

생성자 함수를 사용해 인스턴스를 생성하는 경우 프로토타입 메서드를 생성하기 위해서는 다음과 같이 명시적으로 프로토타입에 메서드를 추가해야 한다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/a782e6fe-7c96-4021-939c-49df47bee82a">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/050d9fc2-f09f-47a6-a926-8f01f720ebe3">

클래스 몸체에서 정의한 메서드는 생성자 함수에 의한 객체 생성 방식과는 다르게 클래스의 prototype 프로퍼티에 메서드를 추가하지 않아도 기본적으로 프로토타입 메서드가 된다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/9fdc1e2c-f9cc-4b82-a71c-3a274fb8f23b">

생성자 함수와 같이 클래스가 생성한 인스턴스는 프로토타입 체인의 일원이 된다.

결국 클래스는 생성자 함수와 같이 인스턴스를 생성하는 생성자 함수라고 볼 수 있다. 다시 말해, 클래스는 생성자 함수와 마찬가지로 프로토타입 기반의 객체 생성 메커니즘이다.

### 정적 메서드

정적 메서드는 인스턴스를 생성하지 않아도 호출할 수 있는 메서드를 말한다.

생성자 함수는 정적 메서드를 생성하기 위해서는 명시적으로 생성자 함수에 메서드를 추가해야 한다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/5058b22b-ce68-44df-96bd-ee300e96a93f">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/5671f939-d07b-4560-8366-a897e2875673">

클래스에서는 메서드에 static 키워드를 붙이면 정적 메서드(클래스 메서드)가 된다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/80b29afc-4833-441e-a9ab-2a1601495f3f">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/7c9de8c5-4893-46e1-ac71-157a271ea094">

이처럼 정적 메서드는 클래스에 바인딩된 메서드가 된다. 클래스는 함수 객체로 평가되므로 자신의 프로퍼티/메서드를 소유할 수 있다.

정적 메서드는 프로토타입 메세드처럼 인스턴스로 호출하지 않고 클래스로 호출한다.

정적 메서드는 인스턴스로 호출할 수 없다. 정적 메서드가 바인딩된 클래스는 인스턴스의 프로토타입 체인상에 존재하지 않기 때문이다. 다시 말해, 인스턴스의 프로토타입 체인 상에는 클래스가 존재하지 않기 때문에 인스턴스로 클래스의 메서드를 상속받을 수 없다.

---
### 정적 메서드와 프로토타입 메서드의 차이

<img width="569" alt="image" src="https://github.com/user-attachments/assets/297a419c-8746-4e43-ab6b-ab015cc1ba4b">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/c1eecd42-a2f1-412a-b8f0-1d3f96afe3c8">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/94967be2-9437-4256-b388-e527856f1185">

표준 빌트인 객체인 Math, Number, JSON, Object, Reflect 등은 다양한 정적 메서드를 가진다. 이들 정적 메서드는 애플리케이션 전역에서 사용할 유틸리티 함수다. 클래스 또는 생성자 함수를 하나의 네임스페이스로 사용해 정적 메서드를 모아 놓으면 이름 충돌 가능성을 줄여 주고 관련 함수들을 구조화할 수 있는 효과가 있다.

---
### 클래스에서 정의한 메서드의 특징

<img width="569" alt="image" src="https://github.com/user-attachments/assets/0cc50d79-0110-4d68-8a98-f23e243dd3e8">

## 클래스의 인스턴스 생성 과정

new 연산자와 함께 클래스를 호출하면 생성자 함수와 마찬가지로 클래스의 내부 메서드 [[Construct]]가 호출된다. 클래스는 new 연산자 없이 호출할 수 없다.

1. 인스턴스 생성과 this 바인딩
  new 연산자와 함께 클래스를 호출하면 constructor의 내부 코드가 실행되기에 앞서 암묵적으로 빈 객체가 생성된다. 이 빈 객체가 클래스가 생성한 인스턴스다. 이때 클래스가 생성한 인스턴스의 프로토타입으로 클래스의 prototype 프로퍼티가 가르키는 객체가 설정된다. 그리고 암묵적으로 생성된 빈 객체, 즉 인스턴스는 this에 바인딩된다. 따라서 constructor 내부의 this는 클래스가 생성한 인스턴스를 가르킨다.
   
2. 인스턴스
   constructor의 내부 코드가 실행되어 this에 바인딩되어 있는 인스턴스를 초기화한다. 즉, this에 바인딩되어 있는 인스턴스에 프로퍼티를 추가하고 constructor가 인수로 전달받은 초기값으로 인스턴스의 프로퍼티 값을 초기화한다. 만약, counstructor가 생력되었다면 이 과정도 생략된다.
   
3. 인스턴스 반환
   클래스의 모든 처리가 끝나면 완성된 인스턴스가 바인딩된 this가 암묵적으로 반환된다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/bd1b0c9d-8934-4b53-a14e-fc00142944da">

## 프로퍼티



## 상속에 의한 클래스 확장
