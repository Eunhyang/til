## pip명령어 정리

pip란?

> 파이썬으로 작성된 패키지(라이브러리)를 관리하는 프로그램
>
> 만약 사용하고자 하는 라이브러리가 다른 라이브러리를 의존하고 있다면, 한 가지 라이브러리만 설치해야만 정상적으로 기능을 사용할 수 있고, 또한 설치된 라이브러리의 버전을 관리하려면 주기적으로 라이브러리 배포 사이트를 확인해야하는 번거로움이 있음
>
> 이러한 복잡한 과정을 해결 해주는 프로그램



1. 패키지 검색 `pip search 키워드`
   - 존재하는 모든 패키지를 키워드로 검색
   - 설치된 라이브러리라면 installed와 함께 현재 설치된 버전이 표시됨
2. 패키지 설치 `pip install 패키지`
3. 패키지 삭제 `pip uninstll 패키지`
4. 패키지 업데이트 `pip install --upgrade 패키지`
5. 설치된 패키지 확인 `pip show 패키지`
6. 설치된 전체 패키지 확인 `pip list`
7. requirements.txt 설치 `pip install -r requirements.txt`
8. 설치된 패키지 전부 삭제 `pip freeze | xargs pip uninstall -y`
