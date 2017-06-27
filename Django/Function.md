## Function



- clear()

  **<u>관계된</u>** object set에서 모든 object제거 

  ```python
  b = Blog.objects.get(id=1)
  b.entry_set.clear()
  ```

  - remove(), clear()은 Foreingkey(null = Trye)일 때 가능
  - remove()는 관계를 삭제 object를 삭제하지 않음ㅉ