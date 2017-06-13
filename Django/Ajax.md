## Ajax

views.py

```python
from django.contrib.auth.models. import User
from django.http import JsonResponse

def validate_username(request):
    username = request.GET.get('username', None)
    data = {
      'is_taken' : User.objects.filter(username__exists())
    }
    if data['is_taken']:
        data['erro_message'] = 'Username이 이미 존재합니다.'
    return JsonResponse(data)
```



Javascript

```javascript
$.ajax({
  url: '{% url "validate_username" %}'
  ...
});
```

