## 19-01 PXE 서버-PXE 서버 및 킥스타트 구현

### PXE 설치 서버 개요

- 시나리오
    
    리눅스 전용 교육장을 구축, 100대의 컴퓨터에 CentOS를 설치 하려고 함  
    입/출력 할 Floppy/DVD/USB 장치를 모두 제거, 시간, 장치 문제 발생

- 해결책

    PXE 설치 서버 + 킥스타트

### PXE 설치 서버의 개념도

PXE 설치를 위해서 PXE 설치 서버와 컴퓨터가 모두 같은 네트워크 안에 있어야 함
![19-01 PXE 서버 설치 개념도](./assets/19-01PXE서버설치개념도.png)

### [실습1] PXE 설치 서버 구현

실습목표
- Server에 PXE 설치 서버를 구현

원리: `DHCP서버`의 `ip`를 받고 `tftp`에서 `부팅관련 파일`을 받고 내용을 설치함

1. DHCP 서버, tftp서버, ftp서버 다운로드

    서버 터미널에서

    ```bash
    $ dnf -y install syslinux dhcp-server tftp-server vsftpd  # 관련 패키지 설치
    $ systemctl stop firewalld  # 방화벽 정지
    $ system disable firewalld  # 방화벽 비활성화
    ```

2. DHCP 서버 환경 설정

    ```bash
    $ gedit /etc/dhcp/dhcpd.conf  # dhcp 환경설정
    # 제일 아래에 추가
    subnet 192.168.111.0 netmask 255.255.255.0 {
        option routers 192.168.111.2;
        option subnet-mask 255.255.255.0;
        range dynamic-bootp 192.168.111.120 192.168.111.199;
        option domain-name-servers 192.168.111.2;
        allow booting;
        allow bootp;
        next-server 192.168.111.100;
        filename "pxelinux.0";
    }
    ```

3. 서버는 ftp 서버 역할도 해야 함

    익명의 다운로드를 허락

    ```bash
    $ vi /etc/vsftpd/vsftpd.conf
    # Allow anonynous FTP?
    anonymous_enalbe=YES  # 변경 후 저장
    ```

4. 우리가 넘겨줄 파일(centos)을 ftp서버에 마운트하고 환경설정하기

    DVD에서 centos 넣기

    왼쪽 위에 `settings` -> `connected` -> `centos-dvd` 넣기

    ```bash
    $ umount /dev/cdrom  # 자동 연결 해제
    $ mount /dev/cdrom /var/ftp/pub/  # ftp의 홈 디렉토리로 연결
    ```

    마운트 된 파일중 4가지 파일들을 복사해 tftpboot로 옮겨줌

    ```bash
    $ cp /var/ftp/pub/images/pxeboot/vmlinuz /var/lib/tftpboot/
    $ cp /var/ftp/pub/images/pxeboot/initrd.img /var/lib/tftpboot/
    $ cp /var/ftp/pub/isolinux/ldlinux.c32 /var/lib/tftpboot/
    $ cp /usr/share/syslinux/pxelinux.0 /var/lib/tftpboot/
    $ ls -l /var/lib/tftpboot/  # 4개 파일 존재
    ```

    폴더 생성

    ```bash
    # 부팅하면서 DHCP 서버의 ip를 받고 ftp안의 내용을 설치함
    $ mkdir /var/lib/tftpboot/pxelinux.cfg
    $ cd /var/lib/tftpboot/pxelinux.cfg/
    $ touch default
    $ vi default
    DEFAULT CentOS8_Auto_Install
            LABEL   CentOS8_Auto_Install
            kernel  vmlinuz
            APPEND  initrd=initrd.img repo=ftp://192.168.111.100/pub
    ```

5. 관련 서비스 3개 시작

    ```bash
    $ systemctl restart dhcpd
    $ systemctl restart vsftpd
    $ systemctl restart tftp
    $ systemctl enable dhcpd
    $ systemctl enable vsftpd
    $ systemctl enable tftp
    ```

6. 가상머신 추가해서 잘 동작하는지 확인

    VMware Workstation에서 `Edit`

    -> `Virtual Network Editor`의 `VMware8` -> `NAT`로 설정, `192.168.111.0`으로 설정

    간단하게 가상머신 만들기 test용

    VMware에서 하드와 네트워크만 있는 `test용 서버`를 만듬  
    (실무에서도 DVD나 USB를 막아두는 경우가 많음)

    가상머신을 실행하면 자동으로 PXE의 설치 서버를 연결해 설치함  
    설정파일까지 한번에 하면 더 편할꺼 같음  
    그래서 아래 킥스타트를 하면 편함

### 킥스타트

PXE 설치 서버를 이용할 때 부팅 후에 필요한 작업까지 미리 설정해서

원격 설치시 편리하게 설치할 수 있게 도와주는 기능

킥스타트(Kick Start)는 CentOS 8은 GUI 기능 없어짐

### [실습2] 킥스타트 기능을 추가

실습목표
- PXE 설치 서버에 킥스타트 기능을 추가

`root/anaconda-ks.cfg` 파일을 수정 후 ftp 폴더에 넣는다. [What is anaconda-ks.cfg?](https://unix.stackexchange.com/questions/398410/what-is-anaconda-ks-cfg/398417#:~:text=It's%20the%20kickstart%20file%20made,cfg.)

`Anaconda-ks.cfg` is the kickstart file made by the anaconda installer based on your configured settings.

서버 터미널에서

```bash
$ ls /root/anaconda-ks.cfg  # 이 파일이 초기에 설정했던 파일임
$ vi /root/anaconda-ks.cfg  # 들어가서 확인만 하기
# 이 파일을 수정 후 ftp 파일에 추가하기만 하면 킥스타트 가능
# 1. 복사해서 ftp에 옮겨서 수정하기
$ cp /root/anaconda-ks.cfg /var/ftp/centos.ks
$ cd /var/ftp
$ ls
$ vi centos.ks
# graphical url 부분을 다음과 같이 수정
url     --url=ftp://192.168.111.100/pub
# % package ~ %end 사이에 원하는 패키지를 추가
%package
@^Server with GUI
@GNOME Applications
mc
%end
# 패키지 환경 그룹
# 패키지 그룹
# mc 패키지 하나 추가
# 2. 추가를 위한 설정하기
$ cd /var/lib/tftpboot/pxelinux.cfg/
$ ls  # 아까 추가한 default 수정하기
$ gedit default
# APPEND 끝에 다음을 추가
ks=ftp://192.168.111.100/centos.ks
```

가상머신 생성 후 테스트 해보기

하드는 반드시 SCSI 80GB로 설정(서버와 동일한 환경)
