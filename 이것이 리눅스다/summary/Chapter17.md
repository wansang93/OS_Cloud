## 17-01 프록시 서버-프록시 서버 개념과 구현

### 프록시 서버 개념

- 프록시(Proxy)란 단어의 뜻인 '대리인'의 역할을 하는 서버
- 웹 환경에서 프록시 서버는 웹 클라이언트와 웹 서버 사이에서 요청한 데이터를 전달하는 역할
- 한번 전송한 데이터를 캐시에 저장한 후, 같은 데이터를 또 요청할 경우에 캐시에 저장된 것을 보내줌
- 서버 구현시 네트워크 환경을 좀 더 빠르고 비용 절감이 될 수 있음

![17-01 프록시 서버 개념](./assets/17-01프록시서버개념.png)

### [실습1] 프록시 서버 구현

실습목표
- CentOS에서 제공되는 `Squid 프록시 서버`를 설치
- 설정 파일인 `/etc/squid/squid.conf`파일 내용을 파악
- 웹 클라이언트의 다운로드 속도가 향상되는 것을 확인

서버 터미널에서

```bash
dnf -y install squid
vi /etc/squid/squid.conf
:set nu
29행(acl 밑에): 빈줄에 acl centos8 src 192.168.111.0/255.255.255.0 추가
57행(http_access 밑에): http_access allow centos8
65행(cache_dir): 주석 풀고 100을 1000으로 수정
78행(제일 아랫줄): visible_hostname  centos8 추가
:wq
firewall-cmd --permanent --add-port=3128/tcp
firewall-cmd --reload
```

리눅스 클라이언트에서 파이어폭스에서

오른쪽 메뉴 버튼 -> Preferences -> 제일 아래 Network Proxy Settings

Manual proxy configuration 클릭
HTTP Proxy: `192.168.111.100` Port: `3128` -> OK

다시 웹 작동시 작동 불가, 이유: 웹 프록시 서버가 작동을 안하기 때문에

다시 서버에서

```bash
systemctl restart squid
```

다시 리눅스 클라이언트에서 열어서 웹 실행 후 아무 사이트 들어가면 가능

윈도우 클라이언트에서

마우스 오른쪽 -> 설정 -> 네트워크 및 인터넷 -> 프록시 -> 자동 끔 -> 프록시 서버 사용

`192.168.111.100` Port: `3128` -> OK

인터넷 들어가서 아까 들어간 사이트 접속 시 자동으로 캐쉬에 저장된 데이터를 부름
