## REST API

>  Representational safe transger(REST)

웹의 창시자(HTTP) 중의 한 사람인 Roy Fielding의 2000년 논문에 의해 소개됨

현재의 아키텍쳐가 웹의 본래 설계의 우수성을 많이 사용하지 못하고 있다고 판단했기 때문에, 웹의 장점을 최대한 활용할 수 있는 네트워크 기반의 아키텍처를 소개



#### REST 기본

요소

- 리소스
- 메서드
- 메시지



예) "(이름이 Terry인) (사용자를) (생성한다)" 라는 호출 -> "**사용자**"는 생성되는 리소스, "**생성한다**"라는 행위는 메서드, "**이름이 Terry인 사용자"**는 메시지

=> REST형태로 표현

```
HTTP POST, http://myweb/user/
{		
	"users":{
      "name":"terry"
	}
}

```

- "생성한다" 메서드 : HTTP POST 메서드
- "사용자" 리소스 : `http://myweb/user/`라는 형태의 url로 표현
- 생성하고자하는 사용자의 디테일한 내용 : JSON문서를 이용해 표현



#### HTTP 메서드

행위에 대한 메서드를 HTTP메서드 그대로 사용

| 메서드    | 의미     | Idempotent |
| ------ | ------ | ---------- |
| POST   | Create | No         |
| GET    | Select | Yes        |
| PUT    | Update | Yes        |
| DELETE | Delete | Yes        |

- 각각 Post, Put, Get, Delete는 각각의 CRUD 메서드에 대응됨

- Idempotent : 여러 번 수행해도 결과가 같은 경우를 의미

  - 예) a++는 Idempotent하지 않다고 하지만(호출시마다 값이 증가되기 때문), a=4와 같은 명령은 반복적으로 수행해도 Idempotent하다(값이 같기 때문)

  - POST연산의 경우에 리소스를 추가하는 연산이기 때문에, Idempotent하지 않지만 나머지 GET, PUT, DELETE는 반복 수행해도 Idempotent함

    ​



참조

[REST API의 이해와 설계1-개념 소개](http://bcho.tistory.com/953)



