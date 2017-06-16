## CSS Layout

html 엘리먼트 두 가지 구분

- block element
- inline level element



#### Position

- static 기본값
  - static이라고 지정된 엘리먼트는 위치가 지정된 것이 아님
  - static이 아닌 다른 값으로 지정된 엘리먼트에 대해 위치가 지정됐다고 표현
- relative
  - 별도의 프로퍼티를 지정하지 않는 이상 static과 동일하게 동작
  - 상대 위치가 지정된 엘리먼트에 top이나 right, bottom, left를 지정하면 기본 위치와 다르게 위치가 조정됨
  - 상대의 위치를 지정
- fixed
  - 스크롤되더라도 늘 같은 곳에 위치
  - 모바일 브라우저의 경우 지원이 불안정
- absolute
  - 가장 가까운 곳에 위치한 조상 엘리먼트에 상대적으로 위치가 지정됨
  - fixed와 비슷하게 동작
  - 조상 엘리먼트가 없으면 문서 본문(document)를 기준으로 삼고, 페이지 스크롤에 따라 움직임
  - 절대 위치가 지정