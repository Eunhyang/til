ES6 Class

> 6버전부터 지원

- 생성자
- 자바스크립트 class안에서는 method만 만들 수 있음



- 모든 react 컴포넌트는 render 메소드 존재
  - 컴포넌트가 어떻게 생길지 정의해줌
  - JSX? XML같은 문법을 native 자바스크립트로 변환 (babel에서 지원)

JS(Babel)

````
class Codelab extends React.Component{
  render(){
    return(
      <div>Codelab</div>
    );
  }
}

class App extends React.Component {
  render(){
    return(
      <Codelab/>
    );
  }
}

ReactDOM.render(<App/>, document.getElementById('root')); //1.렌더링할 컴포넌트, 2.렌더링할 엘리먼트
````

HTML

````
<div id="root"></div>
````

- 모든 JSX 코드는 container element안에 포함시켜야함

  - ![1](C:\Users\Juhyang\Desktop\1.PNG)

- JSX안에서 자바스크립트 표현하는 방법 =.> {}으로 wrapping

  - `let text = 'Hello React!'` =>사용 `return(<div> {text} </div>);`
  - let?  함수 유효 범위를 갖는 var키워드와 달리 let구문은 블록 유효 범위를 갖는 지역 변수를 선언하며, 임의로 값을 초기화할 수 있다. 
  - ES6에서 변수 선언시 let을 사용하도록 하세요!

- JSX안에서 Style 설정 할때는, string형식을 사용하지 않고 key가 camelCase인 객체가 사용됨

  ````
  let style = {
  backgroundColor:'aqua'
  }
  return(
  <div style={style}>{text}</div>
  );
  ````

- 주석 `{/*내용*/}`, 컴포넌트 안에 있어야 함