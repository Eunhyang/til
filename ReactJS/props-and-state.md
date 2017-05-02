## props

> - 컴포넌트 내부의 Immutable Data
> - JSX 내부에 {this.props.propsName}
> - 컴포넌트를 사용 할 때, < > 괄호 안에 **propsName="value"**
> - **this.props.children**은 기본적으로 갖고있는 props로서, **<Cpnt>**여기에 있는 값이 들어간다.**</Cpnt>**

![ㄴprops](C:\Users\Juhyang\til\img\props.PNG)

- 기본 값 설정 `Component.defaultProps ={...}`
- Type 검증 `Component.propTypes={...}`



## state

> - 유동적인 데이터
> - JSX 내부에 **{ this.state.stateName }**
> - 초기값 설정이 필수, 생성자(constructor) 에서 **this.state = { }** 으로 설정
> - 값을 수정 할 때에는 **this.setState({ val: 'new_val' })**, 렌더링 된 다음엔 **this.state =** 절대 사용하지 말것