## REST API

>  Representational safe transger(REST)

웹의 창시자(HTTP) 중의 한 사람인 Roy Fielding의 2000년 논문에 의해 소개됨

현재의 아키텍쳐가 웹의 본래 설계의 우수성을 많이 사용하지 못하고 있다고 판단했기 때문에, 웹의 장점을 최대한 활용할 수 있는 네트워크 기반의 아키텍처를 소개



#### API

Application Programming Interface

> 응용 프로그램에서 사용할 수 있도록 운영체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스
>
> 주로 파일 제어, 창 제어, 화상 처리, 문자 제어 등을 위한 인터페이스 제공

예) API를 통해 소스 및 데이터베이스는 접근하지 못하게하고 해당 프로그램을 사용할 수 있도록 기능을 제공



#### 배경

하나의 클라이언트를 위한 서버를 구성하는 것은 비효율적인 일

- 클라이언트가 다양해졌기 때문
- 서비스가 여러 플랫폼을 지원해야할 때, 혹은 API로서 공개되어야 할 때, 설명을 간결하게 해주는 것이며 여러가지 문제 상황을 지혜롭게 해결(버전, 포맷/언어 선택 등) 

=> 하나의 서버로 여러대의 클라이언트를 대응하도록 할 때 필요한 것이 RESTFul API



#### 중심규칙

- URI는 정보의 자원을 표현해야 함
- 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)으로 표현



#### 특징

- Stateless : Statelessness
  - 이전, 이후에 대한 직접적인 정보가 필요없이 직관적인 오브젝트에의 접근으로 서비스를 처리
  - 쿠키, 세션 필요 없음
-  URI 이용 : Addressability
  - 예) 서울대학교의 대학원생 중 학번이 1234567인 사람의 정보를 얻어오자 =>`www.univinfo.co.kr/seouluniv/undergraduate/1234567`
  - 특정 오브젝트에 접근할 때 특정 URI를 통한 접근이 가능한지가 중요
- HTTP 메소드를 사용 : Homogeneous Interface
  - 동종의 인터페이스만을 사용
  - 한편으로는 단점
    - CRUD유형으로 분류할 수 없는 작업에 대해서는 어떻게 처리해야할지 모호해짐



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


#### URI 설계

URI? Uniform Resource Identifier, 균등한 리소스 식별자

-> 인터넷의 어떠한 리소스를 식별하기 위해 만들어진 것

- 소문자만 사용하도록 하자(대소문자 구분)
  - `http://abc.com/haha`
  - = `HTTP://ABC.COM/haha`
  - not = `http://abc.com/HAHA`
- 하이픈을 사용하자
- 확장자를 사용하지 말자




참조

[REST API의 이해와 설계1-개념 소개](http://bcho.tistory.com/953)



