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





