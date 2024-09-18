# 7️⃣ 연산자

연산자는 하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 타입, 지수 연산 등을 수행해 하나의 값을 만든다.

## 산술 연산자

```
var x = "10;
console.log(+x); // 10
```

숫자 타입이 아닌 피연산자를 숫자 타입으로 변환한다.

## 비교 연산자

### 동등 비교/일치 비교

동등비교(==) : 타입이 다른 피연산자를 비교할 때 피연산자의 타입을 강제로 변환한 후 비교한다.

```
//타입은 다르지만 암묵적 타입 변환을 통해 타입을 일치 => 동등하다 판단
console.log(5 == '5'); // true

'0' == ''; // false
0 == ''; // true
0 == '0'; // true
false == 'false'; // false
false == '0'; // true
```

➡️ 동등 비교 연산자는 예측하기 어려운 결과를 만들어 낸다.</br>
따라서 동등 비교 연산자는 사용하지 않는 편이 좋다.

일치 비교(===) : 타입과 값이 모두 같은 경우에만 true를 반환한다.

```
console.log(5 === 5); // true
console.log(5 === '5'); // false
```

일치 비교 연산자에서 주의할 것은 NaN이다.
NaN은 자신과 일치하지 않는 유일한 값이다.

```
console.log(NaN === NaN); // false
```

## 쉼표 연산자

(,)로 표현식을 연결할 수 있다.

```
var x, y, z;
x = 1, y = 2, z = 3;
console.log(x, y, z); // 1 2 3
```

## typeof 연산자

피연산자의 데이터 타입을 문자열로 반환한다.

```
console.log(typeof 'hello'); // string
console.log(typeof 123); // number
console.log(typeof true); // boolean
console.log(typeof function(){}); // function
console.log(typeof null); // object
console.log(typeof undefined); // undefined
console.log(typeof {}); // object
console.log(typeof []); // object
```

값이 null 타입인지 확인 시 typeof 연산자를 사용하면 안된다.

```
var foo = null;
console.log(typeof foo === null); // false
console.log(foo === null);  // true

```
