## 배열이란?

```
const arr = ['apple'];
```
위는 배열 리터럴을 통해 생성한 것이다.

요소, 인덱스, length 프로퍼티


### 객체 vs 배열

배열 또한 객체이다. 다만 일반 객체와는 구별된다.

<img width="424" alt="image" src="https://github.com/user-attachments/assets/2a56936b-55ee-4e2d-85c0-6926441ac76a">

명확한 차이점은 "값의 순서"와 "length" 프로퍼티다.


## JS 배열은 배열이 아니다

자료구조에서 말하는 배열은 메모리 공간이 빈틈없이 연속적으로 나열된 자료구조를 말한다.

JS의 배열은 위에서 말하는 배열과는 다르다. 배열 요소의 각각의 메모리 공간은 동일한 크기를 갖지 않아도 되며, 연속적으로 이어져 있지 않을 수도 있다. 배열의 요소가 연속적으로 이어져 있지 않는 배열을 **희소 배열**이라 한다.

JS의 배열은 일반적인 배열의 동작을 흉내 낸 특수한 객체다. 인덱스를 나타내는 문자열을 프로퍼티 키로 갖으며, length 프로퍼티를 갖는다.

### 일반적인 배열과 JS 배열의 장단점

일반적인 배열은 인덱스로 요소에 빠르게 접근할 수 있다. 하지만 요소를 삽입, 삭제하는 경우에는 효율적이지 않다.

JS 배열은 해시 테이블로 구현된 객체이므로 인덱스로 요소에 접근하는 경우 일반적인 배열보다 성능적인 면에서 느릴수밖에 없는 구조적인 단점이 있다. 하지만 요소를 삽입, 삭제하는 경우 일반적인 배열보다 빠른 성능을 기대할 수 있다.

## length 프로퍼티와 희소 배열

length 프로퍼티 값은 요소의 개수, 즉 배열의 길이를 바탕으로 결정되지만 임의의 숫자 값을 명시적으로 할당할 수도 있다. 현재 length 프로퍼티 값보다 작은 숫자 값을 할당하면 배열의 길이가 줄어든다.

<img width="586" alt="image" src="https://github.com/user-attachments/assets/f9be7ec8-74fc-4646-8cee-aacbac02b698">

현재 length 프로퍼티 값보다 큰 숫자 값을 할당하는 경우를 주의하자. 이때 length 프로퍼티 값은 변경되지만 실제로 배열의 길이가 늘어나지는 않는다.

<img width="586" alt="image" src="https://github.com/user-attachments/assets/6dc1a1af-416a-47a2-a460-2f5b39840e67">

<img width="586" alt="image" src="https://github.com/user-attachments/assets/107a538a-c79a-4957-82f8-18fc53c27e21">

이런 경우에는 length 프로퍼티 값은 성공적으로 변경되지만 실제 배열에는 아무런 변함이 없다. 값 없이 비어 있는 요소를 위해 메모리 공간을 확보하지 않으며 빈 요소를 생성하지도 않는다.

## 배열 생성

배열 생성 방식에도 여러가지가 있다.

### 배열 리터럴

배열 리터럴은 0개 이상이 요소를 쉼표로 구분해 대괄호로 묶는다.

ex) const arr = [1, 2, 3]

### Array 생성자 함수

Array 생성자 함수는 전달된 인수의 개수에 따라 다르게 동작하므로 주의를 요한다.

<img width="556" alt="image" src="https://github.com/user-attachments/assets/d622e0f0-aac1-4912-b56e-a609652c2921">

<img width="556" alt="image" src="https://github.com/user-attachments/assets/165e57dd-4d50-4b1d-8b09-f61179efb6ef">


### Array.of

ES6에서 도입된 Array.of 메서드는 전달된 인수를 요소로 갖는 배열을 생성한다. Array 생성자 함수와는 다르게 전달된 인수가 1개이고 숫자이더라도 인수를 요소로 갖는 배열을 생성한다.

