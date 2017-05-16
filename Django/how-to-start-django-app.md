# Django app만들기

1.  vertualenv 설정
2. project 생성
3. app생성
4. 빅 픽처 그리기 - veiws.py 기준
5. 데이터베이스(DB)설정
   1. ERD그리기
   2. models.py에 model 설계
   3. migrate
6. 가짜 view정의 (url - view) : view 목적 설정 (HttpResponse)
7. 진짜 view 정의 (view-models-templates)



#### 1. vertualenv 설정

----

#### 독립환경 설정(Virtual Environment)

> __window__

1. Virtualenv 라이브러리 설치하기 : `pip install Virtualenv`
2. 프로젝트 폴더 생성: `mkdir {{폴더명}}`
3. 프로젝트 폴더 들어가기 : `cd {{폴더명}}`
4. 독립환경 만들기 : `python-m venv {{독립환경명}}`
5. 독립환경 실행 시키기 : `{{독립환경명}}\scripts\activate`

> __mac__

1. pyenv-virtualenv 라이브러리 설치: `brew install pyenv-virtualenv`
2. 터미널 시작 시 자동 반영: `pecho 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile`
3. 즉각 반영:` source ~/.bash_profile`
4. 폴더 생성: `mkdir {{폴더명}}`
5. 폴더 들어가기: `cd {{폴더명}}`
6. 파이썬 3.5.2버전 독립환경 설정: `pyenv virtualenv {{독립환경명}}`
7. 독립환경 실행: `pyenv activate {{독립환경명}}`

pip install django 가상환경 내부에 장고 설치



#### 2. project 생성

----

1. django-admin startproject {{프로젝트명}}
2. 프로젝트 명으로 만들어진 폴더 이름 src로 변경
3. python manage.py migrate



### 3. app 생성 (+ py파일 추가, static, html, 파일경로 세팅)

----

> “app은 프로젝트 mysite(만들고자 하는 웹) 내에서 어떤 기능을 하 는 ’기능적 단위’”
>
> Django DRY(Do not Repeat Yourself) Principle”
>
> - app은 잘 만들어 놓으면 다른 프로젝트에 여러 번 사용 가능 
> -  ex) 투표 기능 app, 로그인 기능 app, 게시판 기능 app 등.

1. ptrhon manage.py startapp {{app명}}
2. polls app에 urls.py추가
3. templates폴더 만들고 base.html 복사
4. static 폴더 복사
5. setting.py 파일 수정
   1. INSTALLED_APPS 리스트 안에 `'app명',` 넣기
   2. TEMPLATES 안 'DIRS' 리스트 안에` os.path.join(BASE_DIR, "templates")`
   3. 가장 하단에` STATICFILES_DIRS = [ os.path.join(BASE_DIR, "static") ] `추가



#### 4. 빅픽쳐 그리기 (view 기분으로 Page(GET) / Action(POST) 기준) 

----

e.g.

1. Question **Index** Page (GET) : 맨 처음 페이지 접속시 – 있는 질문들 보여줌 
2. Question **Detail** Page (GET) : 특정 질문을 클릭시 그 질문의 상세 내용을 보여줌 
3. Question **Result** Page (GET) : 특정 질문에 선택지를 골라 투표시, 해당 질문의 투표 내역을 결과로 보여줌
4. Vote Action (POST) : 특정 질문의 선택지를 골라 투표함 ( = 데이터베이스에 있는 votes 라는 변수 += 1 해서 저장하는 기능, 즉 POST 기능을 하겠네)



#### 5. 데이터 베이스 설정

##### 5-1) ERD(개체-관계 모델)그리기

----

![erd](..\img\erd.PNG)

- 1 to 1
- 1 to many (ForeingKey)
- ​
- 1 to many(ForeingKey( blank=True, null=True))



##### 5-2) 데이터베이스 설정

----

models.py에 model설계



##### 5-3) migrate하기

----

1. `$ python manage.py makemigrations polls` - 먼저 포장하자! (polls app안에 있는 models.py에 있 는 모델을 포장하기)
2. `$ python manage.py migrate`
   - 포장이 끝나면, DB(데이터베이스)로 보내자!(migrate)
3. **admins.py**에서 register한 후, admin page에서 확인해보기 – 다 잘 DB에 저장되었는지
   - createsuperuser


#### 6. 가짜 view정의(url-view)

----

{{project}}/urls.py

- import include 추가, urlpatterns 추가

````python
from django.conf.urls import url, include
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^앱명/', include('앱명.urls')),
] 
````



{{app}}/urls.py

- app_name 정의

````python
from django.conf.urls import url
from . import views

app_name = 'polls'
urlpatterns = [
    url(r'^$', views.IndexView, name='index'),
    url(r'^(?P<question_id>\d+)/$', views.DetailView, name='detail'),
    url(r'^(?P<question_id>\d+)/result/$', views.ResultView, name='result'),
    url(r'^(?P<question_id>\d+)/vote$', views.vote, name='vote'),
    url(r'^(?P<question_id>[0-9]+)/votedata/$', views.vote_data, name='vote_data'),
]
````



{{app}}/veiws.py

````python
from django.shortcuts import render
from django.http import HttpResponse

def IndexView(request):
    return HttpResponse('투표할 질문들을 보여주는 Index Page')

def DetailView(request, qustion_id):
     return HttpResponse('해당 질문의 제목, 그리고 선택지들을 보여주는 Detail Page')
    
def ResultView(request, question_id):
     return HttpResponse('해당 질문을 투표한 후, 결과를 보여주는 Result Page')
    
def vote(request, question_id):
     return HttpResponse('투표하기 기능을 실행')
````



=>python  manage.py runserver



#### 7. 진짜 기능을 하는 view정의(view-models-templates)

