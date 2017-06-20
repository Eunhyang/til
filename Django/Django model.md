## Django 모델

- 각각의 모델은 파이썬 클래스로 표현되며 django.models.Model클래스의 서브클래서

#### Method

- `get_absolute_url` : 모델의 개별 데이터에 접근하는 URL을 문자열로 반환

  models.py

  ```python
  def get_absolute_url(self):
  return reverse('cast:congressman_detail', args=[self.pk])
  ```

  사용 예) url -> `congressman_detail/10` : 10번 국회의원

