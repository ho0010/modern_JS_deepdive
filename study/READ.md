# 1주차

<br />

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
```

