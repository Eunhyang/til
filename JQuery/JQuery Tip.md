## JQuery Tip

- 퍼포먼스 향상 tip (참고: [jQuery 퍼포먼스 향상을 위한 Tips And Tricks](http://codefactory.kr/2011/12/07/jquery-performance-tips-and-tricks/))
  - 최신 버전의 jQuery 사용
  - 셀렉터 사용
    - ID & Element 셀렉터가 가장 빠름
      - `$('#Element, form, inpput')`
      - 내부적으로 브라우저 내장 메서드인 getElementById(), getElementTagName()를 사용하기 때문에 가장 빠름
    - Class 셀렉터는 느림
  - 꼭 필요한 경우가 아니라면 jQuery 사용하지 않기
    - $()를 한번 수행할 때마다 시간 소요 -> 바닐라 사용하기, 섞어써도 아무 문제없음