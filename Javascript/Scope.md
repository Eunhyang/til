# 유효범휘

````
function a(){
    var i = 0;
}
for(var i = 0; i < 5; i++){
    a();
    document.write(i);
````

> 변수가 원래 지역, 전역으로 나누어져있지 않았다!
>
> 문제 발생 (로직의 충돌)-> 지역 변수가 나옴 



**익명함수** : 전역변수가 전혀 없는 함수/ 바로 호출됨

````
(function(){
    var MYAPP = {} //funtion의 지역변수가 됨
    MYAPP.calculator = { // == MYAPP['caluclator']key값에
        'left' : null,
        'right' : null
    }
    MYAPP.coordinate = {
        'left' : null,
        'right' : null
    }
    MYAPP.calculator.left = 10;
    MYAPP.calculator.right = 20;
    function sum(){
        return MYAPP.calculator.left + MYAPP.calculator.right;
    }
    document.write(sum());
}())
````



> __자바스크립트의 지역변수는 <u>함수에서만</u> 유효하다.__

````
for(int i = 0; i < 10; i++){
    String name = "egoing";
}
System.out.println(name);
````



> 정적 유효범위

````
var i = 5;
 
function a(){
    var i = 10;
    b();
}
 
function b(){
    document.write(i);
}
 
a();
````

i 읽을 때 b()안에서 지역변수를 찾게 됨. -> 없다? 바깥의 **전역변수** `var i = 5`가 사용 됨 

=> 사용될 때 가 아니라 __정의될 때__ 사용됨 

- b()가 누구에게 사용될지 알 수 없을 때 사용되는 대상에 따라서 그 대상의 변수에 접근할 수 있다면, <u>동적 유효범위</u>
- 지금처럼 (정의되는 시점의)전역변수에 접근한다면 <u>정적 유효범위</u>

