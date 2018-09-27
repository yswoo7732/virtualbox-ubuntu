1. virtualbox를 이용하여 ubuntu설치
- https://www.virtualbox.org/wiki/Downloads
위의 홈페이지에서 각 os에 맞는 virtualbox를 다운로드한다.

2. 다운로드한 virtualbox를 실행한다.
- mac os에서는 설치가 안될 경우, 환경설정>보안 및 개인정보보호에서 맨 밑의 허용버튼 클릭후, 실행

3. ubuntu image 다운(iso file) 후, 저장소에 cd삽입하여 재실행
- https://www.ubuntu.com/download/server

4. apache를 이용한 웹서버 구축
- apache2 설치하기
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2

위의 명령어를 입력한 후, apache2 -v 및 localhost를 실행하면 /var/www/html/index.html이 실행

cf) ubuntu desktop이 아닌 server를 설치하여 포트포워딩을 이용하여, 맥os에서 웹서버가 잘 돌아가는지 확인
virtualbox의 설정의 네트워크>고급에서 포트포워딩

5. apache2.conf, site-availe/000-default.conf의 설정파일을 변경하여 원하는 directory root로 변경

6. php 설치
- php 패키지를 다운로드하기 위하여, 저장소를 추가
sudo add-apt-repository ppa:ondrej/php
- 추가한 저장소로부터 패키지 목록을 가져옴
sudo apt-get update

- 필요한 모듈설치
sudo apt-get install php
sudo apt-get install php7.2-mysql php7.2-curl php7.2-xml php7.2-gd php7.2-mbstring

- 추가적으로 설치하고싶은 모듈 확인
apt-cache search php-

cf) php7.2-mbstring에 대해서는 저장소에서 다국어모듈 패키지가 없음.
/etc/apt/sources.list에 다음을 추가한 후, 패키지 목록을 다시 가져온 후, 모듈 설치해야함.
deb http://archive.ubuntu.com/ubuntu bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main multiverse restricted universe