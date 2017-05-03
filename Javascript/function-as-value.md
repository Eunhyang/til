JS에서 함수?

> `funtion a(){}` = `var a = fuction(){}`

- a : 변수 = key = 속성(props) 
- function(){} : 객체 =  {} = 값(Value) = 변수에 담길 수 있다. 
- `a= {b:function(){}} ` 객체 안에 정의되어 있다면? b는**<u>method</u>**라 불림
- 따라서 함수는 인자로도 전달될 수 있다.

````
function cal(func,num){
  return func(num) //func에 함수가 인자로 전달됨
}

function increase(num){
  return num+1
}

alert(cal(increase, 1));
````

