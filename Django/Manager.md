## Manager

1. 발단

ecommerce-2의 model.py

````python
class ProductManager(models.Manager):
	def get_queryset(self):
		return ProductQuerySet(self.model, using=self._db)

	def all(self, *args, **kwargs):
		return self.get_queryset().active()
````

````python
class Product(models.Model):
	title = models.CharField(max_length=120)
	...

	objects = ProductManager() #objects(기본매니저)를 ProductManger로 지정
````

- product가 active=T-> 화면에 보여짐 / active=F-> 화면에 출력X 하도록 만들어야 함
- => productManager사용



2. 공부

   - ````python
     def get_queryset(self):
         return ProductQuerySet(self.model, using=self._db)
     ````

     - queryset = object.all -> 특정 모델 클래스에 해당되는 모든 인스턴스들

   - ````python
     def all(self, *args, **kwargs):
     		return self.get_queryset().active()
     ````

     - queryset을 active상태로 