## Conflict

#### 충돌 일어났을 때 메시지

```
Auto-merging piggyback/cast/templates/cast/contents_detail.html
CONFLICT (content): Merge conflict in piggyback/cast/templates/cast/contents_detail.html
Automatic merge failed; fix conflicts and then commit the result.
```

#### git status로 충돌 일어난 파일 확인 : both modified 부분

````
Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   cast/templates/cast/contents_detail.html
````

=> 충돌이 발생한 부분 수정

- `<<<<<<<HEAD` 부터 `=========` 사이의 구간: 현재 체크 아웃된 파일의 내용 (현재 내코드)
- `=========` 부터 `>>>>>>>브랜치네임` 사이의 구간이 병합 대상 브랜치 코드 내용