### Django stuydy week2



## 초간단 정규식

[정규식 알아보는 사이트](https://regexper.com/)



## 웹 크롤링

> 크롤링이란?

쿠차!

스타트업 - 초기데이터 구성



GET으로 받을 때 : 웹 브라우저?마다 받을 수 있는 글자수가 다름.



> pip install requests

python으로 http request받아올 수 있음.



> 파싱

가공되지 않는 데이터에서 필요한 데이터만 가져오기

[Beautiful Soup](http://www.crummy.com/software/BeautifulSoup) <= 원하는 부분을 가져오기위해 정규표현식 다 만들기 아주 힘듬. 이를 도와주는 python 라이브러리

````
<a href="(.+?)"
````

? 기능 : __최소__의 "를 찾아서 그사이의 부분만 뽑아올수있도록



> 실습

````
import requests

br = requests.Session()

data = {'csrfmiddlewaretoken':res.cookies['csrftoken'],
        'title':"듣기 좋은 OST 모음",
        'key':"IZwtiaH2ZDc",}
        
br.post("http://127.0.0.1:8000/video/new",data)
````

----



````
br = requests.Session()
````

Session을 만든 것임.

