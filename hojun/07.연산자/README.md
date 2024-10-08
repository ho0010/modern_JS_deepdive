> 7.1 산술 연산자

- 문자열 연결 연산자
  
  '+' 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다

```
'1' + 2; //'12'

1 + true; // 2

1 + null; // 1
```
JS엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다

이를 **암묵적 타입 변환(implicit coercion)** 또는 **타입 강제 변환(type coercion)** 이라 한다

<br />

> 7.2 할당 연산자

할당문은 표현식인 문일까, 표현식이 아닌 문일까? 

```
var x;

console.log(x = 10); //10
```

할당문은 값으로 평가되는 표현식인 문으로서 할당된 값으로 평가된다

<br />

> 7.3 비교 연산자

동등 비교 연산자와 일치 비교 연산자는 비교하는 엄격성의 정도가 다르다

![image](https://github.com/user-attachments/assets/4d589db0-645f-4e7a-8bc6-f09fabcb2120)

일치 비교(===) 연산자는 암묵적 타입 변환을 하지 않고 값을 비교한다

```
// NaN은 자신과 일치하지 않는 유일한 값이다
NaN === NaN; // false
```
따라서 숫자가 NaN인지 조사하려면 Number.isNaN 을 사용

++
```
// Object.is 메서드
ES6에 도입되었으며 예측 가능한 정확한 비교 결과를 반환한다

-0 === +0; //true
Object.is(-0, +0); // false

NaN === NaN; // false
Object.is(NaN, NaN); //true
```

<br />

> 7.4 삼항 조건 연산자

```
var result = score >= 60 ? 'pass' : 'fail';
```

물음표 앞의 첫 번째 피연산자는 조건식, 즉 불리언 타입의 값으로 평가될 표현식이다

만약 조건식의 평가 결과가 불리언 값이 아니면 불리언 값으로 암묵적 타입 변환된다

if ...else 문과의 차이는 표현식을 값처럼 사용할 수 있다는 것이다

즉, 삼항 조건 연산자 표현식은 값으로 평가할 수 있는 표현식인 문이다

<br />

> 7.5 논리 연산자
||, &&, !

<br />

> 7.6 쉼표 연산자

```
var x, y, z;

x=1, y=2, z=3; // 3 
```

<br />

> 7.7 그룹 연산자

```
10 * (2 + 3); // 50
```
연산자의 우선순위를 조절할 수 있다

<br />

> 7.8 typeof 연산자

```
typeof null // object
```

위 사례는 수정되지 않은 버그이다

값이 null타입인지 확인할 때는 typeof 연산자가 아닌 일치 연산자를 사용하자

<br />

> 7.9 지수 연산자

```
2 ** (3 ** 2); // 512
```

<br />

> 7.10 그 외의 연산자


<img width="569" alt="image" src="https://github.com/user-attachments/assets/77be8d99-ded1-4669-a7f4-f95fd92d215a">


<br />

> 7.11 연산자의 부수 효과

대부분의 연산자는 다른 콛으에 영향을 주지 않는다

하지만 일부 연산자는 다른 코드에 영향을 주는 부수 효과가 있다.

- 할당 연산자(=)
- 증가/감소 연산자(++/--)
- delete 연산자
