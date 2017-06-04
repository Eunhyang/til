## BOM

> Browser Object Model
>
> 웹 브라우저의 창이나 프레임을 추상화해서 프로그래밍적으로 제어할 수 있도록 제공하는 수단
>
> BOM은 Window의 프로퍼티와 메소드들을 통해서 제어할 수 있음

#### 전역객체 Window

> Window 객체는 모든 객체가 소속된 객체이고, 전역객체이면서 창이나 프레임을 의미

Window 객체는 식별자 window를 통해서 얻을 수 있음/생략 가능

=> Window 객체의 메소드인 alert를 호출하는 방법

```html
<!DOCTYPE html>
<html>
  <script>
  	alert('Hello world');
    wndow.alert('Hello world');
  </script>
  <body>
    
  </body>
</html>
```

=> 전역변수 a에 접근하는 방법

```javascript
var a = 1;
alert(a);
alert(window.a);
```

객체를 만든다는 것 = window객체의 프로퍼티를 만드는 것



#### 커뮤니케이션 기능

- alert `alert('hello world');`

- confirm : 확인을 누르면 true/ 취소를 누르면 false를 rerturn

- prompt 

  ```html
  <input type="button" value="prompt" onclick="func_prompt()" />
  <script>
  	function func_prompt(){
        if(prompt('id?') === 'hyang'){
          alert('welcome');
        }else{
          alert('fail');
        }
  	}
  </script>
  ```



#### Location 객체

> Location 객체는 문서의 주소와 관련된 객체로 Window 객체의 프로퍼티
>
> 윈도우의 문서 URL을 변경할 수 있고, 문서의 위치와 관련해서 다양한 정보를 얻을 수 있음

=> 현재 윈도우의 URL 알아내기

````javascript
console.log(location.toString(), location.href);
````

=> URL Parsing

> location 객체는 URL을 의미에 따라서 별도의 프로퍼티로 제공

```
console.log(location.protocol, location.host, location.port, location.pathname, location.search, location.hash)
```

=> URL 변경하기(현재문서를 http://hyang.net으로 이동)

```
location.href = 'http://hyang.net';
```

```
location = 'http://hyang.net';
```

=> 현재문서 리로드

```
location.reload();
```



#### Navigation 객체

=> 모든 프로퍼티 열람

```
console.dir(navigator);
```

- appName : 웹 브라우저의 이름(IE는 Microsoft Internet Explorer, 파이어폭스와 크롬은 Nescape로 표시)
- appVersion : 브라우저의 버전
- userAgent : 브라우저가 서버측으로 전송하는 USER-AGENT HTTP 헤더의 내용, appVersion과 비슷
- platfrom : 브라우저가 동작하고 있는 운영체제에 대한 정보



#### 창 제어

window.open 메소드는 새 창을 생성 

```html
<input type="button" onclick="open1()" value="window.open('demo2.html');" />
<script>
	function open1(){
      window.open('demo2.html');
	}
</script>
```

- 첫번째 인자는 새 창에 로드할 문서의 URL
- 인자를 생략하면 이름이 붙지 않은 새 창이 만들어짐

```html
<input type="button" onclick="open2()" value="window.open('demo2.html'),'_self';" />
<script>
	function open2(){
      window.open('demo2.html', '_self');
	}
</script>
```

- _self는 스크립트가 실행되는 창을 의미
- _blank는 새 창을 의미 `window.open('demo2.html', '__blank');`
- 창에 이름을 붙일 수 있음. open을 재실행 했을 때 동일한 이름의 창이 있으면 그곳으로 문서가 로드됨 ` window.open('demo2.html', 'ot');`
- 세번째 인자는 새 창의 모양과 관련된 속성 `window.open('demo2.html', '_blank', 'width=200, height=200, resizable=no');`