### filename 저장 패턴 만들기

```python
#filename을 slug-instance_id.확장명(jpg,png)
	basename, file_extension = filename.split(".")# file_extension에 확장명을 담음
	new_filename = "%s-%s.%s" %(slug, instance.id, file_extension)
	return "products/%s/%s" %(slug,new_filename)
```

