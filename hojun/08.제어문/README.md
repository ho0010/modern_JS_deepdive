> 8.1 블록문

- 블록문은 0개 이상의 문을 중괄호로 묶은 것으로, 코드 블록 또는 블록이라고 부르기도 한다
- JS는 블록문을 하나의 실행 단위로 취급한다
- 블록문은 언제나 문의 종료를 의미하는 자체 종결성을 갖기 때문에 블록문의 끝에는 세미콜론을 붙이지 않는다

<br />

> 8.2 조건문

- if...else 문
  if문의 조건식은 불리언 값으로 평가되어야 하며 만약 불리언 값이 아닌 값으로 평가되면 JS엔진에 의해 암묵적 타입변환이 이루어진다

- switch 문
  
```
switch (표현식) {
  case 표현식1:
    switch 문의 표현식과 표현식1이 일치하면 실행될 문;
    break;
  case 표현식2:
    switch 문의 표현식과 표현식1이 일치하면 실행될 문;
    break;
  default:
    switch 문의 표현식과 일치하는 case 문이 없을 때 실행될 문;
}
```
break를 사용하지 않으면 폴스루가 일어날 수 있다
++ 폴스루란 표현식과 case의 표현식이 일치했으나 break를 하지않아 다음 실행문들이 전부 실행되는 것이다

if...else문보다 조건문이 많아 가독성이떨어질 수 있다. if...else문으로 해결할 수 있다면 이를 사용하는게 현명하다.

<br />

> 8.3 반복문

JS는 for문, while문, do...while문을 제공한다 (이는 다른 언어에서도 충분히 다루었기에 자세히 다루지 않는다)

```
++ JS는 반복문을 대체할 수 있는 다양한 기능을 제공한다
배열 순회시 사용할 수 있는 forEach 메서드
객체의 프로퍼티를 열거할때 사용하는 for...in 문
ES6에서 도입된 이터러블을 순회할 수 있는 for...of문
```

<br />

>  8.4 break 문

break 문은 레이블 문, 반복문 또는 switch 문의 코드 블록을 탈출한다.

++ 레이블 문은 식별자가 붙은 문을 이야기한다

위의 코드 블록 외에 break 문을 사용하면 SyntaxError가 발생한다

<br />

중첩된 for문의 내부 for문에서 break 문을 실행하면 내부 for문을 탈출해 외부 for 문으로 진입한다

이때 내부 for 문이 아닌 외부 for 문을 탈출하려면 레이블 문을 사용한다 

```
outer: for ( var i = 0; i < 3; i++){
  for(var j = 0; j < 3; j++){
    if(i + j === 3) break outer;
    console.log(`inner[${i}, ${j}]`);
  }
}
console.log('Done!');
```

<br />

> 8.5 continue 문

continue 문은 반복문의 코드 블록 실행을 현 지점에서 중단하고 반복문의 증감식으로 실행 흐름을 이동시킨다.

<img width="508" alt="image" src="https://github.com/user-attachments/assets/637b2935-374b-4fec-834a-f88f078bd074">
