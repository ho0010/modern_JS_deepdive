위 장에서 7가지 데이터 타입을 크게 원시 타입과 객체 타입으로 구분했었는데 두 가지 타입으로 구분하는 이유가 무엇일까?

두 타입이 근본적으로 다르다는 의미이며 크게 세 가지 측면에서 다르다

<table border="1">
  <tr>
    <th>Type</th>
    <th>Mutable/Immutable</th>
    <th>Assignment (Stored in Memory)</th>
    <th>Passing Type</th>
  </tr>
  <tr>
    <td>Primitive Value</td>
    <td>Immutable</td>
    <td>Actual value stored</td>
    <td>Passed by value (copy of actual value)</td>
  </tr>
  <tr>
    <td>Object</td>
    <td>Mutable</td>
    <td>Reference (address) stored</td>
    <td>Passed by reference (copy of reference)</td>
  </tr>
</table>

<br />

> 11.1 원시 값

원시 값은 변경 불가능한 값이다

변경 불가능하다는 것은 변수가 아니라 값에 대한 진술이다

변수는 언제든지 재할당을 통해 변수 값을 변경(교체)할 수 있다

- 상수

상수도 값을 저장하기 위한 메모리 공간이 필요하므로 변수라고 할 수 있다. 단, 상수는 단 한 번만 할당이 허용되므로 변수 값을 변경(교체)할 수 없다. 따라서 상수와 변경 불가능한 값을 동일시하는 것은 곤란하다. **상수는 재할당이 금지된 변수일 뿐이다.**

<br />

원시 값은 변경 불가능한 값이기 때문에 값을 직접 변경할 수 없다. 따라서 변수 값을 변경하기 위해 원시 값을 재할당하면 새로운 메모리 공간을 확보하고 재할당한 값을 저장한 후, 변수가 참조하던 메모리 공간의 주소를 변경한다. 값의 이러한 특성을 **불변성** 이라 한다

<img width="413" alt="image" src="https://github.com/user-attachments/assets/7ef2574a-7e96-4bc8-b1d5-0557cbed165b">

**score 변수와 copy 변수의 값 80은 다른 메모리 공간에 저장된 별개의 값이라는 것에 주의**

<br />

> 11.2 객체

객체는 프로퍼티의 개수가 정해져 있지 않으며, 동적으로 변한다. 또한, 프로퍼티 값에도 제약이 없기때문에 객체는 원시 값과 같이 확보해야 할 메모리 공간의 크기를 사전에 정해 둘 수 없다.

객체는 원시 값에 비해 관리하는 방식이 복잡하기 때문에 관련 작업을 할때 상대적으로 많은 리소스를 소비한다.

<img width="545" alt="image" src="https://github.com/user-attachments/assets/732e12cb-d09e-454f-a975-10301824a57c">
<img width="540" alt="image" src="https://github.com/user-attachments/assets/2102e407-d9c0-4852-bdff-4f2684776447">
<img width="533" alt="image" src="https://github.com/user-attachments/assets/5f692099-5c53-4f51-bb22-b0e0f52aa29d">

---

### 객체(참조) 타입의 값, 즉 변경 가능한 값이다

원시 값에서는 할당한 변수가 기억하는 메모리 주소를 통해 메모리 공간에 접근하면 원시 값에 접근할 수 있다
즉, 원시 값을 할당한 변수는 원시 값 자체를 값으로 갖는다

하지만 객체를 할당한 변수가 기억하는 메모리 주소를 통해 메모리 공간에 접근하면 **참조 값(객체가 실제로 저장된 메모리 공간의 주소)** 에 접근할 수 있다

<img width="574" alt="image" src="https://github.com/user-attachments/assets/4f267eb0-6b8e-45f7-8d92-6f3e6f18d026">

---

<img width="550" alt="image" src="https://github.com/user-attachments/assets/4e64efe9-367a-41a6-a1a2-eacb326eb43f">

---

### 참조에 의한 전달

여러 개의 식별자가 하나의 객체를 공유할 수 있다는 것이 무엇을 의미하는 지, 어떤 부작용이 발생하는지 보자

<img width="564" alt="image" src="https://github.com/user-attachments/assets/6040babd-1bd5-4ced-88de-bb2d597c71bc">

<img width="563" alt="image" src="https://github.com/user-attachments/assets/927f10a4-c8ad-44eb-bbe8-0342a38bcd1a">

결국 **"값에 의한 전달"과 "참조에 의한 전달"은 식별자가 기억하는 메모리 공간에 저장되어 있는 값을 복사해서 전달한다는 면에서 동일하다**

다만, 식별자가 기억하는 메모리 공간, 즉 변수에 저장되어 있는 값이 원시 값이냐 참조 값이냐의 차이만 있다

따라서 **JS에는 "참조에 의한 전달"은 존재하지 않고 "값에 의한 전달"만이 존재한다고 말할 수 있다**

JS의 이 같은 동작 방식을 설명하는 정확한 용어가 존재하지 않는다. 이런 이유로 위의 "~전달"이라는 용어가 아닌 "공유에 의한 전달"로 표현하는 경우(ECMAScript 사양에 정의된 공식 용어는 아님)도 있다.

---

### 퀴즈

<img width="569" alt="image" src="https://github.com/user-attachments/assets/c56f572b-d1a8-450e-bb94-6b4f7d9c8380">

