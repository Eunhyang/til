## Function



- clear()

  **관계된** object set에서 모든 object제거 

  ```python
  b = Blog.objects.get(id=1)
  b.entry_set.clear()
  ```

  - remove(), clear()은 Foreingkey(null = Trye)일 때 가능
  - ​