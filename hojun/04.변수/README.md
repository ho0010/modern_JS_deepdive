> 4.1 변수란 무엇인가? 왜 필요한가


일반적으로 메모리 주소를 통해 값에 직접 접근하는 것은 치명적 오류를 발생시킬 수 있다


때문에 JS는 개발자의 직접적인 메모리 제어를 허용하지 않는다

<br />

프로그래밍에서 어떠한 값을 저장하고 여러번 사용하게 될 일은 정말 많다


그때 메모리 주소로 저장된 값에 직접 접근하는 것이 아닌 값의 위치를 가르키는 상징적인 이름인 **변수**를 이용해 원하는 값에 접근한다

<br />

변수에 값을 저장하는 것 = 할당(assignment)


변수에 저장된 값을 읽어 들이는 것 = 참조(reference)

<br />

> 4.2 식별자

변수 이름을 식별자라고도 한다. (때문에 식별자는 값이 아닌 메모리 주소를 기억한다)

식별자는 어떤 값을 구별해 식별할 수 있는 고유한 이름을 말한다. 또한, 변수 이름에만 국한되는 것이 아닌 함수, 클래스 등의 이름은 모두 식별자이다

<br />


> 4.3 변수 선언

변수 선언 = 변수를 생성하는 것

값을 저장하기 위해 메모리 공간을 확보하고 변수 이름과 확보된 메모리 공간의 주소를 연결해 값을 저장할 수 있게 준비하는 것이다 (해당 공간은 해제되기 전까지 보호됨)

변수를 사용하려면 반드시 선언이 필요하다. 변수 선언시에는 var, let, const 키워드를 사용한다.

```
키워드란 JS 엔진이 수행할 동작을 규정한 일종의 명령어
```

```
var score;

변수 선언(메모리 확보 + JS엔진에 의해 undefined라는 값이 암묵적으로 할당됨)
```

```
변수 이름은 어디에 등록되는가?
모든 식별자는 실행 컨텍스트에 등록된다 (스코프 또한)
변수 이름과 변수 값이 key/value 형식인 객체로 등록되어 관리

실행 컨텍스트란 JS엔진이 소스코드를 평가하고 실행하기 위해 필요한 환경을 제공하고 코드의 실행 결과를 실제로 관리하는 영역
```

<br />


> 4.4 변수 선언의 실행 시점과 변수 호이스팅

```

console.log(score); //undefined

var score;

```


참조 에러가 아닌 undefined가 출력된다

JS 코드는 인터프리터에 의해 한 줄씩 순차적으로 실행된다 

하지만 변수 선언이 소스코드가 한 줄씩 순차적으로 실행되는 시점, 즉 런타임이 아닌 그 이전 단계에서 먼지 실행되기 때문이다.

JS엔진은 런타임 전에 소스코드의 평가 과정을 거친다.

이때, 모든 선언문(변수 선언문, 함수 선언문 등)을 먼저 실행한다.

```
이러한 것처럼 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 것을 변수 호이스팅이라 한다.
```

<br />

> 4.5 값의 할당

변수 선언은 런타임 이전에 먼저 실행되지만 값의 할당은 런타임에 실행된다.

```
console.log(score);

var score = 80;

console.log(score);
```

변수의 선언과 값의 할당을 위 처럼 하나의 문장으로 단축하더라도 JS엔진은 변수의 선언과 값의 할당을 2개의 문으로 나누어 각각 실행한다

또한, 값을 할당할때에 변수 선언시 할당되어있던 메모리의 undefined를 지우고 저장하는 것이 아닌 새로운 메모리 주소에 값을 저장한다
=> 이건 왜이럴까..?

<br />

+++ 책에서는 undefined가 메모리주소를 차지하는 것처럼 나왔으나 찾아보니까 undefined는 값이 할당되지 않았다는 모종의 상태이고 메모리에 특정 주소를 차지하는 값이 아닌것으로 보인다.

또한, 기존 메모리 주소에 값을 덮어씌우는 것보다 새로운 메모리에 저장하는 것이 메모리 관리에 효율적이다.

어차피 참조하지 않게되는 메모리 주소는 가비지컬렉터가 처리 할것이니까

<br />


> 4.6 값의 재할당

```
let score = 80;

score = 100;

```


score에 100이 할당될때에 80이 저장된 메모리 주소에 저장하는게 아니라 새로운 메모리 주소에 저장된다

이유는 4.5에서 설명한 것과 같다
