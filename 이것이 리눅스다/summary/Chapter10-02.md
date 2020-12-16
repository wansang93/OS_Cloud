## 10-02 메일 서버-메일서버 개념과 네임서버 구축(2)

### [실습1] 메일서버 구현을 위한 네임서버 구현

실습목표
- 메일 서버 환경을 구축하기 위해서 우선 naver.com 및 daum.net의 도메인을 관리하는 네임 서버를 구축

1. 서버A에서 메일 서버 설정

    ```bash
    $ dnf -y install sendmail  # 메일 보내기 다운
    $ nano /etc/hostname
    localhost.localdomain -> mail.naver.com  # 이걸로 수정 후 Ctrl + X(나가기) 후 Y(저장) 후 Enter
    $ nano /etc/hosts
    192.168.111.100   mail.naver.com  # 제일 아래에 추가하기
    $ nano /etc/mail/local-host-names
    mail.naver.com  # 추가
    $ nano /etc/sysconfig/network
    HOSTNAME=mail.naver.com  # 추가
    # 재부팅 후 호스트 네임이 mail.naver.com 인지 확인
    reboot
    hostname
    ```

2. 서버B에서 메일 서버 설정
    
    ```bash
    $ dnf -y install sendmail
    $ vi /etc/hostname
    localhost.localdomain -> mail.daum.net
    :wq
    $ vi /etc/hosts
    192.168.111.200   mail.daum.net  # 제일 아래에 추가
    :wq
    $ vi /etc/mail/local-host-names
    mail.daum.net  # 추가
    :wq
    $ vi /etc/sysconfig/network
    HOSTNAME=mail.daum.net
    :wq
    # 재부팅 후 호스트 네임이 mail.daum.net 인지 확인
    reboot
    $ hostname
    ```

3. 서버A를 완전한 네임 서버로 구현

    ```bash
    dnf -y install bind bind-chroot
    vi /etc/named.conf
    :set nu  # 행번호 보기
    11행(listen-on): 127.0.0.1; -> any;
    12행(listen-on-v6): ::1; -> none;
    19행(allow-query): localhost; -> any;
    34행(dnssec-validation): yes; -> no;

    # 제일 아래에
    zone "naver.com" IN {
            type master;
            file "naver.com.db";
            allow-update { none; };
    };

    zone "daum.net" IN {
            type master;
            file "daum.net.db";
            allow-update { none; };
    };
    :wq

    $ cd /var/named/
    $ ls
    $ touch naver.com.db daum.net.db
    $ vi naver.com.db

    $TTL 3H
    @               SOA     @       root. ( 2 1D 1H 1W 1H )
                    IN      NS      @
                    IN      A       192.168.111.100
                    IN      MX      10  mail.naver.com.

    mail            IN      A       192.168.111.100
    # IN MX mail.naver.com. 이부분은 메일이 오면 여기로 보내라 라는 의미
    :wq

    $ vi daum.net.db
    $TTL 3H
    @               SOA     @       root. ( 2 1D 1H 1W 1H )
                    IN      NS      @
                    IN      A       192.168.111.200
                    IN      MX      10  mail.daum.net.

    mail            IN      A       192.168.111.200
    :wq

    $ named-checkconf
    $ named-checkzone naver.com naver.com.db
    $ named-checkzone daum.net daum.net.db
    $ systemctl restart named
    $ systemctl enable named
    $ systemctl status named
    $ systemctl stop firewalld
    $ systemctl disable firewalld
    # 네임 서버가 잘 작동하는지 확인
    $ nslookup
    > server 192.158.111.100
    > mail.naver.com
    > mail.daum.net
    > exit

    # 네임 서버를 영구적으로 168.111.100번으로 지정하기
    $ vi /etc/sysconfig/network-scripts/ifcfg-ens160
    DNS1="192.168.111.100"
    :wq
    $ vi /etc/resolv.conf
    nameserver 192.168.111.100
    $ reboot  # 확실하게 하기 위해 재부팅
    ```

4. 나머지 3개의 컴퓨터에서 네임 서버를 192.168.111.100 으로 바꾸기

    서버B 터미널에서 설정

    ```bash
    $ vi /etc/sysconfig/network-scripts/ifcfg-ens160
    DNS1=192.168.111.100
    :wq
    $ vi /etc/resolv.conf
    nameserver 192.168.111.100
    :wq
    $ reboot  # 확실하게 하기 위해 재부팅
    ```

    리눅스 클라이언트 터미널에서 설정

    ```bash
    $ su -c 'gedit /etc/resolv.conf'
    nameserver 192.168.111.100
    $ nslookup
    > server  # 192.168.111.100
    > mail.naver.com  # 192.168.111.100
    > mail.daum.net  # 192.168.111.200
    ```

    윈도우 클라이언트에서 관리자 권한으로 파워쉘 접속해 설정

    ```powershell
    C:\Windows\system32> netsh interface ip set dns "Ethernet0" static 192.168.111.100
    C:\Windows\system32> nslookup
    > mail.naver.com
    > mail.daum.net
    ```
