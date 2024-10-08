> strict mode란?

<img width="506" alt="image" src="https://github.com/user-attachments/assets/d31569a0-0932-47f7-a7a8-0362c5dcc35d">

x 변수의 선언이 존재하지 않기 때문에 ReferenceError를 발생시킬 것 같지만 JS 엔진은 암묵적으로 전역 객체 x 프로퍼티를 동적 생성한다. 이때 전역 객체의 x 프로퍼티는 마치 전역 변수처럼 사용할 수 있는데 이러한 현상을 **암묵적 전역**이라 한다.

오타나 문법 지식의 미비로 인한 실수는 언제나 발생할 수 있다. 잠재적인 오류를 발생시키기 어려운 개발 환경을 만들고 그 환경에서 개발하는 것이 좀 더 근본적인 해결책이라 할 수 있다.

이를 지원하기 위해 ES5 부터 strict mode가 추가되었다.

해당 기능은 JS 언어의 문법을 좀 더 엄격히 적용해 문제가 될 코드에 대해 명시적 에러를 발생시킨다.

<br />

> 적용

'use strict';
를 전역의 선두 또는 함수 몸체의 선두에 추가하면 된다.

<br />

> 주의

**전역에 사용하는 것은 피하자**

외부 서드파티 라이브러리를 사용하는 경우 라이브러리가 non-strict mode인 경우도 있기에 문제가 생길 수 있다.

**함수 단위로 strict mode를 적용하는 것도 피하자**

일관성 없이 사용하는 것은 바람직 하지 않다.

<br />

> 발생시키는 에러

<img width="506" alt="image" src="https://github.com/user-attachments/assets/33e3d978-ecc1-4d2e-9c9f-6747da8a9446">

<img width="578" alt="image" src="https://github.com/user-attachments/assets/5eb0ce35-2bba-4684-a89b-173d70d5b652">

<br />

> strict mode 적용에 의한 변화

<img width="578" alt="image" src="https://github.com/user-attachments/assets/d6bde3ae-b597-46ab-97dc-3fe43e471899">

