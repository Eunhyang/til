## Django 환경설정

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

#### 환경설정

1. 새로운 폴더 생성 후 독립환경 설정

2. pip install --upgrade pip

3. pip install django

4. django-admin startproject {{프로젝트명}}

5. 프로젝트 명으로 만들어진 폴더 이름 src로 변경

6. python manage.py migrate

7. ptrhon manage.py startapp {{app명}}

8. templates폴더 만들고 base.html 복사

9. static 폴더 복사

10. setting.py 파일 수정

    1. INSTALLED_APPS 리스트 안에 `'app명',` 넣기
    2. TEMPLATES 안 'DIRS' 리스트 안에` os.path.join(BASE_DIR, "templates")`
    3. 가장 하단에` STATICFILES_DIRS = [ os.path.join(BASE_DIR, "static") ] `추가

11. Github에 프로젝트 올리기

    1. README.md 파일 만들고, git init 이후, git add . 로 전체 파일 추가하기

    2. .gitignore 파일 만들고, 아래 목록 각각 추가

       ````
       *.pyc
       __pycache__
       myvenv
       db.sqlite3
       .DS_Store
       ````

    3. git commit -m "first commit" 부터 남은 설정 진행 undefined