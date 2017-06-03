## Migration

#### DB Migration

- Django에서 모델 클래스를 생성한 후, 해당 모델에 상응하는 테이블을 데이터베이스에서 생성할 수 있다.
- python 모델 클래스의 수정(및 생성)을 DB에 적용하는 과정을 Migration이라 부름
- Django가 기본적으로 제공하는 ORM(Object - Relational Mapping) 서비스를 통해 진행된다.



- Django 모델 클래스로부터 테이블을 생성하기 위해서는 

  - Migration을 **준비**하는 과정
  - 이를 **적용**하는 과정으로 나뉨

- => 구체적으로 아래와 같은 절차

  1. settings.py 파일 안의 INSTALLED_APPS리스트에 (만약 이미 추가되지 않았다면) 해당 Django App을 추가

  2. 모델 클래스로부터 테이블 스키마를 생성 혹은 수정하기 위해 아래 명령을 실행 

     ```python
     $./manage.py makemigrations
     ```

     이 명령이 실행되면 해당 Django App안에 migrations라는 서브폴더를 만들고 테이블 생성 및 수정을 위한 파이썬 마이그레이션 파일들을 생성한다.

  3. 모델 클래스로부터 실제 DB에 테이블을 생성하거나 수정하기 위해 아래 명령을 실행

     ```python
     $./manage.py migrate	
     ```

     이는 실제 Migration을 DB에 적용하는 명령



#### DB 관리 Shell

```python
$./manage.py dbshell	
```

**dbshell**을 사용해 <u>생성된 테이블</u>과 <u>테이블의 컬럼 정보</u>, <u>테이블 내용</u>등을 확인할 수 있음

```python
$./manage.py dbshell
sqlite> .tables //테이블 리스트
sqlite> PRGMA table_info(테이블이름)
sqlite> select * from 테이블이름
```



#### DB 설정

- Django에서 사용하는 DB에 대한 정보는 settings.py파일에 설정되어 있음
- 기본적인 세팅 : DB 디폴트로 sqlite3/ 파일명은 /db.sqlite3

````python
DATABASES = {
  	'default' : {
      	'ENGINE' : 'django.db.backends.sqlite3',
        'NAME' : os.path.join(BASE_DIR, 'db.sqlite3')
  	}
}
````

- DATABASES에는 반드시 "dafault"가 설정되어 있어야 하고, 뒤에 다른 DB설정도 추가할 수 있음

- 지원하는 DB 엔진

  - django.db.backends.postgresql
  - django.db.backends.mysql
  - django.db.backends.sqlite3
  - django.db.backends.oracle

- DB설정은 각 DB엔진마다 서로 다른 옵션 지정 가능

  - 예) MySQL에 대한 연결정보를 담은 DB설정

    ```python
    DATABASES = {
      'default' : {
        'ENGINE' : 'django.db.backends.mysql',
        'NAME' : 'MyDB',
        'USER' : 'user1',
        'PASSWORD' : 'pwd',
        'HOST' : 'localhost',
        'PORT' : '3306',
      }
    }
    ```

    ​

