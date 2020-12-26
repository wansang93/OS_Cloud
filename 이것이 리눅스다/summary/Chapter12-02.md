## 12-02 웹 서버-워드프레스 활용

### [실습2] 워드프레스 설치 및 운영

실습목표
- 오픈 소스 웹사이트 통합 구성 도구인, 워드프레스를 설치하여 운영
- 간단한 웹 사이트를 만드는 방법을 익힘

서버 터미널에서

```bash
$ mysql
```

```sql
CREATE DATABASE wpDB;
GRANT ALL PRIVILEGES ON wpDB.* TO wpUser@localhost IDENTIFIED BY '1234';
exit
```

```bash
# wordpress 다운로드
$ wget https://ko.wordpress.org/wordpress-4.9.6-ko_KR.tar.gz
$ ls -l word*
$ tar xfz word*
# 홈페이지로 옮기기
$ mv wordpress /var/www/html
$ cd /var/www/html/
$ ls -l
$ chmod 707 wordpress/  # 외부에서 접근 가능하도록 하기
$ chown -R apache.apache wordpress/  # 소유주 바꾸기
# 설정하기
$ cd wordpress/
$ ls
# 샘플로 제공하는 것을 복사해 수정하기
$ cp wp-config-sample.php wp-config.php
$ gedit wp-config.php
> 23행(define): 'database_name_here' -> 'wpDB' 수정
> 26행(define): 'username_here' -> 'wpUser' 수정
> 29행(define): 'password here' -> '1234' 수정

# 웹 서버 설정파일 편집
$ vi /etc/httpd/conf/httpd.conf
> :set number
> 122행(Document): '/var/www/html/wordpress' 로 수정
> 134행(<Directory): '/var/www/html/wordpress' 로 수정
> 154행(Allow): 'None' -> 'All' 로 수정
> :wq
$ systemctl restart httpd
```

웹에서 -> `localhost` 로 들어가서 설정

사용자명: wpAdmin, 비밀번호: 1234, 이메일 아무거나 쓰고 설정 완료 후 로그인

워드프로세스 자체 사용법 익히기

테마 변경 -> WordPress.org 테마 -> 사용자 정의하기 -> 공개

웹 껏다 켜서 `192.168.111.100`으로 접속해 확인하고 win 클라이언트에서도 확인