### Array.from

ES6에서 도입된 Array.from 메서드는 유사 배열 객체 또는 이터러블 객체를 인수로 전달받아 배열로 변환하여 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/d7e4e018-cc0a-4c68-8ea0-41eb70331407">

## 배열 요소의 참조

배열의 요소를 참조할 때에는 대괄호 표기법을 사용한다. 대괄호 안에는 인덱스가 와야 한다. 정수가 평가되는 표현식이라면 인덱스 대신 사용할 수 있다. 존재하지 않는 요소에 접근하면 undefined가 반환된다.

## 배열 요소의 추가와 갱신

배열에도 요소를 동적으로 추가할 수 있다. 존재하지 않는 인덱스를 사용해 값을 할당하면 새로운 요소가 추가된다. 이때 length 프로퍼티 값은 자동 갱신된다.

## 배열 요소의 삭제

배열은 객체이기 때문에 배열의 요소를 삭제하기 위해 delete 연산자를 사용할 수 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/bfe60147-322a-4f19-a7ad-97a1b3d7af26">

delete 연산자는 객체의 프로퍼티를 삭제한다. 따라서 요소가 삭제된 배열은 희소 배열이 되며 length 프로퍼티 값은 변하지 않는다. 때문에 delete보다 Array.prototype.splice 메서드를 사용하는 것이 좋다.

## 배열 메서드

배열을 다룰 때 유용한 빌트인 메서드를 제공한다.

> 배열에는 원본 배열(배열 메서드를 호출한 배열, 즉 배열 메서드의 구현체 내부에서 this가 가르키는 객체)을 직접 변경하는 메서드와 원본 배열을 직접 변경하지 않고 새로운 배열을 생성해 반환하는 메서드가 있다.

ES5부터 도입된 배열 메서드는 대부분 원본 배열을 직접 변경하지 않지만 초창기 배열 메서드는 원본 배열을 직접 변경하는 경우가 많다. 원본 배열을 직접 변경하는 메서드는 외부 상태를 직접 변경하는 부수 효과가 있으므로 사용할 때 주의해야 한다.

### Array.isArray

위 메서드는 Array  생성자 함수의 정적 메서드다. 전잘된 인수가 배열이면 true, 배열이 아니면 false를 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/37986eb2-fac8-418a-ad2c-c297101eac22">

### Array.prototype.indexOf

위 메서드는 원본 배열에서 인수로 전달된 요소를 검색해 인덱스를 반환한다.

원본 배열에 인수로 전달한 요소와 중복되는 요소가 여러 개 있다면 첫 번째로 검색된 요소의 인덱스를 반환한다.

원본 배열에 인수로 전달한 요소가 존재하지 않으면 -1을 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/072d9741-975d-4fd6-ae1d-67090184bad7">

### Array.prototype.push

push 메서드는 인수로 전달받은 모든 값을 원본 배열의 마지막 요소로 추가하고 변경된 length 프로퍼티 값을 반환한다. push 메서드는 원본 배열을 직접 변경한다.

push 메서드는 성능 면에서 좋지 않다. 마지막 요소로 추가할 요소가 하나뿐이라면 push 메서드를 사용하지 않고 length 프로퍼티를 사용해 배열의 마지막에 요소를 직접 추가할 수 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/01507b38-883b-4c73-8e7c-c96f55c62415">

또한, push 메서드는 원본 배열을 직접 변경하는 부수 효과가 있기 때문에 ES6의 스프레드 문법을 사용하는 편이 좋다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/fa2131aa-987a-484d-92ce-425541c08516">

### Array.prototype.pop

위 메서드는 원본 배열에서 마지막 요소를 제거하고 변경된 배열을 반환한다. 원본 배열을 변경시킨다.

### Array.prototype.unshift

위 메서드는 인수로 전달받은 모든 값을 원본 배열의 선두에 추가하고 변경된 length 프로퍼티 값을 반환한다. 원본 배열을 변경시킨다. 

