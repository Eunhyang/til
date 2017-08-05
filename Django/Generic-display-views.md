## Generic Display Views

- Detail View

  - => method로 구현시

    -  views.py

  - => Class 로 구현

    - views.py

      ```python
      from django.views.generic.detail import DetailView
      from .models import Product

      class ProductDetailView(DetailView):
      	model = Product
      	#template_name = "<appname>/<modelname>_detail.html"
          #template_name 직접 정하고 싶은경우
          #=> template_name = '아무거나.html'
      ```

    - urls.py

      ````python
      url(r'^(?P<pk>\d+)/$', ProductDetailView.as_view(), name='product_detail'),
      ````

      ​