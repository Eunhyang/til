#### 리눅스 파일 시스템 구조(채워가는 중)

* 전제적으로 역 트리 구조
* `/` 루트
  * 최상위 디렉토리 
* `/bin`
  * 기본적인 명령어가 저장된 디렉토리
  * ex) `mv` `cp` `rm`
  * root사용자와 일반사용자가 함께 사용할 수 있는 명령어 디렉토리
* `/boot` 
  * 리눅스 Boot Loader가 존재
* `dev`
  * system device 파일들을 저장
  * ex) 하드디스크 장치파일 (`/dev/sda`) 
* `/etc`
  * 시스템의 거의 모든 설정 파일들이 존재
  * ex) 시스템 제어판용 설정파일 `/etc/sysconfig`
* `/usr/bin`
  * 일반 사용자들이 사용가능한 명령어 파일들이 존재하는 디렉토리
  * ex) `/usr/bin/python` python명령어를 입력하면 여기 파일이 실행됨
  * python 명령어에 python3.6을  link해줄경우 
    * `rm -rf /urs/bin/python` 하고 `ln -s /usr/bin/python3.6 /usr/bin/python` 

* `/usr/local`
  * MySQL, Apache, PHP 또는 python package와 같은 어플리케이션들을 소스로 컨파일할 때 사용되는 장소