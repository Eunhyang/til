## Adding additional data to **select option** Using jQuery

1. 발단

   ```python
   {% for vari_obj in object.variation_set.all %}
     <option data-price="vari_obj.price" value="{{ vari_obj.id }}">{{ vari_obj.title }}</option>
   {% endfor %}
   ```

   option tag에 data-price 필드가 들어감 



2. 공부

- jquery로 추가적인 data(value 값) 을 보내고 싶을 때 option attr로  `data-데이터명 = 값`으로 지정

