## 16-01 DHCP 서버-dhcp 서버 개념과 구현

### DHCP 개념

- DHCP(Dynamic Host Configuration Protocol) 서버가 하는 역할
  - 자신의 네트워크 안에 있는 클라이언트 컴퓨터가 부팅될 때 자동으로 IP주소, 서브넷 마스크, 게이트웨이 주소, DNS 서버 주소를 할당해 주는 것임
- 일반 사용자는 IP에 관련된 어려운 정보를 알지 못해도 인터넷을 사용하는데 더 이상 아무런 문제가 없어짐
- DHCP 서버의 가장 큰 장점은 관리가 편하고 이용자가 편함
- 한정된 IP 주소를 가지고 더 많은 IP 주소가 있는 것처럼 활용 가능, 적은 개수의 IP주소로 여러 명의 사용자가 사용 할 수 있음

### DHCP 서버의 작동원리

![16-01 DHCP 작동 원리](./assets/16-01DHCP작동원리.png)

### [실습1] Windows에서 리눅스 자원 사용

실습목표
- DHCP 서버를 구축
- VMware의 네트워크 구성 환경을 이해

가상머신 모두 초기화 후 클라이언트 터미널에서

DHCP 작동 하는 과정 보기

```bash
$ nm-connection-editor
```

ens160 -> IPv4설정 -> 자동(DHCP)로 설정 -> 저장 

```bash
$ ifconfig ens160
$ /cat /etc/resolv.conf
```

DHCP 작동 안하게 하기

VMware Workstation Pro 열고

상단에 Edit -> Virtual Network Editor -> Change Settings -> VMnet8

DHCP Settings -> 할당 범위(192.168.111.128 ~ 254) 기억하기, Subnet IP(Network 주소), Subnet mask 보기 -> Cancel

NAT Settings -> Gatway IP(192.168.111.2) 기억하기 -> Cancel

아래 네모 상자 두개 위에 켜기 아래 끄기
위 Connect a host virtual adapter to this network
아래 Use local DHCP service to distribute IP address to VMs -> Apply -> OK

다시 클라이언트로 돌아가서

```bash
$ rpm -qa dhcp-client
$ reboot
$ ping www.google.com  # IP 할당을 받지 못해 ping 이 안날라감
```

서버 B를 열어서

```bash
$ ping -c 3 www.google.com  # 핑이 잘 감, 고정 IP로 적용해서 IP가 할당이 되어 있음
$ vi /etc/sysconfig/network-scripts/ifcfg-ens160
> BOOTPROTO=dhcp
> :wq
$ nmcli connection down ens160
$ nmcli connection up ens160
$ reboot  # 확실하게 하기
```

서버 A를 열어서 서버를 DHCP 서버로 구현하기

```bash
dnf -y install dhcp-server
gedit /etc/dhcp/dhcpd.conf
# 제일 아래에 적기
ddns-update-style  interim;
    subnet 192.168.111.0 netmask 255.255.255.0 {
    option routers 192.168.111.2;
    option subnet-mask 255.255.255.0;
    range dynamic-bootp 192.168.111.55 192.168.111.99;
    option domain-name-servers 8.8.8.8;
    default-lease-time 10000;
    max-lease-time 50000;
}
# subnet: 네트워크 주소, netmask: netmask
# option routers: 게이트웨이
# subnet-mask: C클래스(255.255.255.0)
# dynamic-bootp: 동적 할당 주소 범위
# domain-name-servers: 구글 서버(8.8.8.8)
# default-lease-time ~ max-lease-time: 최소 ~ 최대 시간(초)
# 오래 켠 컴퓨터 IP 주소 회수 후 다시 알려주기
ls -l /var/lib/dhcpd/dhcpd.leases  # dhcp 기록 내용을 적는 파일
systemctl restart dhcpd
systemctl enable dhcpd
systemctl status dhcpd
```

리눅스 클라이언트로 돌아가서

```bash
su -c 'systemctl restart NetworkManager'
ifconfig ens160  # 할당 받은 번호 확인해보기
# 인터넷을 들어가서 잘 작동하는지 확인하기
```

서버 B로 가서

```bash
systemctl restart NetworkManager
ifconfig ens160
ping -c 3 www.google.com  # 작동 확인
```

서버 A로 가서 로그 보기

```bash
cat /var/lib/dhcpd/dhcpd.leases
```

DHCP 작동 다시 하기

VMware Workstation Pro 열고

상단에 Edit -> Virtual Network Editor -> Change Settings -> VMnet8

DHCP Settings -> 할당 범위(192.168.111.128 ~ 254)

NAT Settings -> Gatway IP(192.168.111.2)

아래 네모 상자 두개 위에 끄기 아래 켜기
위 Connect a host virtual adapter to this network
아래 Use local DHCP service to distribute IP address to VMs -> Apply -> OK
