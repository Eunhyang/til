## 파일 업로드 경로 지정 함수

1. 발단

   product image를 저장하는데 `products/`경로에 자신의 `product.title/image_name`경로를 추가하고 싶음

   ````python
   image = models.ImageField(upload_to='products/')
   ````

   ​

2. 해결

   ````python
   from django.utils.text import slugify

   def image_upload_to(instance, filename):
   	title = instance.product.title
   	slug = slugify(title)
   	return "products/%s/%s" %(slug,filename)

   class ProductImage(models.Model):
   	product = models.ForeignKey(Product)
   	image = models.ImageField(upload_to=image_upload_to)#upload_to 경로를 image_upload_to함수의 return값으로 지정
   ````

   ​

3. 공부

   - slugify
     - ​

