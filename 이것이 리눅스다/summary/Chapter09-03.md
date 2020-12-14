## 09-03 네임 서버-마스터네임서버 구축

### 마스터 네임 서버

- 도메인에 속해 있는 컴퓨터들의 이름을 관리
- 외부에 해당 컴퓨터의 IP주소를 알려주는 역할

 ![09-03 마스터 네임 서버 구축](./assets/09-03마스터네임서버구축.png)

 ### [실습3] 마스터 네임 서버 구축

실습목표
- john.com의 '마스터 네임 서버'를 설치하고 운영하자
- 간단한 웹 서비스/FTP 서비스를 제공해 봄
- 네임서버 관련 설정파일을 익힘

1. 서버A에서 웹 서버 만들고 웹페이지를 만듬

    ```bash
    $ rpm -qa httpd
    $ dnf -y install httpd  # 간단한 웹 서버 만들기
    $ systemctl start httpd
    $ firewall-config
    ```

    `영구적` -> `http`, `https` 체크 -> 상단에 `옵션` -> firewalld 다시 불러오기

    ``` bash
    $ gedit /var/www/html/index.html  # 웹 서버 초기 홈페이지
    <h1> CentOS 웹 서버 입니다.</h1>
    ```

2. 서버B에 ftp 서버 설치, FTP 서버로 설정

    ```bash
    $ dnf -y install vsftpd
    $ firewall-cmd --permanent --add-service=ftp  # ftp포트를 영구적으로 열어놓음
    $ firewall-cmd --reload  # 재시작
    $ cd /var/ftp/
    $ vi welcome.msg
    ###################################
    Welcome~~~ This is Linux FTP Server
    ###################################
    :wq
    $ vi /etc/vsftpd/vsftpd.conf
    banner_file=/var/ftp/welcome.msg  # 첫줄에 입력, # 접속 시 출력
    :wq
    $ systemctl restart vsftpd
    ```

3. 서버A 로 돌아와서

    ```bash
    $ vi /etc/named.conf

    # 제일 아래에 적어주기
    zone "john.com" IN {
            type master;
            file "john.com.db";
            allow-update { none; };
    };
    :wq

    $ cd /var/named/
    $ ls
    $ touch john.com.db
    $ vi john.com.db

    $TTL 3H
    @               SOA     @       root. ( 2 1D 1H 1W 1H )
                    IN      NS      @
                    IN      A       192.168.111.100

    www             IN      A       192.168.111.100
    ftp             IN      A       192.168.111.200
    :wq

    named-checkconf  # named.conf 파일 설정이 잘 됐는지 확인
    named-checkzone john.com john.com.db  # john.com, john.com.db 설정 확인

    systemctl restart named
    systemctl status named
    ```

4. linux 클라이언트로 가서 잘 되는지 확인

    ```bash
    $ su -c 'dnf -y install ftp'
    $ cat /etc/resolv.conf  # 네임서버가 192.168.111.100 인지 확인
    $ ftp ftp.john.com
    ```
    `www.john.com` 들어가서 확인하기

5. windows 클라이언트로 가서 잘 되는지 확인

    ```powershell
    netsh interface ip set dns "Ethernet0" static 192.168.111.100
    ```

    `www.john.com` 들어가서 확인하기