## Element Object

> 엘리먼트를 추상화한 객체
>
> Element는 마크업 언어의 일반적인 규격에 대한 속성을 정의하고 있고, 각각의 구체적인 언어(HTML, XML, SVG)를 위한 기능은 HTMElement, SVGElement, XULElement와 같은 객체를 통해 추가해서 사용



![img](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/904/2240.png)



#### 식별자 API

- 엘리먼트를 제어하기 위해서는 엘리먼트를 **조회하기 위한 식별자**가 필요
- HTML 식별자
  ​
  - 엘리먼트의 이름
  - id
  - class
- 식별자 API: 이 식별자를 가져오고 변경하는 역할



**<u>Element.tagName</u>**

해당 엘리먼트의 태그 이름을 알아냄 (태그 이름을 변경하지는 못함)

```javascript
console.log(document.getElementById('active').tagName)
```

=> id 

```javascript
var active = document.getElementById('active');
console.log(active.id);
active.id = 'deactive';
console.log(active.id);
```

=> className

```javascript
var active = document.getElementById('active');
//class 값을 변경할 때는 프로퍼티의 이름으로 className을 사용
active.className = "important current";
console.log(active.className);
//클래스를 추가할 때는 아래와 같이 문자열을 더함
active.classNmae += "readed";
```

=> classList(className에 비해 훨씬 편리한 사용성)

```javascript
function loop(){
  for(var i=0; i<active.classList.length; i++){
    console.log(i, active.classList[i]);
  }
}
```

