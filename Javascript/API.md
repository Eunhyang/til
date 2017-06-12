## 조회 API

> 

```javascript
var list = document.getElementByClassName('marked');
console.group('document');
for(var i=0; i<list.length; i++){
  console.log(list[i].textContent);
}
console.groupEnd();
```

****