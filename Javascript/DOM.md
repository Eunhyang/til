## DOM

> Document Object Model
>
> 웹페이지를 자바스크립트로 제어하기 위한 객체 모델
>
> Window 객체의 **document 프로퍼티**를 통해서 사용할 수 있음
>
> **Window 객체**: **창**을 의미/ **Document 객체**: 윈도우에 로드된 **문서**를 의미



#### 제어대상 찾기

- document.getElementByTagName : 인자로 전달된 태그명에 해당하는 객체들을 찾아서 그 리스트를 <u>NodeList</u>라는 유사 배열에 담아서 반환

  - NodeList : 배열은 아니지만 length와 배열접근연산자를 사용해서 엘리먼트를 조회할 수 있음

  ```javascript
  var lis = document.getElementByTagName('li');
  for(var i=0; i<lis.length; i++){
    lis[i].style.color = 'red';
  }
  ```

- document.getElementByClassName 

  ```javascript
  var lis = document.getElementByClassName('active');
  for(var i=0; i<lis.length; i++){
    lis[i].style.color = 'red';
  }
  ```

- document.getElementById (성능면에서 가장 우수)

````javascript
var li = document.getElementById('active');
li.style.color='red';
````

- css 선택자의 문법을 이용해서 객체 조회할 수 있음

  ```javascript
  var li = document.querySelector('li');
  li.style.color='red';
  var li = document.querySelector('.active');
  li.style.color='blue';
  ```

- doucment.querySelectorAll : querySelector과 기본적인 동작방법은 같지만 모든 객체를 조회

```javascript
var lis = document.querySelectorAll('li');
for(var name in lis){
  lis[name].style.color = 'blue';
}
```



#### HTMLElement

=> getElement의 return값??

````javascript
var li = document.getElementById('active');
console.log(li.constructor.name);
var lis = document.getElementByTagName('li');
console.log(lis.constructor.name);
````

-> 실행결과

```
HTMLLIElement
HTMLCollection
```

- document.getElementById : 리턴 데이터 타입은 HTMLLIElement (하나)
- document.getElementByTagName : 리턴 데이터 타입은 HTMLCollection (복수)



엘리먼트 객체에 따라서 프로퍼티가 다르나, 모든 엘리먼트들은 HTMLElement를 상속 받음



#### DOM Tree

> 모든 엘리먼트는 HTMLElement의 자식, 엘리먼트는 Node의 자식, Node는 Object의 자식

![img](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/904/2234.png)