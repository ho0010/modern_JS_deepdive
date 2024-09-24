# 9️⃣ 타입 변환과 단축 평가

## 타입 변환이란?

- 자바스크립트는 동적 타입 언어이다. 이는 변수의 타입을 선언하지 않아도 된다는 의미이다. 변수에 할당된 값에 따라 변수의 타입이 동적으로 결정된다.</br>
- 타입 변환이란 변수의 타입을 변경하는 것을 의미한다. </br>
- 타입 변환은 명시적 타입 변환과 암묵적 타입 변환으로 구분할 수 있다.
  - **명시적 타입 변환** : 개발자가 **의도적**으로 값의 타입을 변환하는 것
  - **암묵적 타입 변환** : 자바스크립트 엔진에 의해 **암묵적**으로 타입이 자동 변환되는 것

### 타입 변환이 기존 원시 값을 직접 변경하는 것은 아니다.

원시 값은 변경 불가능한 값이므로 변경할 수 없다. 타입 변환이란 **기존 원시값을 사용해 다른 타입의 새로운 원시값을 생성하는 것**이다.

## 암묵적 타입 변환

자바스크립트 엔진은 표현식을 평가할 때 개발자의 의도와는 상관없이 코드의 문맥을 고려해 암묵적으로 테이터 타입을 강제 변환할 때가 있다.

```
✅ 앞의 문자열 기준으로 뒤의 숫자를 문자열로 변환
'10' + 2 // '102'

✅ 뒤의 숫자를 문자열로 변환
5 * '10' // 50
```

### 문자열 타입으로 변환

```
1 + '2' // '12'
```

- - 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다. 이때 다른 피연산자도 문자열로 타입을 변환한다.

### 숫자 타입으로 변환

```
1 - '1' // 0
1 * '10' // 10
1 / 'one' // NaN
```

- 산술 연산자 표현식을 평가하기 위해 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다. 피연산자를 숫자 타입으로 변환할 수 없다면 NaN을 반환한다.

```
'1' > 0 // true
```

- 비교 연산자도 피연산자의 타입을 일치시키기 위해 필요한 암묵적 타입 변환을 수행한다.

### 불리언 타입으로 변환

```
if ('') console.log('1')
```

- 빈 문자열은 false로 변환된다.

```
if (true) console.log('2')
```

- true는 true로 변환된다.

```
if (0) console.log('3')
```

- 0은 false로 변환된다.

```
if ('0') console.log('4')
```

- '0'은 true로 변환된다.

```
if (null) console.log('5')
```

- null은 false로 변환된다.

```
if (undefined) console.log('6')
```

- undefined는 false로 변환된다.

```
if ({}) console.log('7')
```

- 객체는 true로 변환된다.

```
if ([]) console.log('8')
```

- 배열은 true로 변환된다.

## 명시적 타입 변환

개발자가 의도적으로 값의 타입을 변환하는 것을 말한다.

### 문자열 타입으로 변환

- String 생성자 함수를 new 연산자 없이 호출

```
String(1) // '1'
```

- Object.prototype.toString 메서드 사용

```
(1).toString() // '1'
```

- 문자열 연결 연산자를 이용하는 방법 (암묵적)

```
1 + '' // '1'
```

### 숫자 타입으로 변환

- Number 생성자 함수를 new 연산자 없이 호출

```
Number('0') // 0
```

- parseInt, parseFloat 함수를 사용

```
parseInt('0') // 0
```

- "+" 단항 산술 연산자 이용 (암묵적)
- "\*" 산술 연산자 (암묵적)

### 불리언 타입으로 변환

- Boolean 생성자 함수를 new 연산자 없이 호출

```
Boolean('x') // true
Boolean('') // false
Boolean('false') // true
Boolean(NaN) // false
Boolean(null) // false
Boolean(undefined) // false
Boolean({}) // true
Boolean([]) // true
```

- ! 부정 논리 연산자를 두 번 사용하는 방법

```
!!'x' // true
!!0 // false
```

## 단축 평가

논리 연산자는 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환하지 않는다. 이를 단축 평가라 한다.

### 논리합(||) 연산자

- 두 개의 피연산자 중 어느 하나라도 true로 평가되면 true를 반환한다.
- 두 개의 피연산자가 모두 false로 평가되면 false를 반환한다.
- 첫 번째 피연산자가 객체라면 두 번째 피연산자를 반환한다.

```
'Cat' || 'Dog' // 'Cat'
```

- 첫 번째 피연산자가 객체이므로 두 번째 피연산자인 'Dog'를 평가하지 않고 바로 'Cat'을 반환한다.

```
null || 'Cat' // 'Cat'
```

- 첫 번째 피연산자가 falsy 값이므로 두 번째 피연산자인 'Cat'을 평가한다.

```
'Cat' || null // 'Cat'
```

### 논리곱(&&) 연산자

- 두 개의 피연산자가 모두 true로 평가되면 true를 반환한다.
- 두 개의 피연산자 중 어느 하나라도 false로 평가되면 false를 반환한다.
- 첫 번째 피연산자가 객체라면 두 번째 피연산자를 반환한다.

```
'Cat' && 'Dog' // 'Dog'
```

- 두 피연산자가 모두 truthy 값이므로 두 번째 피연산자인 'Dog'을 반환한다.

```
null && 'Cat' // null
```

- 첫 번째 피연산자가 falsy 값이므로 두 번째 피연산자인 'Cat'을 평가하지 않고 바로 null을 반환한다.

```
'Cat' && null // null
```

- 첫 번째 피연산자가 truthy 값이므로 두 번째 피연산자인 null을 평가한다.

## 단축 평가를 사용한 매개변수의 기본값 설정

```
function getStringLength(str) {
  str = str || '';
  return str.length;
}
```

- 위 코드는 매개변수 str이 falsy 값이면 빈 문자열을 할당한다.

```
function getStringLength(str = '') {
  return str.length;
}
```

- 위 코드는 ES6에서 도입된 매개변수의 기본값 설정을 사용한 것이다.

## null 병합 연산자

```
const name = null;
const userName = name ?? 'Guest';
console.log(userName); // 'Guest'
```

- null 병합 연산자는 좌항이 null 또는 undefined인 경우에만 우항의 피연산자를 반환한다.

## 옵셔널 체이닝 연산자

```
const user = {};
console.log(user.address.street); // TypeError: Cannot read property 'street' of undefined
```

- 위 코드는 user.address가 존재하지 않아 TypeError가 발생한다.

```
const user = {};
console.log(user.address?.street); // undefined
```

- 옵셔널 체이닝 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환한다.

```
const user = {};
console.log(user?.address?.street); // undefined
```

- 옵셔널 체이닝 연산자는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환한다.
