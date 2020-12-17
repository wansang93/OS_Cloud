## 11-03 데이터베이스 서버-Windows에서 접속

### [실습2] Windows에서 MariaDB로 접속

실습목표
- MariaDB의 기본적인 보안을 설정, Windows에서 리눅스의 MariaDB 서버에 접속해 사용해 봄
- MariaDB의 보안에 대해 이해

```bash
# mysql 패스워드 설정
$ mysql -h localhost -u root -p  # 패스워드 없이 잘 들어가짐
$ mysqladmin -u root password '1234'  # 패스워드 설정
$ mysql -h localhost -u root -p  # 패스워드 입력
```

윈도우 클라이언트에서
마리아DB 클라이언트(10.5.8) 다운로드 링크 -> [https://downloads.mariadb.org/interstitial/mariadb-10.5.8/win32-packages/mariadb-10.5.8-win32.msi/from/https%3A//mirror.yongbok.net/mariadb/](https://downloads.mariadb.org/interstitial/mariadb-10.5.8/win32-packages/mariadb-10.5.8-win32.msi/from/https%3A//mirror.yongbok.net/mariadb/)

프로그램 설치 시 Client Programs 만 설치

파워쉘에서

```powershell
$ cd "c:\Program Files\MariaDB 10.5\bin"
$ dir mysql.exe
$ .\mysql  # 접속 불가, 자기 자신에 접속하려고 해서
$ .\mysql -h 192.168.111.100 -u root -p  # 접속 불가
# 사실 root 뒤에 @ 하고 local 호스트라고 적혀있다.(root@localhost)
```

서버 터미널에서

```bash
> GRANT ALL ON *.* TO winuser@'192.168.111.%' IDENTIFIED BY '4321';
# %는 모든 번호가 가능하다는 의미
```

다시 파워쉘에서

```powershell
$ .\mysql -h 192.168.111.100 -u winuser -p  # 4321 입력하면 접속 완료
```
