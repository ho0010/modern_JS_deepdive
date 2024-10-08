JS는 명령형, 함수형, **프로토타입 기반 객체지향 프로그래밍**을 지원하는 멀티 패러다임 프로그래밍 언어이다.

JS는 객체 기반의 프로그래밍 언어이며 JS를 이루고 있는 거의 모든 것이 객체다.

<br />

> 19.1 객체지향 프로그래밍

객체 지향 프로그래밍은 실세계의 실체를 인식하는 철학적 사고를 프로그래밍에 접목하려는 시도에서 시작한다.

실체는 특징이나 성질을 나타내는 **속성**을 가지고 있고 이를 통해 실체를 인식하고 구별한다.

실체의 다양한 속성 중 필요한 속성만 간추려 표현하는 것을 **추상화**라고 한다.

객체란 **속성을 통해 여러 개의 값을 하나의 단위로 구성한 복합적인 자료구조**이다.

객체 지향 프로그래밍은 객체의 **상태**를 나타내는 데이터와 상태 데이터를 조작할 수 있는 **동작**을 하나의 논리적인 단위로 묶어 생각한다. 즉, 객체는 **상태 데이터와 동작을 하나의 논리적인 단위로 묶은 복합적인 자료구조**라 할 수 있다. 이때 객체의 상태 데이터를 프로퍼티, 동작을 메서드라 부른다.

---
<br />

> 19.2 상속과 프로토타입

객체 지향 프로그래밍의 핵심인 상속 어떤 객체의 프로퍼티 혹은 메서드를 다른 객체가 상속받아 그대로 사용할 수 있는 것을 말한다. JS는 프로토타입을 기반으로 상속을 구현해 불필요한 중복을 제거한다.

위에서 말한 것에 대한 예시로 생성자 함수로 인해 생성되는 인스턴스가 동일한 메서드를 소유해 낭비하는 것을 없애는 것이다.

<img width="561" alt="image" src="https://github.com/user-attachments/assets/402bd834-c244-443a-b897-9fc373c05d5b">

---
<br />

> 19.3 프로토타입 객체

프로토타입 객체(줄여서 프로토타입)는 상속을 구현하기 위해 사용된다. 프로토타입은 어떤 객체의 상위 객체의 역할을 하는 객체로서 다른 객체에 공유 프로퍼티를 제공한다. 프로토타입을 상속받은 하위 객체는 상위 객체의 프로퍼티를 자신의 프로퍼티처럼 자유롭게 사용할 수 있다.

모든 객체는 하나의 프로토타입을 갖는다. 객체, 프로토타입 그리고 생성자 함수는 다음 그림과 같이 연결되어 있다.

<img width="461" alt="image" src="https://github.com/user-attachments/assets/96412b6d-2f8b-42cb-bf70-750d3e7a8996">

---
<br />

```
__proto__ 접근자 프로퍼티

모든 객체는 위 접근자 프로퍼티를 통해 자신의 프로토타입, 즉 [[Prototype]] 내부 슬롯에 간접적으로 접근할 수 있다.
```
<img width="396" alt="image" src="https://github.com/user-attachments/assets/ab3f1ce8-3475-4333-99f5-b077f4d6afbd">

위 접근자 프로퍼티는 객체가 **직접 소유하는 프로퍼티가 아니라** Object.prototype의 프로퍼티다.
모든 객체는 상속을 통해 Object.prototype.__proto 접근자 프로퍼티를 사용 할 수 있다.

[[Prototype]] 내부 슬롯의 값, 즉 프로토타입에 접근하기 위해 접근자 프로퍼티를 사용하는 이유는 상호 참조에 의해 프로토타입 체인이 생성되는 것을 방지하기 위해서이다.

<img width="316" alt="image" src="https://github.com/user-attachments/assets/ddac7509-c3e7-47be-afd7-536b24480248">

위 그림과 같이 순환 참조하는 프로토타입 체인이 만들어지면 프로토타입 체인 종점이 존재하지 않기 때문에 프로토타입 체인에서 프로퍼티를 검색할 때 무한 루프에 빠진다. 따라서 이를 방지하기 위해 __proto 접근자 프로퍼티를 통해 프로토타입에 접근하고 교체하도록 되어 있다.

나중에 나오지만 직접 상속을 통해 Object.prototype을 상속받지 않는 객체가 생성될 수 있기에 코드 내에서 직접 위 접근자 프로퍼티를 사용하는 것은 권장하지 않는다.

<br />

**함수 객체의 prototype 프로퍼티**

