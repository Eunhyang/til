## Django return

- redirect
- reverse
- redirect(reverse('password-set'))
- retrun HttpResponseRedirect(reverse('news-year-archive',args=(year,)))
- render
- render-to-response
- 등..



#### render()

`render(request, template_name, context=None, context_instance=_context_instance_undefined, content_type=None, status=None, current_app=_current_app_undefined, dirs=_dirs_undefined, using=None)`

=>템플릿과 컨텍스트를 합쳐서 HttpResponse 오브젝트를 리턴함

```python
from django.shortcuts import render

def my_view1(request):
    ctx = {}
    retrun render(request, 'myapp/index.html', ctx)
    
def my_view2(reqest):
    t = loader.get_template('myapp/index.html')
    ctx = {}
    return HttpResponse(t.render(ctx, request))
```

my_view1 = my_view2



#### reverse()

reverse(viewname, urlconf=None, args=None, kwargs=None, current_app=None)

```python
def myview(request):
	#url이 argument를 받는 경우
    return HttpResponseRedirect(reverse('arch-summary, args=[1945]'))

#kwargs를 쓰는 방법. 
reverse('admin:app_name', kwargs={'app_label':'auth'})
```



#### HttpResponse

`response = HttpResponse('response할 컨텐츠')`

- HTTP코드가 200(정상)이고 생성자로 전달된 컨텐츠를 포함한 HttpResponse 오브젝트를 만듬
- 보통 작은 response에서만 씀(ajax로 받은 데이터나, 작은 number 등)



##### HttpResponseRedirect

`HttpResponseRedirect('/')`

- HTTP코드가 302(Found/Moved temporarily)인  HttpResponse 오브젝트를 만듬
- 다른 페이지로 redirect할 때만 써야함(폼 POST전송 성공 이후)

