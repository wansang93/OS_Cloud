## 04-12 필수 개념과 명령어-nmtui 명령 실습, SELinux 개념

### nmtui 명령

[실습14] nmtui 명령

- nmtui 명령의 작동을 이해한다.
- 네트워크 관련 파일들의 내용을 확인한다.
- DNS의 작동을 /etc/resolve.conf 파일과 연관해서 이해한다.

``` bash
nmtui  # GUI식 네트워크 설정
cat /etc/sysconfig/network  # 네트워크 사용하는지 보기(아무것도 없으면 사용)
cat /etc/sysconfig/network-scripts/ifcfg-ens160  # 네트워크 정보 보기
systemctl restart NetworkManager  # 네트워크 환경 재시작
cat /etc/resolv.conf  # DNS 서버 바꾸기
vi etc/resolv.conf
    nameserver 168.126.63.1
systemctl restart NetworkManager
cat /etc/resolv.conf
nslookup  # DNS 보기
    server  # DNS 설정 주소 보기
    www.hanbit.co.kr  # 한빛 사이트 연결 보기
ping -c 3 www.google.com  # 핑 3번 보내기
```

### 네트워크 보안을 위한 SELinux

- Security Enhanced Linux로 취약한 리눅스를 보호
- 설정 파일인 ```/etc/sysconfig/selinux``` 를 편집, ```system-config-selinux``` 명령으로 설정
- 강제(Enforcing), 허용(Permissive), 비활성(Disabled) 세 가지 레벨
  - 시스템 보안에 영향을 미치는 기능 감지시 다음과 같음
  - 강제: 그 기능 작동이 않되게 시스템에서 막음
  - 허용: 허용은 하지만 그 내용이 로그에 남음
  - 비활성: SELinux 사용 안함
