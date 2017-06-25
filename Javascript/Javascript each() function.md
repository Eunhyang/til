#### Javascript each() function

`.each(function(index, element))`

e.g.

```javascript
$("input:checkbox[name='feeling']").each(function(index, item){
  	this.checked = true;
});
```

- index
  - 반복문이 몇바퀴 째인지 알 수 있는 인덱스
  - for문에서 많이 쓰는 i 역할
- element
  - 현재 반복문에서 select되는 element
  - $(element)로 선택
  - this를 대신 사용가능