함수 객체만이 소유하는 prototype 프로퍼티는 생성자 함수가 생성할 인스턴스의 프로토타입을 가리킨다.

따라서 생성자 함수로서 호출할 수 없는 함수, 즉 non-constructor 인 화살표 함수와 ES6 메서드 축약 표햔으로 정의한 메서드는 prototype 프로퍼티를 소유하지 않으며 프로토타입도 생성하지 않는다.

<img width="558" alt="image" src="https://github.com/user-attachments/assets/7c508eff-bc5b-49a1-9458-2738e38bc45a">

<br />

**프로토타입의 constructor 프로퍼티와 생성자 함수**

모든 프로토타입은 constructor 프로퍼티를 갖는다. 이 프로퍼티는 prototype 프로퍼티로 자신을 참조하고 있는 생성자 함수를 가르킨다. 

<img width="395" alt="image" src="https://github.com/user-attachments/assets/d55b4ece-5e0e-4dc7-a26d-68bf6cafde15">

---
<br />

> 19.4 리터럴 표기법에 의해 생성된 객체의 생성자 함수와 프로토타입

<img width="395" alt="image" src="https://github.com/user-attachments/assets/1ecfdba2-dbd8-472f-b65a-475a7ad8be33">

리터럴 표기법에 의해 생성된 객체도 물론 프로토타입이 존재한다. 하지만 이 경우에 프로토타입의 constructor 프로퍼티가 가르키는 생성자 함수가 반드시 객체를 생성한 생성자 함수라고 단정할 수 없다.

<img width="576" alt="image" src="https://github.com/user-attachments/assets/07c8adb8-49a4-497d-9fbc-f3db8dbd7e0a">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/9b33d274-39bc-41b0-ad57-f56cf022f13a">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/e9cbeed0-1403-42c6-9651-f8fcadcdb3bf">

리터럴 표기법에 의해 생성된 객체도 상속을 위해 프로토타입이 필요하다. 따라서 가상적인 생성자 함수를 갖는다.

프로토 타입은 생성자 함수와 더불어 생성되며 prototype, constructor 프로퍼터에 의해 연결되어 있기 때문이다. 다시 말해, 프로토타입과 생성자 함수는 단독으로 존재할 수 없고 언제나 쌍으로 존재한다.

---
<br />

> 19.5 프로토타입의 생성 시점

객체는 리터럴 표기법 또는 생성자 함수에 의해 생성되는데 결국 모든 객체는 생성자 함수와 연결되어 있다.

프로토타입은 생성자 함수가 생성되는 시점에 더불어 생성된다.

생성자 함수는 사용자가 직접 정의한 사용자 정의 생성자 함수와 JS 빌트인 생성자 함수로 구분할 수 있다.

<br />

**사용자 정의 생성자 함수와 프로토타입 생성 시점**

생성자 함수로서 호출될 수 있는 함수, 즉 constructor는 함수 정의가 평가되어 함수 객체를 생성하는 시점에 프로토타입도 더불어 생성된다. 생성된 프로토타입의 프로토타입은 언제나 Object.prototype이다.

<br />

**빌트인 생성자 함수와 프로토타입 생성 시점**

<img width="569" alt="image" src="https://github.com/user-attachments/assets/83db6be8-7c50-4d8b-a83f-e9192c6040ef">

객체가 생성되기 전에 생성자 함수와 프로토타입은 이미 객체화되어 존재한다. 이후 생성자 함수 또는 리터럴 표기법으로 객체를 생성하면 프로토타입은 생성된 객체의 [[Prototype]] 내부 슬롯에 할당된다.

---
<br />

> 19.6 객체 생성 방식과 프로토타입의 결정

<img width="249" alt="image" src="https://github.com/user-attachments/assets/15ecee3b-a52d-4641-b612-38d2ba51dbbb">

이처럼 다양한 방식으로 생성된 모든 객체는 추상 연산 OrdinaryObjectCreate에 의해 생성된다는 공통점이 있다. 이 추상 연산은 필수적으로 자신이 생성할 객체의 프로토타입을 인수로 전달받는다. 그리고 자신이 생성할 객체에 추가할 프로퍼티 목록을 옵션으로 전달할 수 있다.

즉, 프로토타입은 위 추상 연산에 전달되는 인수에 의해 결정된다. 이 인수는 객체가 생성되는 시점에 객체 생성 방식에 의해 결정된다.

<br />

**객체 리터럴에 의해 생성된 객체의 프로토타입**

추상 연산 OrdinaryObjectCreate에 전달되는 프로토타입은 Object.prototype이다. 즉, 객체 리터럴에 의해 생성되는 객체의 프로토타입은 Object.prototype이다.

