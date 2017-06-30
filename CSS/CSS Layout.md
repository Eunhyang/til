## CSS Layout

모든 HTML요소는 사각형 박스(box)형태를 취함

- border-radius : 실제 박스가 원형이 된 게 아니라 그렇게 보이는 것 뿐임

html 엘리먼트 두 가지 구분

- block element
  - 대표적 예) p, div
  - 내부 콘텐츠 길이와는 상관없이 수직으로 계속 쌓이는 형태
  - 블록 서식 문맥(block formatting context)에 속하는 박스
  - 각 블록 레벨 요소는 자식 박스 및 생선된 콘텐츠를 포함하는 주요 블록 레벨 박스(principal block-level box)를 생성하며 모든 위치 지정 스킴에 관련
  - 블록 컨테이너 박스는 인라인 레벨 박스와 블록 레벨 박스를 포함할 수 잇음
  - 블록 컨테이너면서 블록 레벨 박스 -> 블록 박스
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





---

tip?!

- 전통적인 잘못된 방법중 하나는 Table Layout을 이용하는 것 