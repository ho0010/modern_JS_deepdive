# 1️⃣3️⃣ 스코프

## 스코프란?

스코프(scope)는 **자바스크립트 엔진이 식별자(변수, 함수, 클래스 등의 이름)를 검색할 때 사용하는 규칙**이다.

- 함수의 매개변수는 함수 몸체 내부에서ㅓ만 참조할 수 있고 함수 몸체 외부에서는 참조할 수 없다. 이것은 매개변수를 참조할 수 있는 유효범위, 즉 매개변수의 스코프가 함수 몸체 내부로 한정되기 때문

```
function add(x,y) {
  console.log(x,y); // 2 5
  return x + y;
}

add(2,5);
console.log(x,y); // ReferenceError: x is not defined

```

- 매개변수는 함수 몸체 내부에서만 참조할 수 있다.

### 모든 식별자는 자신이 선언된 위치에 다른 코드가 식별자 자신을 참조할 수 있는 유효범위가 결정된다. 이를 스코프라 한다.

```
let x = 'global';

function foo() {
  let x = 'local';
  console.log(x); // local
}

foo();

console.log(x); // global
```

- 가장 바깥 영역에 선언된 x는 전역 변수이고, foo 함수 내부에 선언된 x는 지역 변수이다. 지역 변수는 자신이 선언된 코드 블록 내부에서만 참조할 수 있다.</br>
  **이름이 동일한 식별자이지만 스코프가 다른 별개의 변수다.**

## 스코프의 종류

- 스코프는 전역 스코프와 지역 스코프로 구분된다.
- 전역 스코프는 코드 어디에서든 참조할 수 있는 전역 변수를 선언할 수 있는 전역 환경을 말한다.
- 지역 스코프는 함수 코드 블록 내부에서만 참조할 수 있는 지역 변수를 선언할 수 있는 지역 환경을 말한다.

```
let x = 'global x';
let y = 'global y';

function outer() {
  let z = 'outer local z';

  console.log(x); // global x
  console.log(y); // global y
  console.log(z); // outer local z

  function inner() {
    let x = 'inner local x';
    console.log(x); // inner local x
    console.log(y); // global y
    console.log(z); // outer local z
  }

  inner();
}

outer();

console.log(x); // global x
console.log(y); // global y

```

- 전역 변수 x와 y는 전역 스코프를 갖는다. 따라서 어디서든 참조할 수 있다.
- 함수 outer 내부에 선언된 지역 변수 z는 함수 outer의 지역 스코프를 갖는다. 따라서 함수 outer 내부에서만 참조할 수 있다.
- 함수 inner 내부에 선언된 지역 변수 x는 함수 inner의 지역 스코프를 갖는다. 따라서 함수 inner 내부에서만 참조할 수 있다.

## 스코프 체인

- 스코프 체인은 스코프가 계층적으로 연결된 것을 말한다.
- 스코프 체인은 스코프가 중첩된 경우, 내부 함수에서 외부 함수의 변수에 접근할 수 있는 메커니즘을 말한다.

let x = 1;

### 함수 레벨 스코프

### 렉시컬 스코프

```

var x = 1;

function foo() {
var x = 10;
bar();
}

function bar() {
console.log(x);
}

foo();
bar();

```

1. 함수를 어디서 호출했는지에 따라 함수의 상위 스코프를 결정한다.
2. 함수를 어디서 정의했는지에 따라 함수의 상위 스코프를 결정한다.
