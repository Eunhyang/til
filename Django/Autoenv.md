#### Autoenv

참고 : [맥에서의 파이썬 개발 환경 자동화](http://guswnsxodlf.github.io/pyenv-virtualenv-autoenv)

- 설치

  `$brew install autoenv`

- .bash_profile에 설정

  - `~/open .bash_profile`
  - 입력: `source $(brew --prefix dautoenv)/activate.sh`

autoenv는 터미널에서 티렉토리에 접근할 때, `.env`파일을 찾아 그 내용을 실행시켜주는 간단한 기능

e.g. Piggies폴더에 들어가면 piggies 가상환경 실행

- `vim .env` 실행
- 입력: `pyenv shell piggies`
  - => vim 저장 후 닫기 `:wq`
- 제일 먼저 디렉토리 들어가면, `.env`내용을 실행할 것인지 물어봄 -> y입력
