***pyenv*** : "Simple Python Version Management", 로컬에 다양한 파이썬 버전을 설치하고 사용할 수 있도록 한다. `pyenv`를 사용함으로써 파이썬 버전에 대한 의존성을 해결할 수 있다.

***virtualenv*** : “Virtual Python Environment builder”, 로컬에 다양한 파이썬 환경을 구축하고 사용할 수 있도록 한다. 일반적으로 `Python Packages`라고 부르는 ( `pip install`을 통해서 설치하는 ) 패키지들에 대한 의존성을 해결할 수 있다.

***autoenv*** : 만약 `pyenv`와 `virtualenv`를 통해서 의존성을 해결한다고 하더라도 작업할때마다 설정해주는 것은 귀찮은 작업이다. 특정 프로젝트 폴더로 들어가면 자동으로 개발 환경을 설정해주는 `autoenv`라는 스크립트를 활용하자. 