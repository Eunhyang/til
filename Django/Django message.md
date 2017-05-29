## Django Message

[참고 사이트](https://simpleisbetterthancomplex.com/tips/2016/09/06/django-tip-14-messages-framework.html)

#### **Usage**

views.py:

````python
from django.contrib import messages

def message_func(request):
    ```
    messages.success(request, 'Your password was updated successfully!'
    
````

success or warning



**template:**

````html
{% if messages %}
  <ul class="messages">
    {% for message in messages %}
      <li class="{{ message.tags }}">{{ message }}</li>
    {% endfor %}
  </ul>
{% endif %}
````



나는 스크립트 사용:

````javascript
<script>
  {% if messages %}
    {% for message in messages %}
      alert('{{message}}');
    {% endfor %}
  {% endif %}
</script>
````

