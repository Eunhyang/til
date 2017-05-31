## JSON

> JSON(Javascript Object Notation)
>
> Javascript에서 객체를 만들 때 사용하는 표현식
>
> 사람도, 기계도 이해하기 쉬우면서 데이터의 용량이 작음

[JSON공식홈페이지]([http://www.json.org/json-ko.html](http://www.json.org/json-ko.html))

- JSON.parse()
  - 인자로 전달된 문자열을 자바스크립트의 데이터로 변환
- JSON.stringify()
  - 인자로 전달된 자바스크립트의 데이터를 문자열로 변환



#### 구조

````xml
{
	color: "red",
	value: "#f00"
}
````

key:"value"



#### Django & JSON

view.py

````python
def memo_data(request):
    memo_id = request.GET.get('memoId')
    memo = get_object_or_404(Memo, pk=memo_id)
    if request.method == "GET":
        memo_form = MemoForm(instance = memo)
        result = {
            'title': memo.title,
            'content':memo.content
        }
        result = json.dumps(result)

    return HttpResponse(result)
````

=> 웹브라우저 Console

````javascript
Object
	content: "헤헿dhkdn"
    title: "헤헤"
````

