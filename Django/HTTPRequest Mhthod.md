## HTTPRequest Mhthod

- ```
  Httprequest.build_absolute_url
  ```

  - -> 쇼핑몰 상품 공유 버튼에서 사용

    ```html
    ><a href="https://www.facebook.com/sharer/sharer.php?u={{request.build_absolute_uri}}">
    페이스북 공유</a>
    ```

    - request요청받은 위치의 absolute uri form 반환