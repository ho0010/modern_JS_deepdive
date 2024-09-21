> 9.1 타입 변환이란?

타입 변환은 크게 두 가지로 생각해볼 수 있다


**명시적 타입 변환(explicit coercion) or 타입 캐스팅**


**암묵적 타입 변환(implicit coercion) or 타입 강제 변환(type coercion)**

주의할 점은 두 가지 변환 모두 기존의 원시 값을 직접 변경하는 것이 아니라 기존 원시 값을 사용해 다른 타입의 새로운 원시 값을 생성하는 것이다

++ 원시 값은 변경 불가능한 값

암묵적 타입 변환이 개발자가 아닌 JS엔진이 하는 것이라고 해서 무조건적으로 암묵적 타입 변환을 지양해야 하는 것은 아니다

때때로 가독성측면에서 암묵적 타입 변환이 유리할 수 있다

<br />

---

> 9.2 암묵적 타입 변환

JS 엔진은 표현식을 평가할 때 개발자의 의도와는 상관없이 코드의 문맥을 고려해 암묵적 타입 변환을 할 때가 있다

- 문자열 타입으로 변환

```
1 + '2' // -> "12"
```
지난 챕터에서 언급했던 것처럼 + 연산자는 문자열이 한 개 이상 있을 때 문자열 연결 연산을 수행한다


이때 숫자 1은 문자열 타입으로 암묵적 타입 변환된다

<br />

- 숫자 타입으로 변환

```
1 - '1' // -> 0
1 * '10' // -> 10
1 / 'one' // -> NaN
```
위 예제에서 사용한 연산자는 모두 산술 연산자다

산술 연산자 표현식을 평가하기 위해 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다

피연산자를 숫자타입으로 변환할 수 없다면 NaN을 반환한다

<br />

```
'1' > 0 // -> true
```
비교 연산자 또한 위와 같다

<br />

<img width="174" alt="image" src="https://github.com/user-attachments/assets/7bcba40e-ec84-4dc8-8cb7-e4252951cefe">



"+" 단항 연산자는 피연산자가 숫자 타입의 값이 아니면 숫자 타입의 값으로 암묵적 타입 변환을 수행한다
  
<br />

<img width="507" alt="image" src="https://github.com/user-attachments/assets/0c132e4a-e97c-46a6-a497-61e1def4239f">


<br />

- 불리언 타입으로 변환
  
불리언 타입에서의 암묵적 타입 변환이 동일하다

<br />

---

> 9.3 명시적 타입 변환

개발자의 의도에 따라 명시적으로 타입을 변경하는 방법은 다양하다

**표준 빌트인 생성자 함수(String, Number, Boolean)를 new 연산자 없이 호출하는 방법**

**빌트인 메서드를 사용하는 방법**

<br />

- 문자열 타입으로 변환

1. String 생성자 함수를 new 연산자 없이 호출
```
String(1); // -> "1"
```
2. Object.prototype.toString 메서드 사용
```
(1).toString(); // -> "1"
```
3. 문자열 연결 연산자를 이용하는 방법 (암묵적)
```
1 + ''; // -> "1"
```

<br />

- 숫자 타입으로 변환

1. Number 생성자 함수를 new 연사자 없이 호출
```
Number('0'); // -> 0
```
2. parseInt, parseFloat 함수를 사용
```
parseInt('0'); // -> 0
```
3. "+" 단항 산술 연산자 이용 (암묵적)
  
4. "*" 산술 연산자 (암묵적)
  
<br />

- 불리언 타입으로 변환

1. Boolean 생성자 함수를 new 연산자 없이 호출
```
Boolean('x'); // -> true
Boolean(''); // -> false
Boolean('false'); // -> true
Boolean(NaN); // -> false
Boolean(null); // -> false
Boolean(undefined); // -> false
Boolean({); // -> true
Boolean([]); // -> true
```

2. ! 부정 논리 연산자를 두 번 사용하는 방법
```
!!'x'; // -> true
!!0; // -> false
```
<br />

---

> 9.4 단축 평가

- 논리 연산자를 사용한 단축 평가

논리합(||) or 논리곱(&&) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있음을 기억하자

위의 연산자 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다

<br />

<img width="341" alt="image" src="https://github.com/user-attachments/assets/2ec80d98-49cb-49b2-9949-00752d9dcd36">

<br />

논리합(||) or 논리곱(&&) 연산자는 이처럼 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다

이를 **단축 평가**라 한다. 즉, 평가도중 평가 결과가 확정된다면 나머지 평가 과정을 생략하는 것이다

<br />

단축평가를 이용하면 if문을 대체할 수 있다

```
const done = true;
var message = '';

if(done) message = '완료';

// 생략 ver
message = done && '완료';
console.log(message); // 완료
```

```
const done = false;
var message = '';

if(done) message = '미완료';

// 생략 ver
message = done || '미완료';
console.log(message); // 미완료
```

if...else 문을 삼항 연산자로 대체할 수 있다

---
<br />

- 객체를 가르키기를 기대하는 변수가 null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조 할때
<br />

<img width="628" alt="image" src="https://github.com/user-attachments/assets/950f15e8-c438-4bac-a979-6438059e6ba0">

---
<br />


- 함수 매개변수에 기본값을 설정할 때
<br />

<img width="347" alt="image" src="https://github.com/user-attachments/assets/28068690-7c28-4a69-b95b-1a07b5c6197e">

---
<br />

- 옵셔널 체이닝 연산자

옵셔널 체이닝 연산자 ?.는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다

<br />

<img width="723" alt="image" src="https://github.com/user-attachments/assets/02bb15e0-1b83-413c-8b61-afaeddbf5a2c">

---
<br />

- null 병합 연산자

null 병합 연산자 ??는 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다

기본값 설정에 유용
