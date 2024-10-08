> 21.1 JS 객체의 분류

<img width="578" alt="image" src="https://github.com/user-attachments/assets/0506244a-c899-4825-a98c-4ecbebe7b894">

---
<br />

> 21.2 표준 빌트인 객체

<img width="578" alt="image" src="https://github.com/user-attachments/assets/476a76d8-b6d5-480e-96ae-6a2a4d670291">

<img width="578" alt="image" src="https://github.com/user-attachments/assets/964613ed-fc86-4ad4-ae7d-d45204725f88">

표준 빌트인 객체의 prototype 프로퍼티에 바인딩된 객체(예를 들어, String.prototype)는 다양한 기능의 빌트인 프로토타입 메서드를 제공한다. 그리고 표준 빌트인 객체는 인스턴스 없이도 호출 가능한 빌트인 정적 메서드를 제공한다.

<img width="578" alt="image" src="https://github.com/user-attachments/assets/87336cd9-b1ac-4864-834c-e6fad14f21d1">

---
<br />

> 21.3 원시값과 래퍼 객체

<img width="537" alt="image" src="https://github.com/user-attachments/assets/8b71a870-1c1f-41a7-96df-80c7787bc7a6">

<img width="537" alt="image" src="https://github.com/user-attachments/assets/cd0947ee-7d45-43e6-be4d-6e0db72933e3">

**문자열, 숫자, 불리언 값에 대해 객체처럼 접근하면 생성되는 임시 객체를 래퍼 객체라고 한다.**

<img width="578" alt="image" src="https://github.com/user-attachments/assets/06e9db5e-a4d8-478d-968a-9251132c8f0a">

---
<br />

> 21.4 전역객체

전역 객체는 코드가 실행되기 전 JS엔진에 의해 어떤 객체보다 먼저 생성되는 특수한 객체이며, 어떤 객체에도 속하지 않은 최상위 객체다.

브라우저 환경에서는 window가 전역 객체를 가르키지만 Node.js 환경에서는 global이 전역 객체를 가르킨다.

<img width="551" alt="image" src="https://github.com/user-attachments/assets/24ad51c5-8c62-4753-bd60-ff260b80ef48">

<img width="565" alt="image" src="https://github.com/user-attachments/assets/c78c3b4f-1379-4848-9b47-6e00e36631de">

<img width="565" alt="image" src="https://github.com/user-attachments/assets/666ee9c4-89ce-48a6-a8fa-90fb9daf1381">

<img width="482" alt="image" src="https://github.com/user-attachments/assets/512fcbca-a04e-44c7-8320-268400ca365b">

<img width="555" alt="image" src="https://github.com/user-attachments/assets/663ff1a1-0929-4547-b005-a809b8821ccc">

위 처럼 전역 객체는 몇 가지 프로퍼티와 메서드를 가지고 있다. 이 프로퍼티와 메서드는 전역 객체를 가리키는 식별자, 즉 window나 global을 생략해 참조/호출할 수 있으므로 전역 변수와 전역 함수처럼 사용할 수 있다.

<br />

### 빌트인 전역 프로퍼티

전역 객체의 프로퍼티를 의미한다. 주로 애플리케이션 전역에서 사용하는 값을 제공한다.

<br />

<img width="579" alt="image" src="https://github.com/user-attachments/assets/33d58653-86d0-4fab-aecf-eb9c464f9ee6">

<img width="580" alt="image" src="https://github.com/user-attachments/assets/3a7c718d-7546-48dd-8697-533ce4e2d215">

### 빌트인 전역 함수

애플리케이션 전역에서 호출할 수 있는 빌트인 함수로서 전역 객체의 메서드다

<img width="580" alt="image" src="https://github.com/user-attachments/assets/1dbd9d22-405a-40d5-afce-e8e1767966d8">

eval 함수를 사용하게 되면 스코드가 동적으로 수정될 수 있고 JS 엔진에 의해 최적화가 수행되지 않으므로 속도가 느리다. 때문에 eval 함수의 사용은 금지해야 한다.

<br />

<img width="580" alt="image" src="https://github.com/user-attachments/assets/85e1de7e-89a8-4dee-9a55-1a60da6b1567">

유한수가 아니면 보통 false를 반환한다고 보면 좋을 듯

<br />

<img width="580" alt="image" src="https://github.com/user-attachments/assets/d119d5ae-4ace-441e-b38b-4784d0c34ef4">

<img width="415" alt="image" src="https://github.com/user-attachments/assets/5f77c3a3-9370-4761-b828-732bbd5879b3">

<br />

<img width="504" alt="image" src="https://github.com/user-attachments/assets/4cee6817-dfb4-475f-bb29-89a7c0124315">

첫 번째 문자열을 숫자로 변환할 수 없다면 NaN을 반환한다.

<br />

<img width="504" alt="image" src="https://github.com/user-attachments/assets/179b06f3-4589-4bc9-b8f9-0b2dd1b09391">

<img width="504" alt="image" src="https://github.com/user-attachments/assets/c540c492-0a95-48b0-8c88-14bcfd9fb989">

문자열이 아니면 문자열로 변환한 다음, 정수로 해석하여 변환한다.

<img width="570" alt="image" src="https://github.com/user-attachments/assets/7456ec48-2c0c-4c52-b083-5838769ceb3f">

<img width="570" alt="image" src="https://github.com/user-attachments/assets/bcd4a4b3-86ce-4bee-88d2-46343f0d15a5">

<img width="484" alt="image" src="https://github.com/user-attachments/assets/0e373c84-fcd2-4e9b-982c-8a2f0600ad26">

<img width="567" alt="image" src="https://github.com/user-attachments/assets/e9a37841-6e11-408a-8b8b-6f36cccfc7c0">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/b6f188c7-0cc6-4eec-90ec-026e6b708608">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/f5064757-aea2-4430-86b0-af89ebefbb48">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/289bbdb0-4ccd-4671-aa1a-c95cd1ebc91c">

.
<br />

<img width="569" alt="image" src="https://github.com/user-attachments/assets/26bf24db-6c6f-4288-893e-5b9333ace62a">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/2ca8a0fe-f52b-4fd9-a991-9315b572faf4">

<img width="569" alt="image" src="https://github.com/user-attachments/assets/f7833f6c-50e9-4173-8a2a-a2ecafe1a247">

.
<br />

### 암묵적 전역

<img width="549" alt="image" src="https://github.com/user-attachments/assets/78d4bcbe-a1c5-4c03-9424-8afba6ab2205">

foo가 호출 될때 Js 엔진은 y 변수에 값을 할당하기 위해 스코프 체인으로 선언된 변수인지 확인하지만 찾을 수 없으므로 참조에러가 발생한다.

하지만 JS 엔진은 y=20을 window.y = 20으로 해석해 전역 객체에 프로퍼티를 동적으로 생성하고 y는 전역 객체의 프로퍼티가 되어 마치 전역 변수처럼 동작한다. 이를 **암묵적 전역**이라 한다.
