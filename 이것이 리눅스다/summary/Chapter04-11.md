## 04-11 필수 개념과 명령어-네트워크 필수 개념과 관련파일

### 네트워크 관련 필수 개념

- TCP / IP
  - 컴퓨터의 프로토콜
- Hostname, Domain name
  - 컴퓨터에 지정된 이름
- IP address
- Network address
  - 같은 네트워크에 속한 공통된 주소(끝자리 0)
- Broadcast address
  - 내부 네트워크의 모든 컴퓨터가 듣게 되는 주소(끝자리 255)
- Gateway, Router
  - VMware의 게이트웨이 주소는 192.168.111.2로 고정
- Netmask & Class
  - 255.255.255.0 - C클래스
- DNS(Domain Name System)(name server)
  - 설정파일은 ```/etc/resolve.conf```에 있음
  - DHCP서버는 서버를 자동으로 할당
- 리눅스에서의 네트워크 장치 이름
  - CentOS8은 랜카드를 ens160 인식함
  - 이전 버전은 eth0, eth1, ens32, ens33 등으로 인식
  - VMware에 CentOS를 설치할 경우 완전히 다른 이름으로 인식할 수 도 있음

### 네트워크 관련 명령어

- ```nmtui```
  - 네트워크와 관련된 대부분의 작업을 이 명령어에서 수행
  - 텍스트 기반으로 작동
- ```systemctl <start|stop|restart|status> NetworkManager```
  - 네트워크의 설정을 변경한 후에 변경된 내용을 시스템에 적용
- ```ifup <장치이름>```, ```ifdown <장치이름>```
  - 네트워크 장치 On, Off
- ```ifconfig <장치이름>```
  - 네트워크 장치의 IP주소 설정
- ```nslookup```
  - DNS 서버의 작동을 테스트
- ```ping <ip주소|URL>```
  - 해당 컴퓨터가 네트워크상에서 응답하는지를 테스트

### 네트워크 설정과 관련된 주요 파일

- ```/etc/sysconfig/network```
  - 네트워크의 기본적인 정보가 설정되어 있는 파일
- ```/etc/sysconfig/network-scripts/ifcfg-ens160```
  - ens32 장치에 설정된 네트워크 정보가 모두 들어 있는 파일
- ```/etc/resolv.conf```
  - DNS 서버의 정보 및 호스트 이름이 들어 있는 이름, 이 정보는 사실 위에 디렉토리에 링크되서 받아옴
- ```/etc/hosts```
  - 현 컴퓨터의 호스트 이름 및 FQDN이 들어 있는 파일
