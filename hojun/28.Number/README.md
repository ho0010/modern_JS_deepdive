표준 빌트인 객체인 Number는 원시 타입인 숫자를 다룰 때 유용한 프로퍼티와 메서드를 제공한다.

## Number 생성자 함수

Number 객체는 생성자 함수 객체다. 따라서 new 연산자와 함께 호출해 Number 인스턴스를 생성할 수 있다. Number 생성자 함수에 인수를 전달하지 않고 new 연산자와 함께 호출하면 [[NumberData]] 내부 슬롯에 0을 할당한 Number 래퍼 객체를 생성한다.

크롬 개발자 도구에서 확인해보면 [[PrimitiveValue]]라는 접근할 수 없는 프로퍼티가 보인다. 이는 [[NumberData]] 내부 슬롯을 가르킨다. ES5에서는 [[NumberDate]]를 [[PrimitiveValue]]라 불렀다.

## Number 프로퍼티

### Number.EPSILON

ES6에서 도입된 EPSILON은 1과 1보다 큰 숫자 중에서 가장 작은 숫자와의 차이와 같다. 약, 2.22044...*10^-16이다. 그냥 겁나 작은 숫자라는 뜼

부동 소수점 산술 연산은 정확한 결과를 기대하기 어렵다. 정수는 2진법으로 오차 없이 저장 가능하지만 부동소수점을 표현하기 위해 가장 널리 쓰이는 표준인 IEEE 754는 2진법으로 변환했을 때 무한소수가 되어 미세한 오차가 발생할 수 밖에 없는 구조적 한계가 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/299f7e4f-2f04-42d2-985d-0fcc36fa99db">


### Number.MAX_VALUE

MAX_VALUE는 JS에서 표현할 수 있는 가장 큰 양수 값 (1.79679...*10^308)이다. 이 숫자보다 큰 숫자는 Infinity다.

### Number.MIN_VALUE

MIN_VALUE는 JS에서 표현할 수 있는 가장 작은 양수 값(5*10^-324)이다. 이보다 작은 숫자는 0이다.

### Number.MAX_SAFE_INTEGER

JS에서 안전하게 표현할 수 있는 가장 큰 정수값이다.

### Number.MIN_SAFE_INTEGER

JS에서 안전하게 표현할 수 있는 가장 작은 정수값이다.

### Number.POSITIVE_INFINITY

양의 무한대를 나타내는 숫자값 Infinity와 같다.

### Number.NEGATIVE_INFINITY

음의 무한대를 나타내는 숫자값 -Infinity와 같다.

### Number.NaN

숫자가 아님을 나타내는 숫자값이다. window.NaN과 같다.

## Number 메서드

### number.isFinite

ES6에서 도입된 정적 메서드로 인수로 전달된 숫자값이 정상적인 유한수, 즉 Infinity 또는 -Infinity가 아닌지 검사해 그 결과 값을 불리언 값으로 변환한다.

### Number.isInteger

ES6에서 도입된 정적 메서드로 인수로 전달된 숫자값이 정수인지 검사해 그 결과를 불리언 값으로 반환한다. 검사 전 암묵적 타입 변환이 이루어지지 않는다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/9d3f2359-dc8b-437b-bd2d-c1a0e9a37830">

### Number.isNaN

ES6에서 도입된 정적 메서드로 인수로 전달된 숫자값이 NaN인지 검사해 그 결과를 불리언 값으로 반환한다. 빌트인 전역 함수 isNaN과 차이가 있다. Number.isNaN은 전달받은 인수를 숫자로 암묵적 타입변환하지 않는다. 즉, 숫자가 아닌 인수가 주어졌을 때는 언제가 false를 반환한다.

### Number.isSafeInteger

ES6에서 도입된 정적 메서드로 인수로 전달된 값이 안전한 정수인지 검사해 그 결과를 불리언 값으로 반환한다. 안전한 정수값은 -(2^53-1)과 2^53-1사이의 정수값이다. 검사전 암묵적 타입변환이 이루어지지 않는다.

### Number.prototype.toExponential

숫자를 지수 표기법으로 변환해 문자열로 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/af6d0025-50b9-4cca-aaf6-9bdcef583525">

### Number.prototype.toFixed

숫자를 반올림해 문자열로 반환한다. 반올림하는 소수점 이하 자릿수를 나타내는 0~20사이의 정수값을 인수로 전달할 수 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/f354c868-dfc9-4e4f-849a-b413d646b2cb">

### Number.prototype.toPrecision

인수로 전달받은 전체 자릿수까지 유효하도록 나머지 자릿수를 반올림해 문자열로 반환한다. 인수로 전달받은 전체 자릿수로 표현할 수 없는 경우 지수 표기법으로 결과를 반환한다. 전체 자릿수를 나타내는 0~21사이의 정수값을 인수로 전달할 수 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/4127d57a-7eb8-40e4-bd15-e387146b3312">

### Number.prototype.toString

숫자를 문자열로 변환해 반환한다. 진법을 나타내는 2~36사이의 정수값을 인수로 전달할 수 있다.
