## this 키워드

객체는 상태를 나타내는 프로퍼티와 동작을 나타내는 메서드를 하나의 논리적인 단위로 묶은 복합적인 자료구조이다.

동작을 나타내는 메서드는 자신이 속한 객체의 상태, 즉 프로터피를 참조하고 변경할 수 있어야 한다. 이때 메서드가
자신이 속한 객체의 프로퍼티를 참조하려면 먼저 자신이 속한 객체를 가르키는 식별자를 참조할 수 있어야 한다.

<img width="498" alt="image" src="https://github.com/user-attachments/assets/2c2c4ec9-30be-40dd-bb4e-89766257bc4c">

위 그림처럼 자기 자신이 속한 객체를 재귀적으로 참조하는 방식은 일반적이지 않으며 바람지하지도 않다.

<img width="498" alt="image" src="https://github.com/user-attachments/assets/194ca106-2258-4627-a4e6-84d9460a8cde">

> this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가르키는 자기 참조 변수다. this를 통해 자신이 속한
> 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.

this는 JS 엔진에 의해 암묵적으로 생성되며, 코드 어디서든 참조할 수 있다.

**this가 가르키는 값, 즉 this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.**

<img width="502" alt="image" src="https://github.com/user-attachments/assets/8004887e-e845-4a51-96aa-23302919e946">

자바나 C++ 같은 클래스 기반 언어에서 this는 언제나 클래스가 생성하는 인스턴스를 가르킨다. 하지만 **JS의 this는 함수가
호출되는 방식에 따라 this에 바인딩될 값, 즉 this 바인딩이 동적으로 결정된다.**

<img width="512" alt="image" src="https://github.com/user-attachments/assets/9b01bb9a-1747-4eb9-996e-284aa44c779d">


## 함수 호출 방식과 this 바인딩

this 바인딩은 함수 호출 방식, 즉 함수가 어떻게 호출되었는지에 따라 동적으로 결정된다.

1. 일반 함수 호출
2. 메서드 호출
3. 생성자 함수 호출
4. Function.prototype.apply/call/bing 메서드에 의한 간접 호출

---

### 일반 함수 호출

기본적으로 this에는 전역 객체가 바인딩된다.

this는 객체의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로 객체를 생성하지 않는 일반 함수에서 this는 의미가 없다.

때문에, 일반 함수로 호출된 모든 함수(중첩 함수, 콜백 함수 포함) 내부의 this에는 전역 객체가 바인딩된다.

strict mode가 적용된 일반 함수 내부의 this에는 undefined가 바인딩된다.

메서드 내부에서 정의된 중첩 함수나 메서드에 전달된 콜백 함수가 호출될 때, 이 함수들 안에서의 this 키워드는 원래의 객체를 가리키지 않을 수 있다.

이렇게 되면 개발자의 의도대로 this가 바인딩되지 않을 수 있다.

```
const obj = {
  name: 'ChatGPT',
  greet() {
    console.log(`Hello, my name is ${this.name}`);
    
    function innerFunction() {
      console.log(`Inner function: my name is ${this.name}`);
    }
    
    innerFunction();
  }
};

obj.greet();

Hello, my name is ChatGPT
Inner function: my name is undefined
```

이유 : greet 메서드 내에서 innerFunction을 호출할 때, this는 obj객체가 아닌 전역 객체를 가르키게 된다.
이는 JS에서 일반 함수로 호출된 함수(innerFunction)를 실행할 때 this가 전역 객체에 바인딩되기 때문이다

해결책1 :
<img width="569" alt="image" src="https://github.com/user-attachments/assets/6b049026-fde3-4475-b06f-6f62d46ec1ba">


해결책2 : bind 사용

```
const boundInnerFunction = innerFunction.bind(this);
```

해결책3 : 화살표 함수 사용

```
const obj = {
  name: 'ChatGPT',
  greet() {
    console.log(`Hello, my name is ${this.name}`);
    
    const innerFunction = () => {
      console.log(`Inner function: my name is ${this.name}`);
    };
    
    innerFunction();
  }
};

obj.greet();
```

---

### 메서드 호출

**메서드 내부의 this는 메서드를 소유한 객체가 아닌 메서드를 호출한 객체에 바인딩된다.**

<img width="573" alt="image" src="https://github.com/user-attachments/assets/9359abd6-5a74-430b-8035-010d313d878d">

메서드는 프로퍼티에 바인딩된 함수다.
즉, person 객체의 getName 프로퍼티가 가르키는 함수 객체는 person 객체에 포함된 것이 아니라 독립적으로 존재하는 별도의 객체다.
getName 프로퍼티가 함수 객체를 가르키고 있을 뿐이다.

<img width="573" alt="image" src="https://github.com/user-attachments/assets/a09d1573-2e93-4554-b6fd-cd8b24133f4d">

<img width="592" alt="image" src="https://github.com/user-attachments/assets/99d9b07e-4e77-4664-ae4a-2418b3200c94">

메서드 할당되는 부분과 Kim이 나오는 것에 주목

<img width="592" alt="image" src="https://github.com/user-attachments/assets/e97f2e73-5c3d-48c2-89ef-7312462dcde9">

---

### 생성자 함수 호출

생성자 함수 내부의 this에는 생성자 함수가 (미래에) 생성할 인스턴스가 바인딩된다.

<img width="592" alt="image" src="https://github.com/user-attachments/assets/7f008a9e-8a3e-4cd7-aaca-87943dd1059f">

당연하게도 new 연산자를 붙이지 않으면 일반 함수로 동작한다.

---

### Function.prototype.apply/call/bind 메서드에 의한 간접 호출

apply, call, bind 메서드는 Function.prototype의 메서드다. 즉, 이들 메서드는 모든 함수가 상속받아 사용할 수 있다.

<img width="592" alt="image" src="https://github.com/user-attachments/assets/8d61085c-f06e-4459-a03b-7d0c9de76a50">

<img width="592" alt="image" src="https://github.com/user-attachments/assets/8a8b7f48-f915-495e-902e-67fb02636dc1">

apply와 call 메서드의 본질적인 기능은 함수를 호출하는 것이다. 

두 메서드는 인수를 전달하는 방식만 다를 뿐 동일하게 동작한다.

<img width="592" alt="image" src="https://github.com/user-attachments/assets/d4a7a240-e439-4475-a583-112aaf2f0462">

bind 메서드는 apply와 call 메서드와 달리 함수를 호출하지 않는다. 다만 첫 번째 인수로 전달한 값으로
this 바인딩이 교체된 함수를 새롭게 생성해 반환한다.

<img width="592" alt="image" src="https://github.com/user-attachments/assets/3346b5ad-1f4d-4893-bf62-941a475628b8">
