## ModelForm factory function

```
form = modelform_factory(model, form=form, fields=fields, exclude=exclude,
 formfield_callback=formfield_callback,widgets=widgets, localized_fields=localized_fields,labels=labels, help_texts=help_texts,error_messages=error_messages, field_classes=field_classes)
 ````

1. modelform 쉽게 만들기 위해 사용
   - 커스터마이징 거의 필요 없을 때
   - class 지정하지 않고 method로 만듬

```python
>>> from django.forms import modelform_factory
>>> from myapp.models import Book
>>> BookForm = modelform_factory(Book, fields=("author", "title"))
```



2. 이미 존재하는 form을 수정하기 쉽도록 사용
   - 예를 들면, widget을 구체적으로 명시화하기 위해

```python
>>> from django.forms import Textarea
>>> Form = modelform_factory(Book, form=BookForm,
...                          widgets={"title": Textarea()})
```



- modelForm의 field들 사용 가능
