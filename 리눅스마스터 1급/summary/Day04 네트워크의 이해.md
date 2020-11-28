# 3. 네트워크의 이해

## 3-1. 네트워크의 기초

### 3-1-1. OSI 7 계층

1. OSI 7 계층의 개요
   1. 정의
   2. 특징

2. OSI 7 계층 세부 설명
   1. 1 계층: 물리 계층(Physical Layer)
   2. 2 계층: 데이터 링크 계층(Data Link Layer)
   3. 3 계층: 네트워크 계층(Network Layer)
   4. 4 계층: 전송 계층(Transport Layer)
   5. 5 계층: 세션 계층(Session Layer)
   6. 6 계층: 표현 계층(Presentation Layer)
   7. 7 계층: 응용 계층(Application Layer)

3. OSI 7 계층의 전송 단위 및 프로토콜
   1. OSI 7 계층의 전송 단위
   2. OSI 7 계층의 프로토콜

### 3-1-2. 네트워크 장비

1. LAN 구성 장비
   1. 네트워크 카드(Network Card)
   2. 케이블
   3. 허브

2. 인터네트워크 장비
   1. 리피터
   2. 브리지
   3. 라우터
   4. 게이트웨이

### 3-1-3 데이터 통신의 기본 이해

1. 네트워크토폴로지
   1. 스타(star)형
   2. 버스(bus)형
   3. 링(ring)형
   4. 망(mesh)형

2. 네트워크 통신 방식
   1. 이더넷(Ethernet)
   2. 토큰링(Token Ring)
   3. FDDI(Fiber Distributed Data Interface)

3. 네트워크 유형
   1. LAN(Local Area Network)
   2. MAN(Metropolitan Area Network)
   3. WAN(Wide Area Network)

4. 교환 방식
   1. 회선 교환 방식(Circuit Switched Network)
   2. 패킷 교환 방식(Packet Switch Network)

5. 패킷 교환 기술
   1. X.25
   2. 프레임 릴레이
   3. 셀 릴레이(ATM: Asynchronous Transfer Mode)

### 3-1-4. TCP/IP 및 네트워크 프로토콜의 이해

1. 프로토콜
   1. 프로토콜의 개요
   2. 프로토콜의 기능

2. TCP/IP
   1. TCP/IP 개요
   2. TCP/IP 구조
   3. TCP와 UDP
   4. 포트 번호
   5. 소켓

3. IP 주소(internet protocol address)
   1. IP 주소
   2. IP 주소의 클래스
   3. 특수 목적 IP 주소

4. 서브넷(subnetting)
   1. 서브넷의 필요성
   2. 서브넷마스크(subent mask)
   3. 서브넷마스크와 호스트의 갯수
   4. C 클래스 기준 서브넷 구성해보기

5. 도메인(domain)
   1. 도메인네임(Domain Name)
   2. 도메인 체계
   3. 도메인네임 시스템(DNS: Domain Name System)
   4. ICANN(Internet Corporation for Assgined Names and Numbers)

6. IPv6(Internet Protocol version 6)
   1. IPv6 개요
   2. 특징
   3. IPv4와의 비교

## 3-2. 네트워크의 설정

### 3-2-1. 환경설정

1. 리눅스 네트워크 환경설정 개요
   1. 호환성
   2. 다양성

2. 인터넷 접속을 위한 이더넷 카드(Ethernet card) 설치하기
   1. ~

3. 인터넷 접속을 위한 네트워크 인터페이스 설정 방법
   1. GUI 기반 네트워크 설정(CentOS 6.9기준)
   2. 텍스트 기반 네트워크 설정
   3. 명령어를 통한 IP 수동 설정
   4. 네트워크 설정 파일을 통한 IP 수동 설정

### 3-2-2. 네트워크 설정 명령어

1. ifconfig
   1. 설명
   2. 형식
   3. 네트워크설정 보기
   4. 모든 네트워크 인터페이스의 설정 보기
   5. 특정 네트워크 인터페이스의 설정 보기
   6. 특정 네트워크 인터페이스 활성화 및 비활성화 하기
   7. 네트워크 설정하기

2. route
   1. 설명
   2. 형식
   3. 라우팅 테이블 출력하기
   4. 디폴트 게이트웨이 추가 및 삭제하기
   5. 특정 네트워크에 대한 라우팅 정보 추가 및 삭제하기
   6. 특정 호스트에 대한 라우팅 정보 추가 및 삭제하기

3. arp
   1. 설명
   2. 형식
   3. arp 캐시 보기
   4. arp 캐시에 정보 추가 및 삭제하기
   5. 그 밖의 옵션

### 3-2-3. 네트워크 진단 명령어

1. ethtool
   1. 설명
   2. 형식
   3. 예제

2. ip
   1. 설명
   2. 형식
   3. 주요 옵션
   4. 네트워크 인터페이스의 정보 출력
   5. IP 할당 및 제거
   6. 네트워크 인터페이스 상태 및 파라미터 변경
   7. 네트워크 인터페이스의 ARP 캐시 관리
   8. 라우팅 정보 관리

3. ping
   1. 설명
   2. 형식
   3. 주요 옵션
   4. Ping 전송하기
   5. 정한 시간 동안 ping하기

4. netstat
   1. 설명
   2. 형식
   3. 주요 옵션
   4. 연결되어 있는 모든 소켓 정보 출력하기
   5. 라우팅 정보 출력하기
   6. 특정 주소 패밀리(address family)에 대한 정보만 출력

5. traceroute
   1. 설명
   2. 형식
   3. 특정 사이트에 어떤 경로로 패킷이 전달되는지 추적하기
   4. 다양한 방식을 통해 경로 추적하기

6. mil-tool
   1. 설명
   2. 형식
   3. 네트워크 인터페이스 정보 출력
   4. 네트워크 인터페이스 재시작
   5. 네트워크 인터페이스 설정 변경

7. ss
   1. 설명
   2. 형식
   3. 옵션
   4. 주요 예제

### 3-2-4. DNS 명령어

1. nslookup
   1. 설명
   2. 형식
   3. 대화형으로 네임 서버 질의하기
   4. 옵션으로 네임 서버 질의하기
   5. DNS 중 MX(Mail Record) 조회하기
   6. CNAME과 NS 레코드 조회하기
2. dig
   1. 설명
   2. 형식
   3. dig을 통해 다양한 정보 조회하기
3. host
   1. 설명
   2. 형식
   3. 주요 옵션
   4. 주요 예제

4. hostname
   1. 설명
   2. 형식
   3. 주요 옵션
   4. 주요 예제

### 3-2-5. 네트워크 응용 프로그램

1. telnet
   1. 설명: telnet 프로토콜 기반 대화형 통신을 위한 텔넷 서버에 접속
   2. 형식: `telnet [options] address`
   3. 주요 예제
      ```bash
      telnet mysite.com  # mysite.com에 텔넷 접속
      telnet 192.168.100.80  # 192.168.100.80에 텔넷 접속
      telnet -l myusername mysite.com 6666  # mysite.com에 6666 포트를 통해 텔넷 접속 수행, -l 옵션으로 사용자 계정으로 접속
      telnet  # 대화형 텔넷 접속
      ```

2. ftp
   1. 설명: 파일 전송을 위한 FTP 서버에 접속, 업로드 다운로드 가능
   2. 형식: `ftp hostname | address`
   3. 예제
      ```bash
      $ ftp 192.168.100.77  # IP 주소로 ftp 서버에 접속
      $ ftp ftp.my.com  # 호스트 이름을 통해 ftp 접속
      ```
