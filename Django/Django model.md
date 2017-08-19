## Django 모델



#### Django Model

- 각각의 모델은 파이썬 클래스로 표현되며 django.models.Model클래스의 서브클래서
- 장고 내장 ORM
  - ORM의 역할 : SQL을 직접 작성하지 않고도 장고 모델을 통해 데이터베이스로 접근한다. (조회/추가/수정/삭제)
  - !!! SQL을 몰라도 된다는 것이 아님 -> 최소한 내가 작성한 코드가 어떤 SQL을 만들어내는지 검증할 수 있어야함
- 하나의 장고 프로젝트 — 하나의 DB 사용
- 파이썬 클래스와 데이터베이스 테이블을 매핑
  - Model 클래스 : DB 테이블과 매핑
  - -> Model Instance : DB테이블의 1 row
- **QuerySet**?
  - 전달받은 객체의 목록
  - 데이터베이스로부터 데이터를 읽고 **<u>필터</u>**를 걸거나 **<u>정렬</u>**할 수 있음

#### SQL(Structured Query Language)

- Qurey: 정보수집에 대한 요청에 쓰이는 컴퓨터 언어
- SQL: 관계형 데이터베이스 시스템의 데이터를 관리하기 위해 설계된 특수목적의 프로그래밍 언어
- RDBMS의 종류 :  MySQL, MariaDB...
- 장고모델은 관계영 데이터 베이스(RDBMS)만을 지원
- 장고 모델을 통해 SQL을 생성/실행(ORM)



#### Field Option

> 필드마다 고유 옵션이 존재하며 공통 적용 옵션도 존재

- null(DB 옵션) : DB필드에 NULL허용 여부(default값: False)
- unique(DB 옵션) : 유일성 여부 (default값 : False)
- blank : 입력값 유효성(validation) 검사시 empty 값 허용 여부 (default값 : False)
- default
- verbose_name
- validators



#### Method

- `get_absolute_url` : 모델의 개별 데이터에 접근하는 URL을 문자열로 반환

  models.py

  ```python
  def get_absolute_url(self):
  return reverse('cast:congressman_detail', args=[self.pk])
  ```

  사용 예) url -> `congressman_detail/10` : 10번 국회의원




#### Meta options

```python
from django.db import models

class Ox(models.Model)
 horn_length = models.IntegerField()
  
 class_Meta:
        ordering = ['horn_length']
        verbose_name_plural = "oxen"
```

- 필드 단위의 옵션들과 달리 **<u>모델 단위의 옵션</u>**
  - 예) 정렬 옵션(ordering), 데이터베이스 테이블 이름(db_table), 읽기 좋은 이름이나 복수(plural)이름을 지정할 수 있음(verbose_name, verbose_name_plural)


#### ModelForm.save(commit=False)

- Model Form 클래스는` .save(self, commit=True)` 메소드로 구현되어 있음

- `commit=False` =>commit False flag(DB저장 여부 결정)를 통해 함수 호출을 지연함

- e.g. f`orm.save(commit=False)`를 통해 DB 저장을 지연시켜 중복 저장을 방지

- e.g.2 

  ```python
  #ecommerce-2 models.py VariationListView(ListView)

  def post(self, request ,*args, **kwargs):
  formset = VariationInventoryFormSet(request.POST, request.FILES)
  		print(request.POST)
  		if formset.is_valid():
  			formset.save(commit=False) #formset의 form 중 중복 DB save 방지
  			for form in formset:
  				form.save()
  				return redirect
  		raise Http404
  ```

  ​


참고

- [[Django\] 모델 - 1. Model Syntax](http://nukggul.tistory.com/17)
- [Django 모델, 모델필드, 필드옵션] (https://wayhome25.github.io/django/2017/03/20/django-ep5-model/)