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



5. 프론트 개발 시 tip
   - CSS
     - **<u>css 공부</u>**할 때는 다른 사이트 어떻게 적용(Chrome 개발자도구 이용해서)했는지 찾아보면서 공부하면 좋다
     - 요소내에 style속성 넣어서 적용하는 것(`<li style=""></li>`)보단 id속성에라도 <u>**css파일**에 넣어서 적용하는 것이 좋다</u>.
     - class 나 id 명은 '**기능-역할**' 이런식으로 예를들면) `tag-btn`
     - **<u>position 은 항상 지정</u>**해두는 편이 좋다. `position:relative`를 선호하신다. 
     - 나중에 유지보수를 염두에두고 코딩하는 편이 좋다
       - 코드도 잘 정리해두고, 주석도 좀 열심히..
     - em, px 등등 중 필요에 따라 사용하지만 굳이 이유가 없다면 px을 선호
     - **<u>CSS 우선순위</u>** -> id로 지정하는것이 제일 높고 `>` (e.g. `.menu > li`)등으로 특정 자식 엘리먼트를 지정하는 것이 빠름
       - 커스텀할 때는 `!important`써도 무방하고 안전
     - 유용한 사이트
       - 크로싱 브라우저 http://caniuse.com/
       - [**jQuery** Quick API Reference3.03.0](https://oscarotero.com/jquery/)
       - [그리드 짤 때 : Foundation Framework](http://foundation.zurb.com/)
   - javascript
     - **<u>바닐라(생 Javascript) 위주로 코딩</u>**하는 편이 좋다.
       - 프레임워크는 유행타니까 
       - 또 jQuery는 하나하나 요소를 검색해서 가져오므로 바닐라가 더 빠름
       - => script에서 최대한 html파일에 접근하지 않도록 짜는 것이 중요
     - class나 id를 어떻게 지정하느냐에 따라 javascript 짜는 방법이 달라짐
       - class로 그룹핑을 잘하면 더욱 효율적으로 코드를 짤 수도 있음
       - e.g. 똑같은 메소드를 적용시킬거라면 id보다 class로 한번에 모두 적용시키는게 효율적인 것 처럼
     - **개발자 도구** 사용 팁
       - getElementById와 같은 긴 메소드들 -> selecId등으로 자기가 임의로 지정하면 편하다.
       - 디버깅 할 때는 
         - 간단하게 변수 확인등 -> console.log로 출력
         - or window.z처럼 전역변수로 담아서 개발자도구에서 확인

6. input 태그 위에 icon 올리기

   - html

     ```html
       <div class="box">
           <span class="icon"><i class="fa fa-search"></i></span>
           <input type="search" id="search" placeholder="Search..." />
       </div>
     ```

   - css

     ```css
     .box {
       position:relative;
     }
     .icon {
       position:absolute;
       z-index:1;
     }
     ```

7. input submit 버튼을 font awesome 버튼 사용

   > css: input submit의 폰트를 FontAwesome으로 지정하고 input 박스의 value에 해당 아이콘 유니코드 지정

   - HTML

     - ```html
       <input type="submit" class="search" value="&#xf002;">
       ```

   - CSS

     - ```CSS
       .search{
         font-family:FontAwesome;
       }
       ```

       ​

8. CSS로 글자 자르기

   - 한 줄 단위로 글자 자르기
     - 요소의 너비를 가질 수 있게 변경
       - `display:block` or `display:inline-block; width:200px;` 
       - block이면 부모의 너비값 100%자동으로, inline-block은 너비값 지정
     - 줄바꿈 없애기 `white-space:nowrap;`
     - 넘치는 부분 감추기 `overflow:hidden`
     - 숨기는 부분 처리:밑줄임표(...) `text-overflow:ellipsis`

   - 여러 줄 단위

     - 줄바꿈 다시 설정 `white-space:nomal`

     - 줄 높이 필수! `line-height:1.2;`

     - 요소 높이 : 줄 높이 *(보여주고 싶은 줄 수) e.g. 3줄`height:3.6em`

     - 숨김 부분 처리 추가

       - ```css
         text-align:left;
         word-wrap:break-word;
         display:-webkit-box;
         -webkit-line-clamp:3;
         -webkit-box-orient:vertical;
         ```

       - `text-align:left;` 글자 정렬이 양쪽 정렬이면 말 줄임표가 숨겨질 수 잇으니 왼쪽 정렬로

       - `word-wrap:break-word;` 잘려버릴 글자를 단어 단위로

       - `display:-webkit-box;` 여백 삽입과 같이 유연한 높이 증가를 위해 플렉스 박스형태로 변환

       - `-webkit-line-clamp:3;` 보여줄 줄 갯수

       - `-webkit-box-orient:vertical;` flex박스의 방향 설정

9. div 안 img 가운데 정렬

   - ```css
     img {
       position:absolute;
       left:50%;
       margin-left:-50px; 
       /*이미지width의 반*/
       top:50%;
       margin-top:-60px;
       /*이미지height의 반*/
     }
     ```

     ​