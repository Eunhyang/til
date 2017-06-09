## Javascript function

> 하나의 로직을 재실행 할 수 있도록 하는 것
>
> 코드의 재사용성을 높여줌

```javascript
function 함수명(인자...){
  코드..
  retrun 반환값
}
```

함수를 정의하는 또 다른 방법

```javascript
var numbering = function(){
  i = 0;
  while(i<10){
    document.write(i);
    i +=1;
  }
}
numbering();
```

