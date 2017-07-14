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
  - static이라고 지정된 엘리먼트는 위치가 지정된 것이 아님(offset 값이 적용되지 않음 e.g. left:100px 을 줘도 적용되지 않음)
  - static이 아닌 다른 값으로 지정된 엘리먼트에 대해 위치가 지정됐다고 표현
- relative
  - 별도의 프로퍼티를 지정하지 않는 이상 static과 동일하게 동작
  - 상대 위치가 지정된 엘리먼트에 top이나 right, bottom, left를 지정하면 기본 위치와 다르게 위치가 조정됨
    - e.g. left:100px : 부모 요소로부터 왼쪽으로 100px
  - 상대의 위치를 지정
- fixed
  - 스크롤되더라도 늘 같은 곳에 위치
  - 모바일 브라우저의 경우 지원이 불안정
- absolute
  - 기본값: 가장 가까운 곳에 위치한 조상 엘리먼트에 상대적으로 위치가 지정됨
  - offset값을 주면 html을 기준으로 위치 적용
  - fixed와 비슷하게 동작
  - 조상 엘리먼트가 없으면 문서 본문(document)를 기준으로 삼고, 페이지 스크롤에 따라 움직임
  - 절대 위치가 지정


#### Display

- table 속성

  - table:

    table-caption: 테이블 캡션으로 표시됨

    table-cell: 테이블의 셀 영역을 표시

    table-column: 테이블의 열 영역을 표시

    table-column-group: 테이블의 열 그룹 영역 표시

    table-row: 테이블의 행 영역을 표시

    table-row-group: 테이블의 행 그룹 영역 표시

    table-header-group: 테이블의 머리글 행 그룹 표시

    table-footer-group: 테이블의 바닥글 행 그룹 표시

---

tip?!

- 전통적인 잘못된 방법중 하나는 Table Layout을 이용하는 것 
- <a> <button> <input> 용도에 맞게 사용하기
  - <a>태그를 사용하며 href의 값으로 아무 의미없는 "#"을 사용하여 onclick과 같은 방식을 쓰는 것은 <a>...</a>요소를 본래의 의미(자원의 참조)와 다르게 사용했다는 것을 반증.
  - 다른 자원을 참조하는 의미 없는 버튼이나 텍스트가 키보드 포커스를 받아야 한다면 <button>을 사용하자