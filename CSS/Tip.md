#### Tip

1. 프로필 사진등 img 원형으로 만들 때

   .photo {

   ```css
   width: 100px; height: 100px;
   object-fit: cover;
   border-radius: 50%;
   ```
   }

2. ul li 블릿, 기호, 점 없애기

   `list-style:none;`

3. css 글자 길이 자르기

   - **전제** : `display:block`이어야함 or `display:inline-block`과 같이 콘텐츠에 따라 유동적인 너비를 가진다면 직접 요소의 너비를 설정해야 함. => 일정한 고정된 너비를 가져야 ****
   - **줄바꿈을 없애기**
     - 너비가 지정된 요소라도 글자수가 해당 너비를 넘어서게 되면 <u>자동으로 줄바꿈이 이루어짐</u>
     - => `white-space:nowrap`
   - **넘치는 부분을 감추기**
     - 넘치는 부분 처리 -> overflow 속성이 담당
     - => `overflow:hidden`
   - **숨긴 부분 처리**
     - 숨겨진 부분을 처리하는 방식은 text-overflow 속성이 담당
     - => `text-overflow:ellipsis` 밑줄임표(...) 생성

   ```css
   .target {
       display: inline-block;
       width: 200px;
       white-space: nowrap;
       overflow: hidden;
       text-overflow: ellipsis;
   }
   ```


4.div 동적으로 사이즈(width, height) 변환

```css
div{
  overflow:hidden;
  height:auto;
}
```

height를 auto로 잡아도 이미지등이 div박스 영역을 벗어나 제대로 영역을 확보하지 못하는 오류가 있음.

=> 이때 overflow를 설정하면 브라우저의 width 값 변경에 따른 불일치가 해결되어 자동으로 height영역이 컨텐츠 크기에 맞게 조절됨

- 내가 설정한 방법

  - 문제: 길이를 고정값으로 주었는데 안의 p 요소안 콘텐츠가 일정 길이를 넘을 경우 정렬이 뒤틀려짐

  - 해결방법 

  - ```css
    .comment{
         list-style:none;
         height: auto;
         border-bottom: 1px solid #eee;
         margin-bottom: 10px;
         overflow:hidden;
    }
    ```

    ​