# 1️⃣1️⃣ 원시 값과 객체의 비교

### 원시값과 객체 타입의 다른 점

1. 원시 타입의 값, 즉 원시값은 변경 불가능한 값이다. </br>
   이에 비해 객체(참조) 타입의 값, 즉 객체는 변경 가능한 값이다. </br>
2. 원시 값을 변수에 할당하면 변수에는 실제 값이 저장된다. 이에 비해 객체를 변수에 할당하면 변수에는 참조 값이 저장된다. </br>
3. 원시값을 갖는 변수를 다른 변수에 할당하면 원시값이 복사되어 전달된다. 이를 값에 의한 전달이라 한다. </br>
   이에 비해 객체를 가리키는 변수를 다른 변수에 할당하면 참조 값이 복사되어 전달된다. 이를 참조에 의한 전달이라 한다. </br>

## 원시 값

- 변경 불가능한 값(immutable value) </br>
  변수 : 값을 저장하고 있는 메모리 공간 </br>
  값 : 변수에 저장된 데이터 </br>
  변수에 할당된 값이 변경되는 것이 아니라 새로운 메모리 공간에 새로운 값이 저장되고, 변수는 새로운 메모리 공간을 가리킨다. </br>
  즉, 원시 값은 변경 불가능하다 -> 원시 값 자체를 변경할 수 없다는 것이지 변수 값을 변경할 수 없다는 것은 아니다.

### 값에 의한 전달

- 함수에 인수로 원시 값을 넘기면 함수의 매개변수에는 인수로 넘긴 원시 값이 복사되어 전달된다.

```javascript
let a = 1;
let b = a;
b = 2;
console.log(a, b); // 1 2
```

## 객체

객체는 프로퍼티의 개수가 정해져 있지 않으며, 동적으로추가되고 삭제할 수 있다. 또한 프로퍼티 값으로는 모든 값을 저장할 수 있다. 객체는 변경 가능한 값이다. 객체를 할당한 변수에는 참조 값이 저장된다. 객체를 가리키는 변수를 다른 변수에 할당하면 변수에는 참조 값이 복사되어 전달된다. 이를 참조에 의한 전달이라 한다.

### 변경 가능한 값 (mutable value)

객체 타입의 값, 즉 객체는 변경 가능한 값이다. 객체를 할당한 변수에는 참조 값이 저장된다. 객체를 가리키는 변수를 다른 변수에 할당하면 변수에는 참조 값이 복사되어 전달된다. 이를 참조에 의한 전달이라 한다.

```
let person = {
  name: "Lee",
};

let copy = person;
console.log(copy === person); // true

copy.name = "Kim";
console.log(person.name); // Kim
```

### 참조에 의한 전달

함수에 객체를 인수로 넘기면 함수의 매개변수에는 객체를 가리키는 참조 값이 복사되어 전달된다.

```javascript
let person = {
  name: "Lee",
};

function changeName(person) {
  person.name = "Kim";
}

changeName(person);
console.log(person.name); // Kim
```
