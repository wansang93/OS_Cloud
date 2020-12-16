## 10-04 메일 서버-웹 메일 구축

### 웹 메일의 설치 및 사용

이전까지의 실습은 예전의 방식이고 요즘은 웹 메일의 개념으로 메일을 사용함 

- 웹 메일: 웹 브라우저에서 메일을 사용
- 라운드 큐브는 PHP로 작성, Sendmail 및 IMAP 서버(Dovecot)를 기반으로 하는 웹 메일 프로그램
- 아파치 웹 서버(httpd) 및 PHP가 설치되어야 함

### [실습3] 라운드 큐브 메일 설치

실습목표
- naver.com 메일 서버에 라운드 큐브(Roundcube)를 설치, 운영

실무에서 메일 서버를 구축하면 웹메일도 구축합니다.

1. 터미널에서 라운트큐브 설치 및 기본 설정
    
    ```bash
    # 라운드 큐브는 CentOS8 에서 제공x
    # 현재 메일 서버가 APM 웹 서버가 되어야 라운트 큐브가 가능
    # 따라서 다음 파일들을 다운로드해서 APM 웹 서버로 구현
    $ dnf -y install httpd mariadb-server php php-mysqlnd php-gd php-mbstring php-pecl-zip php-xml php-json php-intl
    $ systemctl restart httpd
    $ systemctl restart mariadb
    $ systemctl enable httpd
    $ systemctl enable mariadb

    # 라운트 큐브(1.3.10) 다운로드
    $ wget https://github.com/roundcube/roundcubemail/releases/download/1.3.10/roundcubemail-1.3.10-complete.tar.gz
    $ ls -l
    $ tar xfz roundcubemail-1.3.10-complete.tar.gz
    $ mv roundcubemail-1.3.10 roundcube
    $ mv roundcube /var/www/html/
    $ cd /var/www/html/
    $ ls -l

    # 외부에서도 사용이 가능해야돼 권한 변경
    $ chmod 777 roundcube/temp/
    $ chmod 777 roundcube/logs/

    $ mysql
    # email DB 만들기
    > CREATE DATABASE emailDB;
    # email 사용자 만들기
    > GRANT ALL ON emailDB.* TO 'emailAdmin'@'localhost' IDENTIFIED BY '1234';
    # 적용
    > FLUSH PRIVILEGES;
    > exit
    ```

2. 라운트 큐브 웹에서 기본 설정

    웹에서 mail.naver.com/roundcube/installer 들어가기(웹 메일 설정하기)

    - 제일 아래로 내려서 `NEXT`
    - product_name -> This is Linux
    - Database setup -> 디비 서버: `naver`, 디비이름: `emailDB`, 아이디: `emailAdmin`, 비번: `1234`
    - 제일 아래 `CREATE CONFIG`
    - `Download` -> `Save` 하기

3. 기본 설정값 파일 옮기기

    ```bash
    $ mv /root/다운로드/config.inc.php /var/www/html/roundcube/config/
    $ chmod 707 /var/www/html/roundcube/config/config.inc.php
    ```

4. 웹으로 돌아가서 더 설정하기

   - 약간만 내려서 `CONTINUE` 하고 DSN OK를 확인
   - `Initialize database` 클릭(데이터베이스 설정 완료)
   - Sender: `lee@naver.com`
   - Recipient: `lee@naver.com`
   - `Test` 버튼으로 확인
   - Username: `lee`, pw: `lee`로 설정 후 `Check login` 클릭
5. 웹서버에서 첨부파일 크기 조절하기

    ```bash
    $ vi /etc/php.ini
    :set nu
    383행(max_execution): 30 -> 300 으로 변경
    672행(post_max_size): 500M 로 변경
    825행(upload_max_filesize): 500M 로 변경
    :wq

    $ reboot
    # 재부팅 후
    $ cp /boot/vmlinuz-4.18~ file1
    $ ls -l
    ```

6. 웹으로 가서 첨부해서 보내보기

    mail.naver.com/roundcube/ 들어가서 로그인 후 
    `Settings` -> `Identities` -> Email을 lee@naver.com으로 바꾸기
    보내보기

![10-04 실습 결과](./assets/10-04실습결과.png)
