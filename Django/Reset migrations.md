## Reset migrations

1.    migration file 전부 삭제 단,  ` __init.py__` 파일 빼고

   ```
   find . -path "*/migrations/*.py" -not -name "__init.py" -delete
   find . -path "*/migrations/*.pyc" -delete
   ```

2.  현재 db삭제 (db.sqlite3 삭제)

3. 다시 migrations 하고 db 생성

   ```
    python manage.py makemigrations
    python manage.py migrate
   ```