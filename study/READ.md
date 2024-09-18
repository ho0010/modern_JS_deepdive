# 1주차

<br />

## 1 : false가 나오는 이유??
```
0 == []; //true
0 == "0"; //true
"0" == []; //false
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

