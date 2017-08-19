## *args **kargs



#### *args

> 함수에 **<u>임의 갯수의 argment</u>**를 넘겨주기 위해 사용

```python
def echo_args(*args):
    for arg in args:
    	print(arg)
```

-> 실행결과 

```
>>> echo_args(1,2,3)
1
2
3
>>> 
```



---



#### **kwargs

> *args와 차이점은 함수에 keyword argument를 넘겨줄 수 있음 -> 함수 내에서 **dictionary**로 엑세스

예제1

```python
def display_stuff(**kwargs):
    if kwargs is not None:
        print(kwargs)
```

-> 실행결과

```
>>> display_stuff(name='Jeff', passion='development', language='python')
{'passion': 'development', 'name': 'Jeff', 'language': 'python'}
>>>
```



예제2 : 키 'passion'의 값 출력

```python
def display_stuff(**kwargs):
	if kwargs is not None:
        print(kwargs['passion'])
```

-> 실행결과

```
>>> display_stuff(name='Jeff', passion='development', language='python')
development
>>>
```

