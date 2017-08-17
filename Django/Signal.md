## Signal

1. 발단

ecommerce-2의 model.py에서 

`post_save.connect(product_post_saved_receiver, sender=Product)` 사용



2. 공부

- post_save가 뭐냐?
  - django signal 에 속함 
    - django 프레임워크는 어떤 일을 수행할 때마다 알려줄 것을 설정하고, 그 때 지정한 동작(method)을 수행할 수 있게하는 신호(signal)를 발생시킬 수 있는 기능을 가지고 있다.
    - e.g. **post_save** signal을 이용해서 DB model에 관련해서 save가 작동하면, 저장이 완료된 이후에 지정한 동작을 수행