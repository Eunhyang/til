## Ajax (Asynchronous Javascript and XML)

> 웹브라우저와 웹서버가 내부적으로 데이터 통신을 하게 되어 번경된 결과를 웹페이지에 프로그래밍적으로 반영함으로써 웹페이지의 로딩 없이 서비스를 사용할 수 있음

- 비동기적 자바스크립트와 XML?
- 사용하는 API : XMLHttpRequest

참고: [JSON](../Javascript/JSON)

#### 원리

1. 서버에서 특정 데이터를 출력하는 페이지를 만든다.
2. 자바스크립트를 이용해서, 클라이언트 측에서 1에서 만든 서버 페이지에 데이터를 요청하게 만든다.
3. 서버에서 데이터를 받아온 후, 그 데이타를 적절히 parse한 후에 웹사이트에 띄어준다. (document.getElementById("ID").innerHTML("DATA")등등을 이용)

2-3번 내용을 setInterval을 이용해 일정 시간마다 반복되게 만들어주면, 간단한 채팅 프로그램과 같은 것을 만들 수 있다!



Javascript 예제

````html
<html>
  <head>
    <script>
    	var request = new XMLHttpRequest();
      	request.open("GET", "{% url %}")
        request.onreadystatechange = function(){
         if(request.readyState === 4 && request.status === 200){//request가 끝났으며(4)
           document.getElementById("content").innerHTML = request.responseText
         } 
        }
    </script>
  </head>
  <body>
    <div id="content"></div>
  </body>
</html>
````



jQuery 예제

````html
<html>
  <head>
    <script>
    $.ajzx({
      url:"{% url %}",
      method: "GET",
      dataType: "json",
      success: function(data){
        $("#content").html(data);
      }
    })
    </script>
  </head>
  <body>
    <div id="content"></div>
  </body>
</html>
````

```javascript
function changeSequence (zoneId, isOver) {  
    // 목록의 순서를 바꿀 때 바꾸려는 대상이 없을 경우를 제외합니다.
    if (checkSequence(zoneId, isOver)) {
        $.ajax({
            // 전송할 Data를 Post방식으로 전송합니다.
            type : "POST",
            // URL 주소를 설정합니다.
            url : "해당 요청 URL 주소",
            // 전송할 Data를 zoneId, isOver의 이름으로 넘겨줍니다.
            data : {
                        "zoneId" : zoneId, "isOver" : isOver
            },
            // Data를 성공적으로 전송할 경우에 대한 Code 입니다.
            success : function (data) { 
                if (isOver) {
                    // 상위 목록과 위치를 바꾸는 Logic 입니다.
                    ...
                } else {
                    // 하위 목록과 위치를 바꾸는 Logic 입니다.
                    ...
                }
            }
        });
    }
}
```