<img width="588" alt="image" src="https://github.com/user-attachments/assets/4857e1be-5629-4a97-bd87-a3fe357fbbb2">

이 또한 원본 배열을 바꾸는 부수효과를 생각하면 스프레드 연산자를 사용하는 편이 좋다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/a4578922-1ed1-4e76-bbee-210d95c69cc7">

### Array.prototype.shift

위 메서드는 원본 배열에서 첫 번째 요소를 제거하고 변경된 배열을 반환한다. 원본 배열을 변경시킨다.

### Array.prototype.concat

concat 메서드는 인수로 전달된 값들(배열 또는 원시값)을 원본 배열의 마지막 요소로 추가한 새로운 배열을 반환한다. 배열을 인수로 전달하는 경우에 배열을 해체 해 새로운 배열의 요소로 추가한다. 원본 배열은 변경되지 않는다.

push와 unshift의 부수효과를 생각하면 concat을 사용하는 것이 좋다.

주의점

<img width="588" alt="image" src="https://github.com/user-attachments/assets/a03ea954-6520-4c91-9956-db5220b9a847">

concat 메서드는 ES6의 스프레드 문법으로 대체할 수 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/fb7c0c3d-eef5-4968-9f71-19d1b75fd484">

### Array.prototype.splice

push, pop, unshift, shift 메서드는 모두 원본 배열을 직접 변경하는 메서드이며 원본 배열의 처음이나 마지막에 요소를 추가하거나 제거한다. 원본 배열 중간에 요소를 추가하거나 제거하는 경우 splice 메서드를 사용한다. 매개변수가 3개이며 원본 배열을 직접 변경한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/9e0f4caf-3cf5-493e-9b7e-69c2b014882e">

<img width="588" alt="image" src="https://github.com/user-attachments/assets/9b2c2803-422a-4d3b-a08a-b521ee1ed636">

### Array.prototype.slice

slice 메서드는 인수로 전달된 범위의 요소들을 복사해 배열로 반환한다. splice 메서드와 달리 원본 배열은 변경하지 않는다. 

<img width="588" alt="image" src="https://github.com/user-attachments/assets/54308a50-3057-439e-b04c-adb3e16b28a6">

<img width="588" alt="image" src="https://github.com/user-attachments/assets/23fed5fe-f171-4f35-aced-0ebcea80fe69">

<img width="588" alt="image" src="https://github.com/user-attachments/assets/6ae486b4-7b82-4f26-b0ef-a70d66cad27b">

### Array.prototype.join

위 메서드는 원본 배열의 모든 요소를 문자열로 반환한 후, 인수로 전달받은 문자열, 즉 구분자로 연결한 문자열을 반환한다. 구분자는 생략 가능하며 기본 구분자는 콤마다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/8f05e563-2d8a-42b4-8499-2ef90ec16449">

### Array.prototype.reverse

reverse 메서드는 원본 배열의 순서를 반대로 뒤집는다. 원본 배열을 변경시킨다. 반환값은 변경된 배열이다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/e70e71f0-cd88-4219-a3b4-c47298d9aae2">

### Array.prototype.fill

ES6에서 도입된 fill 메서드는 인수로 전달받은 값을 배열의 처음부터 끝까지 요소로 채운다. 원본 배열을 변경시킨다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/8d9a205b-e486-4304-a6ea-e992aabf7477">

### Array.prototype.includes

ES7에서 도입된 includes 메서드는 배열 내에 특정 요소가 포함되어 있는지 확인해 true 또는 false를 반환한다.

두 번째 인수로 검색을 시작할 인덱스를 전달할 수 있다.

### Array.prototype.flat

ES10에서 도입된 flat 메서드는 인수로 전달한 깊이만큼 재귀적으로 배열을 평탄화한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/0ea15380-9bf2-4f99-a993-f7a2225044d2">

## 배열 고차 함수

