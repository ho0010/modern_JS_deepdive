# 1주차

## 1 : false가 나오는 이유??

```
0 == []; //true
0 == "0"; //true
"0" == []; //false
```

```
암묵적 타입 변환을 잘 생각해보면 됩니다

1. 빈 배열 []은 primitive 값으로 변환될 때 0(Number)이 됩니다.

2. 문자열 “0”이 Number 0으로 변환됩니다.

3. 먼저 []을 primitive 값으로 변환하려고하기 때문에 빈 문자열 “”이 됩니다. 문자열 “0”와 빈문자열 “”를 비교하게 되어 false가 나옵니다.
```

<br />

## 2 : 이때 End of Body, script1, script2, DOMC~~ 순서??

```
<script>
  addEventListener("DOMContentLoaded", () => console.log("DOMContentLoaded"));
</script>
<script src="/script1.js"></script>
  Top of page
<br />
<script src="/script2.js"></script>
  Bottom of page
<script>
  console.log("End of Body");
</script>

1. 이때 End of Body, script1, script2, DOMC~~ 순서??

2. script1, script2 에 async, defer가 붙어있을 때 실행 순서?

3. 반대로 붙었을 때?
```

DOMContentLoaded : 돔트리까지만 형성되면 발생하는 이벤트

### load 이벤트와 다른 점

load 는 돔트리 이후 모든 리소스까지 완벽히 끝난 후 발생하는 이벤트

### <script>

문서를 파싱해 읽다가 자바스크립트를 만나면, 진행하고 있었던 파싱을 멈추고 스크립트를 다운 → 파싱 → 실행한 후 다시 문서를 파싱하게 된다.

스크립트를 다운/파싱/실행할 때까지 문서 파싱이 중단돼 화면 랜딩 시간이 더 소요된다.

### <script async>

문서를 파싱하는 동안 스크립트를 만나면 문서 파싱과 함께 스크립트를 다운받고 스크립트 다운이 완료된 **즉시** 스크립트 실행

### <script defer>

스크립트를 다운로드하지만 문서 파싱을 멈추지 않고 끝까지 수행하고 스크립트는 </html>태그를 만났을 때 실행한다.

### async defer 공통점 : 스크립트를 다운로드하는 동안 문서가 중단되지 않는다.

### 답

1. 1 → 2 → E → D

   스크립트는 순서대로 실행
   하지만 DOMContentLoaded 는 돔트리까지만 형성되면 발생하는 이벤트이기에 제일 마지막에 수행된다.

2. 1(모른다) E → 2 → D

   1번은 async 이기에 언제 다운이 완료되는지 모르기 때문에 언제 실행이 되는지 모른다.
   2번은 defer 파싱후 마지막 실행

   E 는 순서대로

   D 는 DOMContentLoaded 에 의해 제일 마지막

3. 2(모른다) → E → 1 → D

   위와 동일
