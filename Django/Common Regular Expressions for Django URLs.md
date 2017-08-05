## Common Regular Expressions for Django URLs



#### Django URL patterns example

```python
from django.conf.urls import url, include
# Django 1.9 and Up (required in Django 1.10+)
# urls.py

from django.conf.urls import url, include
from appname.views import (
              AboutView,
              article_detail, 
              ContactView,
              home_view, 
              profile_detail,
              )


urlpatterns = [
    # Examples:
    url(r'^$', home_view, name='home'),
    url(r'^contact/$', ContactView.as_view(), name='contact'),
    url(r'^about/$', AboutView.as_view(), name='about'),
    url(r'^profile/(?P<username>[\w.@+-]+)/$', profile_detail, name='about'),
    url(r'^article/(?P<slug>[\w-]+)/$', article_detail, name='about'),
    url(r'^blog/', include("blog.urls")),
    url(r'^admin/', admin.site.urls),
]
```

