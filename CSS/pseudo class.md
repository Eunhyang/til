## pseudo class

- `:before`

  요소의 앞의 내용을 생성

  - html

    ```html
    <ul>
      <li class="sale">아메리카노</li>
      <li>에스프레소</li>
      <li class="sale">카푸치노</li>
    </ul>
    ```

  - css

    ```css
    ul li.sale:before{
      content:"SALE!\A할인";
      display:inline-block;
    }
    ```

    ​

- `:after`

  요소의 뒤의 내용을 생성

  => li요소의 border-bottom 길이를 82%만 적용하기 위해 사용

  - html

    ```html
    <ul>
      <li class="comment"></li>
    </ul>
    ```

  - css

    ```css
    li.comment:after {
        content:""; 
        background: #eee; 
        position: absolute; 
        bottom: 0;
        right: 0;
        height: 1px; 
        width: 82%;
    }
    ```

    ​