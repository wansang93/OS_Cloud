## 11-02 데이터베이스 서버-MariaDB 설치

### [실습1] MariaDB 운영

실습목표
- Server 가상머신을 DBMS 전용 서버로 운영
- MariaDB 최신 버전을 별로로 다운해 설치

서버A 초기화 이후 인터넷에서 마리아(10.4.10) 다운로드

파일 4개 다운로드 링크 ->
- MariaDB/Galera [http://dw.hanbit.co.kr/centos/8/galera-4-26.4.3-1.rhel8.0.el8.x86_64.rpm](http://dw.hanbit.co.kr/centos/8/galera-4-26.4.3-1.rhel8.0.el8.x86_64.rpm)
- MariaDB/client [http://dw.hanbit.co.kr/centos/8/MariaDB-client-10.4.10-1.el8.x86_64.rpm](http://dw.hanbit.co.kr/centos/8/MariaDB-client-10.4.10-1.el8.x86_64.rpm)
- MariaDB/common [http://dw.hanbit.co.kr/centos/8/MariaDB-common-10.4.10-1.el8.x86_64.rpm](http://dw.hanbit.co.kr/centos/8/MariaDB-common-10.4.10-1.el8.x86_64.rpm)
- MariaDB/server [http://dw.hanbit.co.kr/centos/8/MariaDB-server-10.4.10-1.el8.x86_64.rpm](http://dw.hanbit.co.kr/centos/8/MariaDB-server-10.4.10-1.el8.x86_64.rpm)

다운로드 후 터미널에서

```bash
$ cd 다운로드/
$ ls -l
$ dnf -y install ga*.rpm
$ dnf -y install Maria*.rpm
$ systemctl restart mariadb
$ systemctl enable mariadb
$ systemctl status mariadb
$ firewall-config  # 영구적으로 mysql 포트 열어주기
$ mysql  # 잘 동작하는지 확인
> exit  # Bye 메시지 출력
```
