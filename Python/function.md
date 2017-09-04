## 내장 함수

##### map

````python
def two_times(numberlist):
	result = []
    for number in numberlist:
      result.append(number*2)
    return result
  
result = twon_times([1, 2, 3, 4])
print(result)
````

-> 결과값:[2,4,6,8]



==**<u>map 함수</u>**== 이용

```python
>>> def two_times(x) : retrun x*2
>>> list(map(two_times,[1,2,3,4]))
[2, 4, 6, 8]
```



#### lambda

> 함수를 생성할 때 사용하는 예약어로 **def와 동일한 역할**
>
> 보통 함수를 한줄로 간결하게 만들 때 사용

```python
>>> sum = lambda a,b: a+b
>>> sum(3,4)
7
```

