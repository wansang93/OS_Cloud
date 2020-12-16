## 09-01 네임 서버-네임서버 개념과 hosts 파일 역할

### 네임 서버 개요

- 네임 서버 = DNS(Domain Name System) 서버
- 도메인 이름을 IP 주소로 변환시켜주는 역할

1. IP 주소로 접근
   - 초창기에 네트워크 접속 방법
   - 핸드폰 전화번호를 바로 쳐서 들어가는 역할
2. hosts 파일을 이용하여 네트워크 접속
   - hosts 파일에 URL과 IP주소를 기록해 놓은 방식 사용
   - linux: `/etc/hosts`
   - windows: `C:\Windows\system32\drivers\etc\hosts`
   - 핸드폰 연락처와 같은 역할
3. 네임 서버를 이용하여 네트워크 접속
   - 네트워크 상의 컴퓨터의 모든 IP 정보 파악 무리
   - 이름 해석(Name Resolution)을 전문적으로 해주는 서버 필요
   - 전화 안내 서비스인 114와 같은 역할

### [실습1] /etc/host 파일 설정 확인

실습목표
- /etc/hosts 파일의 작동을 이해
- 네임 서버가 하는 기본적인 역할을 이해
- IP 주소를 얻기 위해 어떤 순서로 작동하는지 확인

```bash
$ nslookup  # 특정 컴퓨터의 IP 주소를 확인하는 방법
> server  # 192.168.111.2 출력
> www.nate.com  # 120.50.132.112
> www.hanbit.co.kr  # 218.38.58.195

$ cat /etc/resolv.conf  # 네임 서버 확인하기
$ nano /etc/resolv.conf  # vi 상위호환 버전
# nameserver  # nameserver 주석 처리 후 Ctrl+x후 y로 저장, 엔터

$ nano /etc/hosts  # 연락처 열기
218.38.58.195  www.hanbit.co.kr  # 연락처에 추가
163.239.1.17  www.nate.com  # 서강대 IP를 네이트로 저장, 네이트 접속 시 서강대로 들어가짐
```
