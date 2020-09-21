## 03-01 CentOS8 리눅스 설치-Server

1. VMware에 Server에 CentOS 8 설치하기

   1. CentOS 8 다운로드  
       CentOS 8 다운로드 링크 -> [https://mirrors.oit.uci.edu/centos/8.0.1905/isos/x86_64/CentOS-8-x86_64-1905-dvd1.iso](https://mirrors.oit.uci.edu/centos/8.0.1905/isos/   x86_64/CentOS-8-x86_64-1905-dvd1.iso)
   2. Vmware로 가서 ```Server``` -> ```Edit virtual machine settings``` -> ```CD/DVD``` ->  ```Connect at power on``` 체크 -> ```Use ISO image file``` -> 다운로드 받은 .iso 파일로 지정 후 완료
   3. CentOS 8 설치
      1. ```Install CentOS Linux 8.0.1905``` 로 이동 후 실행
      2. 한국어 설정
      3. 시간 및 날짜 -> 서울
      4. 네트워크 & 호스트 이름 -> 이더넷 \[켬\]
      5. 소프트웨어 선택 -> 워크스테이션
      6. 설치 목적지 -> 로컬 디스크 표준 클릭 -> Custom -> 완료
         1. LVM -> 표준 파티션으로 변경
         2. ```+``` 버튼 클릭 -> 마운트 지점: ```swap``` -> 원하는 능력: 4G -> 마운트 지점 추가
         3. ```+``` 버튼 클릭 -> 마운트 지점: ```\``` -> 마운트 지점 추가
         4. 완료
         5. 변경사항 적용
      7. 설치 시작
      8. Root 암호(password)
      9. User Creation -> 안에 내용 설정 후 저장
      10. 환경 설정하기 -> 한국어 -> 한국어(Hangul)
      11. 설정 -> 개인정보 -> 화면잠금 -> 자동 화면 잠금 해제

**중요!** VMWare root 계정으로 들어가기

2. Terminal 가서 CentOS 자동 업데이트 방지

   1. ```gsettings set org.gnome.software download-updates false``` 입력
   2. ```systemctl disable dnf-makecache.service``` 입력
   3. ```systemctl disable dnf-makecache.timer``` 입력

3. Terminal 에서 CentOS 패키지 업데이트 방지

   1. ```cd  /etc/yum.repos.d/```
   2. ```mkdir backup```(백업 폴더 생성)
   3. ```ls```: 상태 확인
   4. ```mv  *.repo  backup/```: .repo 파일들을 백업 폴더로 이동
   5. ```ls```: 상태 확인
   6. ```gedit  This.repo```: This.repo 메모 파일 생성
   7. 다음과 같이 입력
      ``` m
        [BaseOS]
        name=CentOS-$releasever - Base
        baseurl=http://vault.centos.org/8.0.1905/BaseOS/x86_64/os/
        gpgcheck=0
        [AppStream]
        name=CentOS-$releasever - AppStream
        baseurl=http://vault.centos.org/8.0.1905/AppStream/x86_64/os/
        gpgcheck=0
        [extras]
        name=CentOS-$releasever - Extras
        baseurl=http://vault.centos.org/8.0.1905/extras/x86_64/os/
        gpgcheck=0
        [centosplus]
        name=CentOS-$releasever - Plus
        baseurl=http://vault.centos.org/8.0.1905/centosplus/x86_64/os/
        gpgcheck=0
        [PowerTools]
        name=CentOS-$releasever - PowerTools
        baseurl=http://vault.centos.org/8.0.1905/PowerTools/x86_64/os/
        gpgcheck=0
      ```
   8. ```dnf  clean  all```

4. Server를 고정 IP 주소로 설정

   1. ```cd  /etc/sysconfig/network-scripts/```: 디렉토리 이동
   2. ```ls```: 파일 목록
   3. ```gedit  ifcfg-ens160```: ifcfg-ens160을 다음과 같이 수정
      ``` m
      TYPE="Ethernet"
      PROXY_METHOD="none"
      BROWSER_ONLY="no"
      
      BOOTPROTO="none"
      
      IPADDR="192.168.111.100"
      NETMASK="255.255.255.0"
      GATEWAY="192.168.111.2"
      DNS1="192.168.111.2"
      
      DEFROUTE="yes"
      IPV4_FAILURE_FATAL="no"
      IPV6INIT="yes"
      IPV6_AUTOCONF="yes"
      IPV6_DEFROUTE="yes"
      IPV6_FAILURE_FATAL="no"
      IPV6_ADDR_GEN_MODE="stable-privacy"
      NAME="ens160"
      UUID="4d0a9185-264c-4a47-bca5-9cd7d6c6f1dc"
      DEVICE="ens160"
      ONBOOT="yes"
      ```
   4. ```nmcli  connection  down  ens160```: ens160 connection down
   5. ```nmcli  connection  up  ens160```: ens160 connection up
   6. ```reboot```: 컴퓨터 다시 시작
   7. ```ifconfig  ens160```: inet이 192.168.111.100 으로 설정 됬는지 확인

6. selinux 보안기능 끄기

   1. ```gedit  /etc/sysconfig/selinux```: 편집기 열기
      1. ```SELINUX=disabled``` 로 설정 후 저장

7. 한글 설정

   설정 -> 지역 및 언어 -> ```한국어(Hangul)```만 남기고 나머지 ```-```

8. 해상도 설정

   1. Terminal -> ```gedit  /etc/grub.d/10_linux```
   2. 169 행 끝에 " 바로 안쪽에 ```vga=773``` 입력  
      결과: ```${grub_editenv} - set kernelopts="root=$ linux_root_device_thisversion} ro ${args} vga=773"```
   3. ```grub2-mkconfig  -o  /boot/grub2/grub.cfg```

9. 방화벽 설치

   1. Terminal -> ```dnf  -y install  firewall-config```: 방화벽 설치 명령어

10. 소프트웨어 업데이트 끄기

   1. 프로그램 표시 -> 아랫쪽에 모두 클릭 -> 소프트웨어 클릭
   2. 왼쪽 위에 소프트웨어 클릭 -> 업데이트 기본 설정 -> 두개 다 끄기

11. 기타 설정

      가상머신 메모리 줄이기(2GB -> 1.5GB(1536MB))

      1. VMware Player 에서 Edit -> Memory(1536MB)로 수정

      CD 꺼내기

      1. VMware Player 에서 Edit -> CD/DVD -> Connect at power on 체크 해제, Use pysical drive로 설정

      SnapShot 찍기

      1. VMware Pro 에서 Open a Virtual Machine -> 원하는 가상 머신 클릭
      2. ```VM``` -> ```snapshot``` -> ```snapshot manager``` -> ```Take snapshot``` -> 원하는 이름 설정 후 저장

## 03-02 CentOS8 리눅스 설치-ServerB

위에와 비슷하게 설치하는데 다른 점: Software Selection에 Minimal install로 설정

1. root 와 password 입력으로 계정 접속

   ```setfont sun12x22```: 폰트 크기 설정

2. 기본적인 패키지 설치(bind--utils, net-tools, wget, unzip, bzip2)

   ```dnf  -y install bind--utils  net-tools  wget  unzip  bzip2```

3. Terminal 에서 CentOS 패키지 업데이트 방지

   1. ```cd  /etc/yum.repos.d/```: 패키지 업데이트 들어가기
   2. ```ls```: 파일 목록 보기
   3. ```rm  -f  *.repo```: .repo 확장자 파일 모두 삭제
   4. ```wget  http://download.hanbit.co.kr/centos/8/This.repo```: 다음 내용 This.repo 파일로 생성
      ``` m
         [BaseOS]
         name=CentOS-$releasever - Base
         baseurl=http://vault.centos.org/8.0.1905/BaseOS/x86_64/os/
         gpgcheck=0
         [AppStream]
         name=CentOS-$releasever - AppStream
         baseurl=http://vault.centos.org/8.0.1905/AppStream/x86_64/os/
         gpgcheck=0
         [extras]
         name=CentOS-$releasever - Extras
         baseurl=http://vault.centos.org/8.0.1905/extras/x86_64/os/
         gpgcheck=0
         [centosplus]
         name=CentOS-$releasever - Plus
         baseurl=http://vault.centos.org/8.0.1905/centosplus/x86_64/os/
         gpgcheck=0
         [PowerTools]
         name=CentOS-$releasever - PowerTools
         baseurl=http://vault.centos.org/8.0.1905/PowerTools/x86_64/os/
         gpgcheck=0
      ```
   5. ```cat  This.repo```: 만든 파일 확인

4. Server를 고정 IP 주소로 설정

   1. ```cd  /etc/sysconfig/network-scripts/```
   2. ```ls```
   3. ```vi  ifcfg-ens160```: vi 편집기로 ifcfg-ens160 파일 수정(a, i 키로)
      1. ```BOOTPROTO="dhcp"``` -> ```"none"``` 으로
      2. 아래 내용을 BOOTPROTO 아래에 추가
         ``` m
         IPADDR=192.168.111.200
         NETMASK=255.255.255.0
         GATEWAY=192.168.111.2
         DNS=192.168.111.2
         ```
      3. :wq로 저장 후 빠져나오기
   4. ```nmcli  connection  down  ens160```: 연결 끊기
   5. ```nmcli  connection  up  ens160```: 연결 하기
   6. ```reboot```: 재 부팅
   7. ```ip  addr```: ip 확인
   8. ```ping  -c  3  8.8.8.8```: google로 응답 3번 받기

5. selinux 보안기능 끄기

   1. ```vi  /etc/sysconfig/selinux```: 편집기 열기
      1. ```SELINUX=disabled``` 로 설정 후 저장

6. 해상도 설정

   1. Terminal -> ```gedit  /etc/grub.d/10_linux```
   2. 169 행 끝(```:set nu```로 설정)에 " 바로 안쪽에 ```vga=771``` 입력  
      결과: ```${grub_editenv} - set kernelopts="root=$ linux_root_device_thisversion} ro ${args} vga=771"```
   3. ```grub2-mkconfig  -o  /boot/grub2/grub.cfg```
   4. ```reboot```: 재 시작 후 해상도가 줄어든 것을 볼 수 있음

7. 컴퓨터 끄기

   ```halt  -p```

8. 기타 설정

      가상머신 메모리 줄이기(2GB -> 0.5GB(512MB))

      1. VMware Player 에서 Edit -> Memory(512MB)로 수정

      CD 꺼내기

      1. VMware Player 에서 Edit -> CD/DVD -> Connect at power on 체크 해제, Use pysical drive로 설정

      SnapShot 찍기

      1. VMware Pro 에서 Open a Virtual Machine -> 원하는 가상 머신 클릭
      2. ```VM``` -> ```snapshot``` -> ```snapshot manager``` -> ```Take snapshot``` -> 원하는 이름 설정 후 저장

## 03-03 CentOS8 리눅스 설치-Client

1. CentOS 8 설치
   1. ```Install CentOS Linux 8.0.1905``` 로 이동 후 실행
   2. 한국어 설정
   3. 시간 및 날짜 -> 서울
   4. 네트워크 & 호스트 이름 -> 이더넷 \[켬\]
   5. 소프트웨어 선택 -> 워크스테이션
   6. 설치 목적지 -> 로컬 디스크 표준 클릭 -> Custom -> 완료
      1. LVM -> 표준 파티션으로 변경
      2. ```+``` 버튼 클릭 -> 마운트 지점: ```swap``` -> 원하는 능력: 4G -> 마운트 지점 추가
      3. ```+``` 버튼 클릭 -> 마운트 지점: ```\``` -> 마운트 지점 추가
      4. 완료
      5. 변경사항 적용
   7. 설치 시작
   8. Root 암호(password)
   9. User Creation -> 안에 내용 설정 후 저장
   10. 환경 설정하기 -> 한국어 -> 한국어(Hangul)

2. Terminal 가서 CentOS 자동 업데이트 방지

   1. ```gsettings set org.gnome.software download-updates false``` 입력
   2. ```systemctl disable dnf-makecache.service``` 입력
   3. ```systemctl disable dnf-makecache.timer``` 입력

3. Terminal 에서 CentOS 패키지 업데이트 방지

   1. ```cd  /etc/yum.repos.d/```
   2. ```ls```: 상태 확인
   3. ```rm  -f  *.repo```: .repo 확장자 파일 모두 삭제
   4. ```wget  http://download.hanbit.co.kr/centos/8/This.repo```: 다음과 같은 This.repo 파일이 만들어 짐
      ``` m
        [BaseOS]
        name=CentOS-$releasever - Base
        baseurl=http://vault.centos.org/8.0.1905/BaseOS/x86_64/os/
        gpgcheck=0
        [AppStream]
        name=CentOS-$releasever - AppStream
        baseurl=http://vault.centos.org/8.0.1905/AppStream/x86_64/os/
        gpgcheck=0
        [extras]
        name=CentOS-$releasever - Extras
        baseurl=http://vault.centos.org/8.0.1905/extras/x86_64/os/
        gpgcheck=0
        [centosplus]
        name=CentOS-$releasever - Plus
        baseurl=http://vault.centos.org/8.0.1905/centosplus/x86_64/os/
        gpgcheck=0
        [PowerTools]
        name=CentOS-$releasever - PowerTools
        baseurl=http://vault.centos.org/8.0.1905/PowerTools/x86_64/os/
        gpgcheck=0
      ```
   5. ```dnf  clean  all```

4. 해상도 설정

   1. Terminal -> ```gedit  /etc/grub.d/10_linux```
   2. 169 행 끝에 " 바로 안쪽에 ```vga=773``` 입력  
      결과: ```${grub_editenv} - set kernelopts="root=$ linux_root_device_thisversion} ro ${args} vga=773"```
   3. ```grub2-mkconfig  -o  /boot/grub2/grub.cfg```

5. 루트 접속 금지

   1. ```gedit  /etc/pam.d/gdm-password```: gdm-password 파일 수정

      5행을 다음과 같이 수정하면 root로 접속을 못함 **주의! 잘못 입력 시 컴퓨터를 못킴**
      ``` m
      auth        required      pam_succeed_if.so  user  !=  root  quiet
      ``` 
   2. ```reboot```: 재부팅 후 접속 불가 확인하기
   3. 다른 사용자로 들어가서 Terminal에서 ```su``` 입력시 super user로 암호 입력시 root계정으로 명령어 사용 가능

6. 기본 설정

   한글 설정

   설정 -> 지역 및 언어 -> ```한국어(Hangul)```만 남기고 나머지 ```-```

   배경 설정

   설정 -> 배경 -> 배경 -> 수정 후 선택

   소프트웨어 업데이트 끄기

   1. 프로그램 표시 -> 아랫쪽에 모두 클릭 -> 소프트웨어 클릭
   2. 왼쪽 위에 소프트웨어 클릭 -> 업데이트 기본 설정 -> 두개 다 끄기

7. 자동으로 로그인 하기

   1. Terminal에서 ```su``` 입력
   2. root 계정의 암호 입력
   3. ```vi /etc/gdm/custom.conf``` 입력
      daemon 아래에 다음과 같이 추가 후 저장
      ``` m
      [daemon]
      AutomaticLoginEnable=True
      AutomaticLogin=centos
      ```
   4. ```reboot``` 입력 후 자동 로그인 되는지 확인

8. 기타 설정

      가상머신 메모리 줄이기(2GB -> 1.5GB(1536MB))

      1. VMware Player 에서 Edit -> Memory(1536MB)로 수정

      CD 꺼내기

      1. VMware Player 에서 Edit -> CD/DVD -> Connect at power on 체크 해제, Use pysical drive로 설정

      SnapShot 찍기

      1. VMware Pro 에서 Open a Virtual Machine -> 원하는 가상 머신 클릭
      2. ```VM``` -> ```snapshot``` -> ```snapshot manager``` -> ```Take snapshot``` -> 원하는 이름 설정 후 저장

## 03-04 리눅스 설치-WinClient

Windows Server 2016 평가판(30일) 링크 -> [https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-server-2016/](https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-server-2016/)

Windows 10 Enterprise 평가판(90일) 링크 -> [https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-10-enterprise](https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-10-enterprise)

여기서 Client는 10 Enterprise 32bit로 Windows Client를 운영

0. 일반적인 Window 설치대로 설치(잘 모를 경우 강의 참고)

1. VMware 드라이브 설치하기

   1. VMware 에서 오른쪽 위에 ```Player``` -> ```Manage``` -> ```Install VMware Tools```
   2. 다운로드 후 ```내 PC``` -> ```D:``` -> ```setup``` 실행

2. 기타 설정

      CD 꺼내기

      1. VMware Player 에서 Edit -> CD/DVD -> Connect at power on 체크 해제, Use pysical drive로 설정

      SnapShot 찍기

      1. VMware Pro 에서 Open a Virtual Machine -> 원하는 가상 머신 클릭
      2. ```VM``` -> ```snapshot``` -> ```snapshot manager``` -> ```Take snapshot``` -> 원하는 이름 설정 후 저장