## CSS Layer 화면 중앙정렬 방법

> 참고 사이트
>
> [Layer 화면 중앙정렬 방법](http://nuli.navercorp.com/sharing/blog/post/1132794)

1. `position : absolute` +`margin: <마이너스값>`

   > 장점 : ie7이상 브라우저 지원
   >
   > 단점: width와 height값 고정 상태에서만 사용 가능

   - html

   ```html
   <div class="layer">
     Layer Contents
   </div>
   ```

   - css

     ```css
     .layer {
       postion:absolute;
       top:50%;
       left:50%;
       width:100px;
       margin: -50px 0 0 -50px;
     }
     ```

2. `position: absolute` 와 `display: inline-block`

   > 장점 : ie7이상 브라우저 지원 + layer 안의 content 영역이 가변적이어도 자동으로 중앙정렬
   >
   > 단점: 불필요한 span 태그

   - html

   ```html
   <div class="layer">
     <span class="content">Layer Contents</span>
     <span class="blank"></span>
   </div>
   ```

   - css

     ```css
     .layer{
       position: absolute;
       top:0;
       left:0;
       width:100%;
       height:100%;
       text-align: center;
     }
     .layer .content {
       display:inline-block;
       vertical-align:middle;
     }
     .layer .blanck{
       display:inline-block;
       width:0;
       height:100%
       vertical-align:middle;
     }
     ```

3. `position:absolute`  + `display:table-cell`

   > 장점: ie8이상 지원 + content값이 가변적이어도 자동 중앙정렬
   >
   > 단점: 코드 중첩이 여러번 되어야함

   - html

   ```html
   <div class="layer">
     <div class="layer_inner">
       <div class="content">
         Layer Contents
       </div>
     </div>
   </div>
   ```

   - css

   ``` css
   .layer {
     position:absolute;
     display:table;
     top:0;
     left:0;
     width:100%;
     height:100%;
   }
   .layer .layer_inner {
     display:table-cell;
     text-align:center;
     verticle-align:middle;
   }
   .layer .content {
     display:inline-block;
   }
   ```

   ​

4. `position:absolute` + `display:flex`

   - html

   ```html
   <div class="layer">
     <span class="content">Layer Contents</span>
   </div>
   ```

   - css

   ```css
   .layer {
     position:absolute;
     top:0;right:0;bottom:0;left:0;
     display:flex;
     align-items:center;
     justify-content:center;

     display:-webkit-flex;
     -webkit-align-item;center;
     -webkit-justify-content:center;
   }
   ```




- `position:absolute` + `right:50;margin-right:-(width의 1/2)px` 일때
  - position이 absolute 이기때문에 하위 엘리먼트들은 absolute 엘리먼트를 무시하고 normal-flow를 따르게됨 (엘리먼트들이 겹치는 현상 발생)
  - => absolute를 감싸는 부모 엘리먼트가 `position:relative`여야 하며 해당 엘리먼트의 높이값과 넓이값을 가져야함
    - absolute의 상대적위치는 static이 아닌 부모위치로 결정
    - 하위 absolute엘리먼트의 크기값을 감싸줘야함
    - *absolute 는 기본적 z-index가 1임