<img width="370" alt="image" src="https://github.com/user-attachments/assets/0e4a464e-9167-4b72-860b-281bdbf0145d">

<br />

**Object 생성자 함수에 의해 생성된 객체의 프로토타입**

Object 생성자 함수를 인수 없이 호출하면 빈 객체가 생성된다. 이 경우에도 추상 연산 OrdinaryObjectCreate가 호출되며 해당 연산에 전달되는 프로토타입은 Object.prototype이다.

<img width="586" alt="image" src="https://github.com/user-attachments/assets/db71c381-a517-42df-9a1b-2734d32ec4a6">

<br />

**생성자 함수에 의해 생성된 객체의 프로토타입**

마찬가지로 OrdinaryObjectCreate가 호출되며 해당 추상 연산에 전달되는 프로토타입은 생성자 함수의 prototype 프로퍼티에 바인딩 되어있는 객체이다.

즉, 생성자 함수에 의해 생성되는 객체의 프로토타입은 생성자 함수의 prototype 프로퍼티에 바인딩되어 있는 객체다.

<img width="575" alt="image" src="https://github.com/user-attachments/assets/11ccce56-99d3-4e02-bb24-f9e1690ae14f">

<img width="575" alt="image" src="https://github.com/user-attachments/assets/fbe1b663-37b5-4adf-9b5d-277596955acd">

---
<br />

> 19.7 프로토타입 체인

<img width="572" alt="image" src="https://github.com/user-attachments/assets/085d6e00-20d7-4bdb-89b1-fafae36e5b58">

<img width="572" alt="image" src="https://github.com/user-attachments/assets/2b37e51f-ed6f-4db5-83f5-c33f0415e07b">

프로토타입 체인의 최상위에 있는 객체는 언제나 Object.prototype으로 프로토타입 체인의 종점이라 한다. Object.prototype의 프로토타입, 즉 [[Prototype]] 내부 슬롯의 값은 null이다.

프로토타입 체인의 종점에서도 프로퍼티를 검색할 수 없는 경우 에러가 아닌 undefined를 반환한다.

**프로토타입 체인은 상속과 프로퍼티 검색을 위한 메커니즘**이라 할 수 있다.

프로퍼티가 아닌 식별자는 스코프 체인에서 검색한다. 따라서 **스코프 체인은 식별자 검색을 위한 메커니즘**이라 할 수 있다.

---
<br />

> 19.8 오버라이딩과 프로퍼티 섀도잉

<img width="579" alt="image" src="https://github.com/user-attachments/assets/d26cbf74-97d3-4fa3-9c84-b181776dbc5a">

<img width="564" alt="image" src="https://github.com/user-attachments/assets/d08ea334-cc0c-4f2c-8466-a2935b3f317e">

<img width="571" alt="image" src="https://github.com/user-attachments/assets/7e6f195b-7a1e-4f65-a6eb-ef73c23f3b79">

참고로 프로토타입 프로퍼티를 변경 또는 삭제하려면 하위 객체를 통해 프로토타입 체인으로 접근하는 것이 아닌 프로토타입에 직접 접근해야 한다.

---
<br />

> 19.9 프로토타입의 교체

프로토타입은 생성자 함수 또는 인스턴스에 의해 교체할 수 있다. 즉, 객체 간의 상속 관계를 동적으로 변경할 수 있다.

<br />

**생성자 함수에 의한 프로토타입의 교체**

<img width="571" alt="image" src="https://github.com/user-attachments/assets/6ee0b55e-3bf8-4368-ac55-5aded3d0cde9">

<img width="571" alt="image" src="https://github.com/user-attachments/assets/ea2aabf6-e199-43a5-82c0-30ff419d6858">

<br />

**인스턴스에 의한 프로토타입의 교체**

프로토타입은 생성자 함수의 prototype 프로퍼티뿐만 아니라 인스턴스의 __proto 접근자 프로퍼티를 통해 접근할 수 있고 교체할 수 있다.

생성자 함수의 prototype 프로퍼티에 다른 임의의 객체를 바인딩하는 것은 미래에 생성할 인스턴스의 프로토타입을 교체하는 것이다. __proto 접근자 프로퍼티를 통해 프로토타입을 교체하는 것은 이미 생성된 객체의 프로토타입을 교체하는 것이다.

<img width="539" alt="image" src="https://github.com/user-attachments/assets/892b2fc6-1c87-4f33-8897-8d01d09c6371">

<br />

**차이**

