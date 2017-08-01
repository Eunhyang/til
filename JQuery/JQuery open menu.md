## JQuery 펼쳐지는 메뉴 구현

- 효과 없음

  - html

    ```html
    <div class="menu">메뉴</div>
    <ul class="hide">
      <li>메뉴1</li>
      <li>메뉴2</li>
      <li>메뉴3</li>
    </ul>
    ```

  - css

    ```css
    .hide {
      display:none;
    }
    ```

  - js

    ```javascript
    $('.menu').click(function(){
      $('ul').toggleClass('hide');
    });
    ```



- 슬라이드 효과

  - js

    ```javascript
    $('.menu').click(function(){
      var submenu = $('ul');
      
      if(submenu.is(":visible")){
       	submenu.slideUp();
      }else{
        submenu.slideDown();
      }
    })
    ```

    ​