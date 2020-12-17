## 11-06 데이터베이스 서버-Oralce 데이터베이스

### [실습5] Oracle Database Express 11g 설치

실습목표
- Server에 리눅스용 Oracle Database Express 11g를 설치

오라클 다운로드 링크 -> [http://download.hanbit.co.kr/centos/8/oracle-xe-11.2.0-1.0.x86_64.rpm.zip](http://download.hanbit.co.kr/centos/8/oracle-xe-11.2.0-1.0.x86_64.rpm.zip)


```bash
# 1. 오라클 설치 전 작업
dnf -y install libnsl

# 2. 오라클 다운로드된 곳에 가 오라클 설치
$ cd 다운로드/
$ ls -l
$ unzip oracle*
$ cd Disk1/
$ ls -l
$ dnf -y install oracle*.rpm
# 3. 오라클 설정
$ service oracle-xe configure
# 포트 8080, 1521 기억해두기
# 시스템 비밀번호 1234 지정 enter x2, then enter

# 4. 서비스 설정
$ systemctl restart oracle-xe
$ systemctl enable oracle-xe
$ systemctl status oracle-xe

$ . /u01/app/oracle/product/11.2.0/xe/bin/oracle_env.sh  # 이 파일을 실행해야 함
$ gedit /etc/bashrc  # 컴퓨터를 실행할 때 자동으로 실행해주기
# 제일 밑에 추가하기
> . /u01/app/oracle/product/11.2.0/xe/bin/oracle_env.sh

# 5. 방화벽 포트 열기
$ firewall-cmd --permanent --add-port=8080/tcp
$ firewall-cmd --permanent --add-port=1521/tcp
$ firewall-cmd --reload
```

웹에서 오라클 서버 들어가기 -> 192.168.111.100:8080/apex
- Workspace -> internal
- Username ADMIN
- Password -> 1234

![11-06 실습 결과](./assets/11-06실습결과.png)

### [실습6] Oracle에서 쇼핑몰 DB 구축

실습목표
- 쇼핑몰 DB를 Oracle에서 구축
- SQL*Plus 사용법을 익힘

Server 터미널에서

```bash
$ mkdir /oradata
$ chmod 777 /oradata/
$ sqlplus  # oracle 들어가기
> system
> 1234
```

```SQL
CREATE TABLESPACE shopping_db DATAFILE '/oradata/shop.dbf' SIZE 5M;
SELECT tablespace_name FROM DBA_DATA_FILES;
CREATE TABLE customer ( id VARCHAR(10) NOT NULL PRIMARY KEY, name NCHAR(5), age INT, address NCHAR(5) ) TABLESPACE shopping_db;
CREATE TABLE purchase ( no INT NOT NULL PRIMARY KEY, cust_id VARCHAR(10), mdate CHAR(8), product NCHAR(5) ) TABLESPACE shopping_db;

DESC customer;
DESC purchase;

INSERT INTO customer VALUES ('hong', '홍길동', 22, '경기');
INSERT INTO customer VALUES ('dang', '당탕이', 23, '충북');
INSERT INTO customer VALUES ('ppuni', '이뿌니', 30, '서울');
INSERT INTO customer VALUES ('john', '존벤이', 28, '강원');

INSERT INTO purchase VALUES (1, 'hong', 20161227, 'TV');
INSERT INTO purchase VALUES (2, 'ppuni', 20160305, '냉장고');
INSERT INTO purchase VALUES (3, 'john', 20191217, '세탁기');
INSERT INTO purchase VALUES (4, 'hong', 20201217, '비디오');

SELECT * FROM customer;
SELECT * FROM purchase;
```

![11-06 실습 결과2](./assets/11-06실습결과2.png)
