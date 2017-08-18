## Signal

1. 발단

ecommerce-2의 model.py에서 

```python
def product_post_saved_receiver(sender, instance, created, *args, **kwargs):
	print(sender)
	print(instance)
	print(created)


post_save.connect(product_post_saved_receiver, sender=Product)
```

=> 결과

![스크린샷 2017-08-17 오후 11.10.28](../img/스크린샷 2017-08-17 오후 11.10.28.png)

- `print(instance)` mp3로 나온이유는 `__str__`메소드에서 title로 지정해서

2. 공부

- post_save가 뭐냐?

  - django signal 에 속함 

    - django 프레임워크는 어떤 일을 수행할 때마다 알려줄 것을 설정하고, 그 때 지정한 동작(method)을 수행할 수 있게하는 신호(signal)를 발생시킬 수 있는 기능을 가지고 있다.
    - e.g. **post_save** signal을 이용해서 DB model에 관련해서 save가 작동하면, 저장이 완료된 이후에 지정한 동작을 수행

  - 다음 코드도 똑같이 동작(주석단부분!!)

    ```python
    from django.dispatch import receiver #receiver 사용하기위해

    @receiver( post_save, sender = Product ) #receiver 데코레이터 통해 post_save사용
    def product_post_saved_receiver(sender, instance, created, *args, **kwargs):
    	print(sender)
        ...
    ```

    ​