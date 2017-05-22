프로그래밍 패턴 책(지은이: 크리스티나 로페즈)에서 공부한 내용을 바탕으로 TIL을 작성합니다.

#### 코드

[github코드](https://github.com/crista/exercises-in-programming-style)



#### 책 에서 다루는 계산 작업

텍스트 파일을 주면 그 파일에 들어있는 단어와 해당 단어의 빈도 목록을 만들고 빈도를 내림차순으로 출력한다. 이 계산 작업을 **단어 빈도**(term frequency)라 한다. 각 장은 해당 형식의 제약조건을 제시하면서 시작한 다음, 예제 프로그램을 보여주고 그 코드에 대한 상세 설명이 뒤따른다. 



##### 단어빈도?

- 텍스트 파일이 제공되면 가장 빈도가 높은 단어 N(예를 들면 25)개와 그에 해당하는 빈도를 내림차순으로 출력한다.
- 대문자는 모두 소문자로 정규화하고 'the', 'for'등과 같은 의미 없는 단어는 무시해야 한다. 
- 문제를 단순하게 만들기 위해 빈도가 같은 단어의 순서는 신경 쓰지 않는다.



예제

````
Input:
	White tigers live mostly in India
	Wild lions live mostly in Africa
	
Outfut:
	live - 2
	mostly - 2
	africa - 1
	India - 1
	lions - 1
	tigers - 1
	wild - 1
````





