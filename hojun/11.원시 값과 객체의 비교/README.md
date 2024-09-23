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

> 11.2 객체
