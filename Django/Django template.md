## Django template

- document의 표현을 분리하는데 사용되는 text 문자열

- MVC Framework에서 View와 비슷한 역할

- 개발가이드상 위치

  - 각 app폴더/templates폴더/app명폴더/.html파일
  - ?=> 복수의 app들이 동일한 이름의 template를 가진경우 혼동방지

  ​

#### 템플릿 언어

- 템플릿 변수 {{}}
- 템플릿 태그 {% %}
  - for
  - if and else
  - block 및 extends
    - 템플릿 상속
      - django의 템플릿 엔진에 있어 가장 강력하고 가장 복잡한 부분
      - title은 페이지마다 다르기 때문에 `<title>{% block title %}{% endblock %}</title>`
      - {% block content %} {% end content %}사이에 정보
- 템플릿 필터 {{ | }}
  - {{ createDate|date:"Y-m-d" }} 날짜 포맷 지정
  - {{ lastName|lower }} 소문자로 변경
- 코멘트 
  - {# 1라인 코멘트 #}
  - {% comment %}복수라인 문장{% endcomment %}