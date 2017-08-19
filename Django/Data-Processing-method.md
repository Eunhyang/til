## Data Processing method

- distinct()
  - e.g. `qs = (qs | qs2).distict()`  -> 중복되는 값(row)을 제거한 queryset을 return
  - multiple table에서는 row값이 중복될 가능성이 있으므로 이러한 경우 사용
    - 위의 예시 경우 qs-> title과 description처리 qs2-> price를 처리하므로 multiple table을 처리하는 경우?]