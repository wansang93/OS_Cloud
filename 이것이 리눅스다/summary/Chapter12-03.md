## 12-03 웹 서버-클라우드 서비스 활용

### 클라우드 서비스 구축

AWS, Azure, Google Drive 등의 서비스를 의미, 웹 하드 기능까지 포함

### [실습3] 클라우드 서비스 설치 및 운영

실습목표
- 클라우드 오픈소스인 ownCloud 커뮤니티 에디션을 설치 운영
- 리눅스, Windows, 스마트폰에서 접속해 사용

서버 초기화 후 터미널에서

```bash
$ dnf -y install httpd mariadb-server php php-mysqlnd php-gd php-mbstring php-pecl-zip php-xml php-json php-intl
$ systemctl restart mariadb
$ systemctl enable mariadb
$ mysql
```

```sql
GRANT ALL ON webDB.* TO webUser@localhost IDENTIFIED BY '1234';
exit
```

```bash
$ firewall-cmd --permanent --add-service=http
$ firewall-cmd --permanent --add-service=https
$ firewall-cmd --reload
$ cd /var/www/html/
$ pwd
$ wget http://download.hanbit.co.kr/centos/8/owncloud-10.3.1.zip  # 10.3.1 다운로드
$ unzip -q owncloud-10.3.1.zip
# 웹 서버 설정
$ mkdir owncloud/data
$ chown -R apache.apache owncloud  # apache 사용자, 그룹에 소유 넘기기
$ chmod -R 755 owncloud
$ systemctl restart httpd
$ systemctl enable httpd
```

윈도우 클라이언트에서

`192.168.111.100/owncloud/index.php` 들어가기

admin, 1234로 계정 생성, 데이터베이스: MySQL/MariaDB, 입력 정보들: webUser, 1234, webDB, localhost로 설정하고 설치 완료

오른쪽 admin으로 가서 사용자, 일반 사용자 계정 관리

사용자 만들기 thisUser, this@hanbit.co.kr, Users 그룹 만들고 그룹 설정, 만들기, 할당량 제한 가능

다시 웹 켜기 -> `192.168.111.100/owncloud` -> 로그인 하기

owncloud-client(2.7.4) 32bit 다운로드 링크 -> [https://download.owncloud.com/desktop/ownCloud/stable/2.7/win/ownCloud-2.7.4.2934.x86.msi](https://download.owncloud.com/desktop/ownCloud/stable/2.7/win/ownCloud-2.7.4.2934.x86.msi)

기본값으로 설정 후 저장, 재부팅 후 owncloud 실행

서버 주소 `http://192.168.111.100/owncloud/` 설정 다음 -> thisUser, 1234로 로그인 후 폴더 설정하기 -> 연결

동기화 후 ownclound 폴더 열고 확인

리눅스 클라이언트 터미널에서

```bash
$ su
$ cd /etc/yum.repos.d/
# 다운로드
$ wget https://download.opensuse.org/repositories/isv:ownCloud:desktop/CentOS_8/isv:ownCloud:desktop.repo
$ ls -l
$ dnf -y install owncloud-client
$ exit
$ owncloud &
```

서버 주소 `http://192.168.111.100/owncloud/` 설정 다음 -> thisUser, 1234로 로그인 후 폴더 설정하기 -> 연결

파일 -> onwcloud로 안에 파일들 확인

![12-03 실습 결과](./assets/12-03실습결과.png)
