## Django Q objects

1. 발단

   product **search** 기능 만들어야함 

2. 공부 

   - Q object

     -> 데이터베이스 관련한 Python object들에서 SQL문을 캡슐화(결국 query문을 쉽게 날릴 수 있다.)

     - Q class 코드

       ```python
       class Q(tree.Node):
           AND = 'AND'
           OR = 'OR'
           default = AND

           def __init__(self, *args, **kwargs):
               super(Q, self).__init__(children=list(args) + list(six.iteritems(kwargs)))

           def _combine(self, other, conn):
               if not isinstance(other, Q):
                   raise TypeError(other)
               obj = type(self)()
               obj.connector = conn
               obj.add(self, conn)
               obj.add(other, conn)
               return obj

           def __or__(self, other):
               return self._combine(other, self.OR)

           def __and__(self, other):
               return self._combine(other, self.AND)

           def __invert__(self):
               obj = type(self)()
               obj.add(self, self.AND)
               obj.negate()
               return obj
       ```

       ​

   - models.py 에 Q import

     ```python
     from django.db.models import Q
     ```

   - e.g. 'who'나 'what' 을 포함한 문장 찾기

      ```python
     Q(question__startswith='Who') | Q(question__startswith='What')
      ```

     ​