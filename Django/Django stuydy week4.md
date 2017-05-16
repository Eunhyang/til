## Django stuydy week4

#### 다대다 관계

e.g. 포스트와 태그, 지하철 노선과 역

[sqlite : db관계를 gui형식으로 보여줌](http://sqlitebrowser.org/)

ManyToManyField 

- 어떤 column으로 연결되어야 할지도 정해줄 수 있음
- 두 개의 테이블을 id로 묶은 테이블이 향성됨
- `tag_set = models.ManyToManyField('Tag')` 
  - tag를 문자열로 찾는 이유 => tag class가 정의되어있지 않기 때문. 
  - 순환참조에러가 나는 경우가 있으므로 처음부터 string으로 써주는 게 권장됨

Through Field 

- 두 모델간의 관계가 추가적인 데이터를 가지는 경우 
- 1. m2m 필드 지정할 떄, through 속성을 명시
  2. 중간 모델을 foreingKey로 연결

#### model 정의 유용한 기능

- `__gt=date(1961,1,1))` : `__lt`,`__lte` ,`__gte`
- `__icontains` : ignore약자 -> B와 b포함 검색
- __ : lookup 메소드



#### Ajax

- 작동과정
  - ​