<img width="539" alt="image" src="https://github.com/user-attachments/assets/531b2a5a-289b-4029-95da-10ce70cd3da1">

이처럼 프로토타입 교체를 통해 객체 간의 상속 관계를 동적으로 변경하는 것은 꽤나 번거롭다. 따라서 프로토타입은 직접 교체하지 않는 것이 좋다.

---
<br />

> 19.10 instanceof 연산자

<img width="604" alt="image" src="https://github.com/user-attachments/assets/a14c6eab-f604-42d1-a248-77257cbc03bb">

<img width="604" alt="image" src="https://github.com/user-attachments/assets/867b25ca-e363-4801-89ca-099048bfda3f">

---
<br />

> 19.11 직접 상속

**Object.create에 의한 직접 상속**

Object.create 메서드는 명시적으로 프로토타입을 지정해 새로운 객체를 생성한다. 이 메서드도 다른 객체 생성 방식과 마찬가지로 추상 연산 OrdinaryObjectCreate를 호출한다.

첫 번째 매개변수에는 생성할 객체의 프로토타입으로 지정할 객체를 전달한다. 두 번째 매개변수에는 옵션이며 생성할 객체의 프로퍼티 키와 프로퍼티 디스크립터 객체로 이뤄진 객체를 전달한다.

<img width="449" alt="image" src="https://github.com/user-attachments/assets/139a8b89-0fe1-49b6-a7d4-42cb8274d819">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/c92523e5-855f-4607-88d5-a4020d1e652a">

<br />

**객체 리터럴 내부에서 __proto 에 의한 직접 상속**

Object.create 메서드에 의한 직접 상속은 위에서 언급한 것과 같은 장점이 있다. 하지만 두 번째 인자로 프로퍼티를 정의하는 것은 번거롭다. ES6에서는 객체 리터럴 내부에서 __proto 접근자를 이용해 직접 상속을 구현할 수 있다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/0cf2c893-7f2e-467a-9f05-4894d3b0b30d">

---
<br />

> 19.12 정적 프로퍼티/메서드

정적 프로퍼티/메서드는 생성자 함수로 인스턴스를 생성하지 않아도 참조/호출할 수 있는 프로퍼티/메서드를 말한다.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/790d1c2c-f390-4e42-81f1-cbbd0c4a0d3d">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/b4d07339-1a83-4564-8a2e-d4b27ae510f8">

<img width="586" alt="image" src="https://github.com/user-attachments/assets/77801a7b-1993-4d39-84e5-ed9c62fe43dc">

---
<br />

> 19.13 프로퍼티 존재 확인

**in 연산자**

해당 연산자는 객체 내의 특정 프로퍼티가 존재하는 지 여부를 확인한다.

<img width="586" alt="image" src="https://github.com/user-attachments/assets/be6ea7fb-5d43-45af-a073-9b4bac62a926">

ES6 에서 도입된 Reflect.has 메서드를 대신 사용할 수 있다. 동일하게 동작한다.

<br />

**Object.prototype.hasOwnProperty 메서드**

<img width="586" alt="image" src="https://github.com/user-attachments/assets/69378007-1ccb-440b-8f87-12039e520232">

---
<br />

> 19.14 프로퍼티 열거

**for ... in 문**

객체의 모든 프로퍼티를 순회하며 열거하려면 위 문을 사용한다.

for ... in 문은 객체의 프로토타입 체인 상에 존재하는 모든 프로토타입의 프로퍼티 중에서 프로퍼티 어트리뷰트 [[Enumerable]] 값이 true인 프로퍼티를 순회하며 열거한다.

for...in문은 프로퍼티를 열거할 때 순서를 보장하지 않지만 모던 브라우저는 순서를 보장하고 숫자(사실 문자열)인 프로퍼티 키에 대해서는 정렬을 실시한다.

배열에서는 위 문이 아닌 일반적인 for문이나 for ... of 문 또는 Array.prototype.forEach메서드를 사용하기 권장한다. 배열도 객체이므로 프로퍼티와 상속받은 프로퍼티가 포함될 수 있다.

<br />

**Object.keys/values/entries 메서드**

for...in 문은 객체 자신의 고유 프로퍼티뿐 아니라 상속받은 프로퍼티도 열거한다.

객체 자신의 고유 프로퍼티만 열거하려면 위 문을 사용하는게 좋다.

<img width="586" alt="image" src="https://github.com/user-attachments/assets/2e7717af-2f0f-427b-abbd-ef07527c8388">

<img width="586" alt="image" src="https://github.com/user-attachments/assets/5c2aa58f-8ac3-4d4c-9e08-49031027c360">
