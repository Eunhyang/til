## background 속성

#### 한꺼번에 지정

```css
body{
  background: green url('brabbit.png') no-repeat fixed 50% 50%/100% 100%;
}
```

- 필요한 속성만 써도 됨

- 순서는 사오간 없지만 background-size 속성을 쓸 경우 앞에 슬래시(/)를 그어 다른 속성과 구분해 줌

- 50% 50%/100% 100%는 background-positio 가로 50% 세로 50%위치에, 크기가 가로100% 세로 100%란 의미 

  ​

#### **속성값**

- background-repeat : 배경 이미지 패턴 지정

  - repeat 기본값
  - repeat-x 가로 반복
  - repeat-y 세로반복
  - no-repeat 반복되지 않음

  ```css
  body{background:repeat-x;}
  ```

  ​

- background-attachment : 배경 이미지 고정 방식

  - scroll 기본값
  - fixed, local

- background-position 배경 위치 지정

  - left right center (가로)
  - top center bottom (세로)
  - %, cm, px, em 등에서 선택

