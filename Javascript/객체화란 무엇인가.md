# 객체화(Object model)

> 객체화는 어떤의미?

- 각각의 tag는 다 document가 객체를 생성
- js는 이러한 객체를 다룸



​	**imgs = getElementsByTagName('img');**

=> img 태그 객체들을 배열 형식으로 가져옴

​	**imgs[0]**

=> 첫 번째 img태그

​	**imgs[0].style.width = '300px';**



![DOM](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/904/2229.png)

> Window 객체

전역객체, window & frame 제어

- window.document = Document Object Model
- BOM 

각각의 객체들의 사용법을 익혀서 브라우저가 할 수 있는, 프로그래밍으로 할 수 있는 일과 못 하는 일을 분리 -> 처해 있는 맥락에 맞도록 문제를 해결