**고차 함수는 함수를 인수로 전달받거나 함수를 반환하는 함수를 말한다. JS의 함수는 일급 객체이므로 함수를 값처럼 인수로 전달할 수 있으며 반환할 수 있다. 고차 함수는 외부 상태의 변경이나 가변 데이터를 피하고 불변성을 지향하는 함수형 프로그래밍에 기반을 두고 있다.**

**함수형 프로그래밍은 순수 함수와 보조 함수의 조합을 통해 로직 내에 존재하는 조건문과 반복문을 제거해 복잡성을 해결하여 변수의 사용을 억제해 상태 변경을 피하려는 프로그래밍 패러다임이다. 조건문과 반복문은 로직의 흐름을 이해하기 어렵게 하여 가독성을 해치고, 변수는 누군가에 의해 언제든지 변경될 수 있어 오류 발생의 근본적 원인이 될 수 있기 때문이다. 결국 순수 함수를 통해 부수 효과를 최대한 억제하려는 노력과 같다.**

### Array.prototype.sort

sort 메서드는 배열의 요소를 정렬한다. 기본적으로 오름차순으로 요소를 정렬한다. 원본 배열을 직접 변경하며 정렬된 배열을 반환한다. 내림차순을 원하면 sort 후에 reverse 메서드를 사용하는 방법도 있다.

문자열 요소로 이루어진 배열의 정렬은 아무 문제가 없지만 숫자 요소로 이루어진 배열의 정렬은 주의가 필요하다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/03687ca3-2ad3-4702-8582-001e8fbff233">

sort 메서드의 기본 정렬 순서는 유니코드 코드 포인트의 순서를 따른다. 배열의 요소가 숫자 타입이라 할 지라도 배열의 요소를 일시적으로 문자열로 변환한 후 유니코드 코드 포인트의 순서를 기준으로 정렬한다.

때문에 숫자 요소를 정렬할 때는 sort 메서드에 **정렬 순서를 정의하는 비교 함수를 인수로 전달**해야 한다. 비교 함수의 반환값이 0보다 작으면 비교 함수의 첫 번째 인수를 우선해 정렬하고, 0이면 정렬하지 않으며, 0보다 크면 두 번째 인수를 우선해 정렬한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/ce1e81e3-a7ce-4dc9-9f85-be33a727c7d7">

### Array.prototype.forEach

forEach 메서드는 for 문을 대체할 수 있는 고차 함수다. forEach함수는 반복문을 추상화한 고차 함수로서 내부에서 반복문을 통해 자신이 호출한 배열을 순회하면서 수행해야 할 처리를 콜백 함수로 전달받아 반복 호출한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/d52e6d05-9613-4fd0-89c2-5139dfeece5f">

forEach 메서드는 원본 배열을 변경하지 않는다. 하지만 콜백 함수를 통해 원본 배열을 변경할 수 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/e1e4972c-9318-4599-b147-0818d748e95b">

forEach 메서드는 for문에 비해 성능이 좋지는 않지만 가독성은 더 좋다. 

### Array.prototype.map

map 메서드는 자신을 호출한 배열의 모든 요소를 순회하면서 인수로 전달받은 콜백 함수를 반복 호출한다. 그리고 **콜백 함수의 반환값들로 구성된 새로운 배열을 반환한다.** 원본 배열은 변경되지 않는다.

forEach 메서드와 map 메서드의 공통점은 자신을 호출한 배열의 모든 요소를 순회하면서 인수로 전달받은 콜백 함수를 반복 호출한다는 것이다. 하지만 forEach 메서드는 언제나 undefined를 반환하고, map 메서드는 콜백 함수의 반환값들로 구성된 새로운 배열을 반환하는 차이가 있다.

즉, forEach는 단순히 반복문을 대체하기 위한 고차 함수이고, map 메서드는 요소값을 다른 값으로 매핑한 새로운 배열을 생성하기 위한 고차 함수다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/a73ae4a9-d947-493a-95c0-864f3a69b0fa">

