## ReactJS

> Facebook 에서 UI개발을 위해 만든 JS 라이브러리

- Redux
- Webpack
- Express
- ES6 
- MongoDB mongoose

> 프레임워크  vs 라이브러리?

- 프레임워크
  - 필요한 기능이 대부분 만들어져 있는 틀! 
  - 틀에서 벗어나기가 어렵다
  - 보통 1가지 프레임워크만 사용, 상황에 따라서 무겁게 느껴질 수도
- 라이브러리
  - 상황에 따라 갖다 쓰면 됨
  - 다른 프레임워크나 라이브러리와 충돌 x
- ReactJS 가 Angular 를 대체 할 수 있을까?
  - 해당 프레임워크 라이브러리를 둘 다 사용해보고 필요한 곳에 적절히 사용하기

> Virtual DOM

- 가상 DOM?
  - 처리해야할 데이터가 많을 경우 관리하기 더 효율적

````
{
  name: "velopert",
  point: 100,
  eyeColor: black,
  nation: "ROK"
}
````

예를 들어, 이런 데이터 셋이 주어지고 값이 업데이트 될 때마다 UI를 업데이트 해야한다?

DOM node들을 기억하는 기능 -> react js

view가 그림만 그리도록 (모델이 데이터 가져다주면 가상 dom이 그림그리고 실제 dom에서는 기억해둔 노드에서 변화만 적용)



#### React and the Virtual Dom

[React and the Virtual Dom](https://www.youtube.com/watch?v=BYbgopx44vo)

React 와 Virtual DOM의 이야기



##### React의 장점?

- 배우기 간단하다
- 뛰어난 Carbage Collection 메모리 관리 성능
- 서버 & 클라이언트 렌더링
  - 서버사이드 렌더링 => 클라이언트 렌더링돼기전에 데이터 문자열로 띄어주어서 유저 편의성 제공
  - 서버사이드 렌더링 => 검색엔진 최적화
- 매우 간편한 UI수정 및 재사용
- 페이스북이 밀어준다
- 다른 프레임워크나 라이브러리와 혼용가능

###### 단점?

- 보여지는 View부분만 관여
- IE8이하 지원 X