<img width="588" alt="image" src="https://github.com/user-attachments/assets/bb63b53f-a31d-4690-b21c-9fa437e517cb">

map 메서드의 콜백 함수 내부에서 this로 사용할 객체를 전달할 수 있다. function 키워드 보다 화살표 함수를 사용하는 것이 유리하다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/59162ca3-c363-49b5-b3ed-d987741fa304">

<img width="588" alt="image" src="https://github.com/user-attachments/assets/99b9ae9f-5c6c-4477-a56b-4d5e4de0bc30">

### Array.prototype.filter

filter 메서드는 자신을 호출한 배열의 모든 요소를 순회하면서 인수로 전달받은 콜백 함수를 반복 호출한다. 그리고 콜백 함수의 반환값이 true인 요소로만 구성된 새로운 배열을 생성한다. 이때 원본 배열은 변경되지 않는다.

filter 메서드는 특정 조건을 만족하는 요소의 배열을 만들기 위한 목적으로 사용되므로 filter 메서드가 생성해 반환한 새로운 배열의 length 프로퍼티 값은 filter 메서드를 호출한 배열의 legnth 프로퍼티 값과 같거나 작다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/3a6efe48-1084-42ca-b763-b7142d651e19">

### Array.prototype.reduce

reduce 메서드는 자신을 호출한 배열을 모든 요소를 순회해 인수로 전달받은 콜백 함수를 반복 호출한다. 그리고 콜백 함수의 반환값을 다음 순회 시에 콜백 함수의 첫 번째 인수로 전달하면서 콜백 함수를 호출해 하나의 결과값을 만들어 반환한다. 이때 원본 배열은 변경되지 않는다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/c64005e2-2cb5-4b08-8351-b30e210647e8">

<img width="588" alt="image" src="https://github.com/user-attachments/assets/d6cf2ef8-7872-4caa-983b-86c94f769166">

reduce를 호출할 때에는 언제나 초기 값을 전달하는 것이 좋다.

### Array.prototype.some

some 메서드는 자신을 호출한 배열의 요소를 순회하면서 인수로 전달된 콜백 함수를 호출한다. 이때 some 메서드는 콜백 함수의 반환값이 단 한 번이라도 참이면 true, 모두 거짓이면 false를 반환한다. 

즉, 배열의 요소 중에 콜백 함수를 통해 정의한 조건을 만족하는 요소가 1개 이상 존재하는지 확인해 그 결과를 불리언 타입으로 반환한다. 단 빈 배열일 경우에 false를 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/3ad41abe-7cc8-493b-b5a1-a107080195a8">

### Array.prototype.every

위 메서드는 자신을 호출한 배열의 요소를 순회하면서 인수로 전달된 콜백 함수를 호출한다. 이때 every 메서드는 콜백 함수의 반환값이 모두 참이면 true, 단 한번이라도 거짓이면 false를 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/eed6cd6b-8371-42da-9416-cc8827016f5a">

### Array.prototype.find

ES6에서 도입된 find 메서드는 자신을 호출한 배열의 요소를 순회하면서 인수로 전달된 콜백 함수를 호출해 반환값이 true인 첫 번재 요소를 반환한다. 없다면 undefined를 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/867f851b-71c3-44c6-97e7-48e38bbfdb03">

### Array.prototype.findIndex

ES6에서 도입된 findIndex 메서드는 자신을 호출한 배열의 요소를 순회하면서 인수로 전달된 콜백 함수를 호출해 반환값이 true인 첫 번째 요소의 인덱스를 반환한다. 없다면 -1 를 반환한다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/becf5203-97dd-40ed-bca9-fd258e644c1d">

### Array.prototype.flatMap

ES10에서 도입된 flatMap 메서드는 map 메서드를 통해 생성된 배열을 평탄화한다. 즉, map 메서드와 flat 메서드를 순차적으로 실행하는 효과가 있다.

<img width="588" alt="image" src="https://github.com/user-attachments/assets/20b165b4-2a98-4a05-99b3-fd969323aa3a">
