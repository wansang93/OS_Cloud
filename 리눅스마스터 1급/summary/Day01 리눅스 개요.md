# 1. 리눅스의 개요

## 1-1. 운영체제의 개요

### 1-1-1. 운영체제의 정의 및 목적, 역할

1. 운영체제의 정의
   1. user interface 제공, 시스템 소프트웨어
   2. CPU(Central Processing Unit), 메모리, 하드웨어 등을 관리
   3. 프로그래밍 인터페이스 제공

2. 목적
   1. **처리능력**(Throught) 항상
   2. **처리 응답 시간**(Turnaround Time) 최소화
   3. **신뢰도**(Reliability) 향상
   4. **사용 가능도**(Availability) 향상

3. 역할
   1. 하드웨어 제어, 입력, 출력 등을 관리
   2. 하드웨어를 다수의 이용자가 공유
   3. 프로세스, 메모리, CPU 등 효율적 사용을 위한 자원 스케줄링
   4. 시스템 호출(system call)
   5. 오류 복구
   6. 데이터 조직화, 파일 관리, DB 기능, 원격 네트워크 기능 제공
   7. 사용자 인터페이스 제공

### 1-1-2. 운영체제의 구조와 기능

1. 운영체제의 구조
   1. 응용 프로그램, GUI, 배치 작업(batch jobs), 셸(shell) 등을 통한 운영체제의 기능 사용
   2. 응용 프로그램은 시스템 호출을 통해 커널 서비스 이용
   3. 다양한 하드웨어에 대한 이식성 향상 -> 추상 계층(HAL: Hardware Abstraction Layer) 제공
2. 기능
   1. **리소스 관리**: 프로세스, 메모리, 장치I/O, 파일시스템 등
   2. **자원 스케줄링**: 자원의 효율적인 사용을 위해
   3. **하드웨어의 관리**: LAN 카드, USB 장치, 디스크 등
   4. **네트워크 제어**: 네트워크 생성, 주소 할당, 경로 설정
   5. **자원 보호**: 사용자, 프로세스, 네트워크 같은 자원에 무분별한 접근 방지
   6. **오류 검사 및 복구**: 디스크 및 파일시스템과 같은 시스템 손상 점검, 복구 기능 제공
   7. **가상화**: 자원의 유휴 시간 최소화를 위해 가상의 컴퓨터를 여러 대 실행할 수 있는 기능

### 1-1-3. 운영체제의 운용 기법

1. 운영체제 운용 기법의 종류
   1. 일괄 처리 시스템(Batch Processing System)
      1. 초기 운영체제, 여러 작업을 묶어 한번에 처리
      2. 실행 시 기다려야 함, 자원 효율성x
      3. 입출력 중 CPU는 유휴 상태(idle), 즉 멈춰 있음
   2. 다중 프로그래밍 시스템(Multi Programming System)
      1. 일괄 처리 시스템 보완
      2. 유휴 상태에 다른 작업 할당, CPU 사용율, 처리량 향상
      3. 하나의 CPU에 동시에 여러 프로그램 실행되는 것 처럼 보임
      4. 작업 단위로 CPU 스케줄링을 수행
   3. 시분할 시스템(Time Sharing System)
      1. 타임 슬라이스(time slice) 또는 타임 퀀텀(time quantum)인 일정 작업 시간 동안 작업 실행, 시간이 만료시 대기 큐에서 다음 작업을 실행
      2. 반응 시간(response time) 단축
      3. 다중 프로그래밍 시스템보다 CPU 사용율, 처리량 향상,더욱더 여러 작업 실행되는 것으로 보임
      4. 멀티유저 지원
   4. 다중 처리 시스템(Multi-Processing System)
      1. 여러개의 CPU를 통해 동시에 여러 개의 작업을 처리
      2. 병렬 처리 시스템(Parallel Processing System) 이라고도 불림
      3. 비대칭적 다중 처리(Asymmetric Multi-processing)
         - 프로세스 간 주종 관계, 주 프로세스에 따라 종 프로세스가 작업을 처리
      4. 대칭적 다중 처리(Symmetric Multi-processing)
         - SMP(Symmetric Multi-Processing)와 MPP(Massively Parallel Processing)
   5. 실시간 처리 시스템(Real Time Processing System)
      1. 경성과 연성 실시간 처리 시스템(Hard / Soft real time processing system)으로 나뉨
         1. 경성 실시간 처리 시스템 -> 제한된 시간 안에 반드시 작업 처리 완료, 무기 제어 등
         2. 연성 실시간 처리 시스템 -> 시스템에 큰 영향을 미치지 않는 시스템, 동영상 제어 등
   6. 다중 모드 시스템(Multi-Mode System)
      1. 위의 기능을 모두 혼용하여 사용할 수 있는 운용 시스템
   7. 분산 처리 시스템(Distribute Processing System)
      1. 독립적인 처리 능력 시스템을 통신망으로 연결한 시스템
      2. 자원 공유, 연산속도 향상, 신뢰도 향상, 통신 가능
      3. 물리적 시스템 간 연결을 넘어 유휴 자원의 효율적 활용을 위해 가상화 기술을 Kernel 단에서 지원, 가상화 시스템과 물리적 시스템 간의 분산 처리 형태로 진화
      4. 강결합(Tightly-Coupled) 방식이 아님: 운영체제 하나, 여러개 프로세서가 하나의 메모리를 공유나는 방식
      5. 약결합(Loosely Coupled) 방식: 둘 이상의 독립된 시스템이 통신으로 연결, 상호작용

2. 운영체제 운영기법의 발전
   1. 1세대: 일괄 처리
   2. 2세대: 다중 프로그래밍, 다중 처리 시스템
   3. 3세대: 시분할 시스템
   4. 4세대: 다중 모드 시스템
   5. 5세대: 분산 처리 시스템

- 한번에 하나의 작업 처리 -> 지역적 분산된 여러 시스템이 동시에 여러 작업을 처리

### 1-1-4. 운영체제의 사례

1. 데스크톱 및 서버 운영체제
   1. 윈도우(Windows)
      - Bill Gates & Paul Allen 의 MS에서 제작
      - Windows 10의 모체가 되는 운영체제는 NT 커널 탑제, Windows NT 3.1
   2. MacOS
      - Steve Jobs % Steve Wozeniak 의 애플에서 제작
      - 유닉스/다윈 기반 Mac 전용 OS
   3. Linux
      - Linus B. Torvalds 가 유닉스에 호환되는 운영체제를 개발
      - GNU 프로젝트는 리눅스 커널에서 동작 가능한 어플 개발, 패키지로 묶은 리눅스 배포판이 출시
   4. UNIX
      - Ken Tompson & Dennis Ritchie가 AT&T의 벨 연구소에서 제작
      - C언어로 개발, 이식 용이, 명령행 인터프리터, 계층적 파일시스템, 장치와 프로세스 간 통신을 파일을 매개체로 수행
      - System V 계열, BSD 계열 존재

2. 모바일 및 임베디드 운영체제
   1. 안드로이드(Android)
      - 리눅스 커널 기반, 안드로이드 런타임 위에 어플리케이션 프레임워크를 사용하는 어플리케이션으로 구성
      - 무료 공개 후 오픈 핸드셋 얼라이언스(OHA: Open Handset Alliance)에서 공개 표준을 위해 개발중
   2. IOS, watchOS, iPadOS, tvOS
   3. Tizen
      - Intel & Samsung 주도 MeeGo 개발자 합류, 리눅스 기반 오픈소스 모바일, 웨어러블, IVI(In-Vehicle Infotainment)
   4. Embedded Linux
      - raspbian: 라즈베리 파이 재단에서 만든 데비안 리눅스 기반 OS
      - webOS: Palm, LG전자에서 개발 중인 IoT용 운영체제
      - IVI: MS의 Windows Embedded Automotive, QNX, GENIVI, Google의 Android Auto, Apple의 Carplay 같은 OS 존재

3. IOT 운영체제
   1. Linux
      - Android Things: 안드로이드 기반 IoT 플랫폼
      - Ubuntu Core: 보안성 강화, 가볍고 안정적, 우분투 최적화
   2. Windows IoT
      - Window 임베디드 운영체제를 IoT에 맞게 최적화
   3. RTOS(Real Time OS)
      - FreeRTOS: 소형 저출력 엣지 디바잉스를 관리, Micro controller용 OS
      - VxWorks: 윈드리버 시스템 사가 만들어 판매하는 실시간 운영체제
      - QNX: 임베디드 시장에서 주로 사용, 유닉스 기반, 블랙베리 및 자동차 산업에 탑재
   4. 경량 OS
      - Contiki: BSD(Berkeley Software Distribution) 라이선스, 오픈소스 네트워크 OS, 스마트 도시에 여러 시설에 적용
      - TinyOS: UC Berkeley에서 개발한 센서 네트워크형 free OS
      - RIOT: 실시간 OS, 8, 16, 32bit 플랫폼을 타깃

## 1-2. 리눅스 기초

### 1-2-1. 리눅스 개요

1. 정의 및 의미
   1. 정의: 각종 Device를 위한 유닉스 호환 운영체제
   2. 의미
      - Linux: 리누스 토발즈에 의해 개발, 초기에는 리눅스 커널만 의미했음
      - GNU/Linux: GNU 프로젝트를 통해 리눅스 커널 기반으로 어플 및 라이브러리를 추가, 리눅스 배포판 개발

2. 리눅스의 일반적인 특징
   1. 이식성 높음
      - C언어로 작성, 플랫폼에 종속적인 부분만 어셈플리어로 작성 때문
   2. 자유 소프트웨어(Free Software)
      - GPL, LGPL 라이선스를 따름, contribution을 통해 진화
   3. 멀티 유저(Multi-User)
      - 다수의 사용자가 한 시스템의 다양한 자원에 접근, 사용 가능
   4. 멀티프로그래밍(Multiprogramming)
      - 프로그램을 메모리에 적재, 동시 실행 가능
   5. 계층적 파일시스템(Hierarchical File System)
      - /(root) -> `/boot` `/home` `/dev` `/usr` `/var` `/sbin` `/etc/` `mnt` `/tmp` 구조
   6. 셸(Shell)
      - 명령어 해석, 프로그래밍, 환경 설정 기능 제공
   7. 보안(Security)
      - 유닉스 보안 모델을 이어 받은 임의접근제어 제공, 이를 향상한 확장 임의접근제어(Extended DAC)
      - 임의접근제어(Discretionary Access Control): 주체마다 객체에 대한 접근 정책 설정
      - 네트워크 정책에 따라 노드나 라우터로 동작 가능
      - 네트워크 인터페이스에서 발생한 트레픽을 서버로 안전하게 전달 가능: netfilter, iptables, ebtables, arptables 제공
      - 네트워크 스택은 IPSec 제공, IP 통신시 안전하게 데이터 송수신 가능
      - SELinux(Security Enhanced Linux) 존재: 강제접근제어(Mandatory Access Control)를 강화

3. 리눅스의 기술적 특징
   1. 모놀리딕 커널(monolithic kernel)
      - 운영체제가 제공하는 서비스를 하나의 커널로 구현하여 제공
      - 운영체제의 기능이 단일 커널로 제공, 해결하려면 커널을 다시 컴파일
      - 기본은 모놀리딕 커널이지만 동적 로드가 가능한 커널 모듈과 프로퍼티 기능 제공
   2. 장치의 파일화
      - 시스템 자원을 모두 파일로 다룸
      - 문자 장치 파일(터미널 등), 블록 장치 파일(디스크 등)로 나뉨
      - 파일 -> 디렉터리, 일반 파일, 특수 파일로 나뉨
      - 특수파일 -> 장치파일, 파이프, 소켓 등으로 나뉨
      - 파이프 파일 -> 프로세스간 통신을 위해
      - 소켓 파일 -> 응용 프로그램이 소켓 프로그래밍이 가능하도록 지원
   3. 다양한 파일시스템의 지원
      - ext2, ext3, ext4의 자체 파일시스템 제공
      - 윈도우용 파일시스템(FAT32, NTFS), 네트워크용 파일시스템(SMB, CIFS)
      - 저널링 파일시스템(journaling file system) 지원
   4. 가상메모리
      - 메모리 관리 기법: 물리적 메모리 크기 극복
      - 프로세스들이 접근하는 메모리 -> 가상 메모리에 매핑 -> 가상 메모리의 페이지를 통해 -> 물리 메모리에 매핑
      - 요구 페이징(Demand Paging): 동작 중인 프로세스가 사용하는 메모리만을 물리 메모리에 로드, 사용 빈도가 낮은 메모리는 디스크에 저장
      - 넓은 주소 공간
      - 페이지에 대한 보호 매커니즘
      - 이미지와 데이터 파일을 프로세스의 주소 공간에 매핑하는 메모리 매핑
      - 프로세스 간 공유 메모리 기능 제공
   5. 스왑
      - 물리 메모리가 가득 차 메모리에 로드할 수 없는 경우, 실행 빈도가 낮은 것을 디스크로 옮기고 메모리를 확보
      - 스왑아웃(swap out): 메모리 -> 디스크
      - 스왑 인(swap in): 디스크 -> 메모리
      - 스왑 파티션(swap partition): 디스크 상에 특별한 공간을 만들어야 함, 동적 스왑크기 조절 불가, 하드디스크 공간 차지
      - 최대 절전 기능때: 스왑 파티션 필요, 메모리의 휘발성 때문, 이동 저장
      - 스왑 빈도를 변경 `/etc/sysctl.conf` -> `vm.swapiness` 설정, 만약 10으로 설정하면 메모리 가용량 10%일 때 스왑 시도
      - `free` 명령어: 스왑 영역 용량, 메모리의 상태 확인
   6. 동적 라이브러리와 정적 라이브러리
      - 동적 라이브러리: 메모리에 한 번 적재, 여러 프로세스가 매번 동일한 라이브러리 로드하기 방지, 공용 사용, 효율적, 실행 속도 느림, 배포에 제약
      - 정적 라이브러리: 실행 프로그램 컴파일 시 링크, 정적 라이브러리도 함께 매번 메모리에 로드, 단일 사용, 비효율적, 실행 속도 빠름, 배포에 제약 존재
   7. 파이프
      - 프로세스간 통신하기 위한 연결 통로
   8. 리다이렉션
      - 표준 입출력 재지정
   9. 가상 콘솔
      - 하나의 화면에서 여러개 콘솔 사용 가능

4. 리눅스의 장단점
   1. 리눅스의 장점
      - 오픈소스, 안정성이 점점 올라감, 네트워크 프로토콜 지원, 커스터마이징 가능
   2. 리눅스의 단점
      - 체계적 아님, 상용 소프트웨어 부족, 드라이버 지원이 느림

### 1-2-2. 리눅스와 GNU 그리고 오픈소스 라이선스

1. 리눅스와 GNU(GNU's not Unix)
   1. GNU GPL 라이선스(General Public Lincense)를 갖는 리눅스
      - GNU GPL 라이선스: 자유롭게 사용, 변경, 배포 가능
      - GPL은 GPL 라이선스로 만든 해당 소스도 GPL 라이선스로 배포되어야 한다는 제약
   2. GNU(GNU's Not Unix)
      - GUN는 유닉스와 호환, 유닉스는 아니다 이중적 의미
      - 응용 프로그램 개발: GNU C 컴파일러(gcc), 문서편집기(emacs), X 윈도우(GNOME), 파일압축(tar), 셸(bash), 부트매니저(Grub) 등
   3. 자유 소프트웨어(free software)의 정의
      - 자유0: 어떠한 목적을 위해 실행할 자유
      - 자유1: 작동 원리 연구, 수정 가능한 자유
      - 자유2: 복제, 배포할 자유
      - 자유3: 프로그램 향상 할 자유
   4. 카피레프트(copyleft)
      - 저작권(Copyright)의 반댓말
      - 자유롭게 사용할 수 있도록 법률적 보장, GNU GPL 라이선스가 대표적

2. 오픈소스(Open Source)
   1. 넷스케이프 소스코드를 어떤 형태로 공개할까 논의 중 처음 쓰인 단어
   2. 오픈소스이니셔티브(OSI: Open Source Initiative) 설립 해 오픈소스 장려
   3. 저작자 권리를 지키며 원시 코드를 누구나 열람
   4. free software와의 차이점: 오픈소스는 용어의 의미가 강함, 자유 소프트웨어는 모든 소프트웨어는 자유롭게 사용 가능
   5. 오픈소스 이니셔티브에 등록되기 위한 10가지 조건
      - Free Redistribution
      - Source Code Open
      - Derived Works
      - Integrity of The Author's Source Code
      - No Discrimination Against Persons or Groups
      - No Discrimination Against Fields of Endeavor
      - Distributioin of License
      - License must not be specific to a product
      - License must not contaminate other software
      - License must be Technology-Neutral

3. 다양한 오픈소스 라이선스
   1. GPL(General Public License) 라이선스
      - 실행, 연구, 공유, 수정의 자유
      - GPLv1: 바이너리 형태의 프로그램을 배포할 때 소스코드를 함께 배포
      - GPLv2: 특허 보호
      - GPLv3: 특허 대처, 다른 라이선스와의 호환성, 원시 코드의 구성법, 디지털권리관리 관련 내용 추가
      - GPL 라이선스의 5가지 의무
        - 어떠한 목적으로도 실행 가능, 법의 제한을 제외한
        - 소스코드와 함께 판매, 소스코드를 무료 배포
        - 소스코드를 용도에 따라 변경 가능
        - 변경된 프로그램 또한 소스코드 공개 배포
        - 변경된 프로그램 또한 똑같은 라이선스(GPL)로 취해야 함
   2. LGPL(Library/Lesser General Public License) 라이선스
      - GPL이 강해 보안책으로 만든 라이선스
      - LGPL 프로그램 자체는 카피레프트 적용, 이 프로그램을 이용하는 프로그램은 적용x
      - 정적, 동적으로 링크하는 경우 소스코드 공개 필요x
      - LGPL 프로그램 자체를 수정시 수정한 LGPL 코드 공개
      - LGPL -> GPL 라이선스로 바꾸기 가능, 반대는 불가능
   3. BSD(Berkley Software Distribution) 라이선스
      - Berkley Uni에서 배포한 라이선스
      - BSD 라이선스 및 저작권 명시
      - 수정본 재배포의 의무x, 소스코드 비공개 가능
      - 상용 소프트웨어에서 BSD 라이선스를 갖는 프로그램 이용도 소스코드 공개x
   4. 아파치(Apache) 라이선스
      - Apache 소프트웨어 재단에서 만든 라이선스
      - Apache 라이선스 및 저작권 명시, 변경사항 안내
      - 상업적 이용o, 배포o, 수정o, 배포o, 특허 신청o, 사적 이용o, 2차 라이선스o, 보증책임x
   5. MPL(Mozzilla Public License) 라이선스
      - BSD + GPL 성격
      - 미첼 베이커 + 모질라 재단이 작성
      - 수정 시 수정한 소스코드 공개, 혼합하여 코드 개발시 공개필요x
      - 파이어폭스 등에 적용
   6. MIT(Massachusetts Institute of Technology) 라이선스
      - MIT Uni. 에서 작성, X11, X 라이선스라고 불리기도 함
      - 카피레프트가 아니며 오픈소스 여부와 관계없이 재사용 허용

### 1-2-3. 리눅스의 역사와 리눅스 배포판

1. 리눅스의 역사
   1. 1984 ~ 1991: 리차드 스톨만의 자유 소프트웨어 운동 시작
   2. 1991 ~ 1993: 리누스 토발즈의 리눅스 커널 및 배포판 출시
   3. 1994: 리눅스 커널 정식 1/0 출시
   4. 1998: 오픈소스 소프트웨어의 태동
   5. 2003~2005: 다양한 배포판의 보급
   6. 2007: GPLv3의 발표 GPL 라이선스 완성
   7. 2011~: 리눅스 커널 지속적인 발전

2. 리눅스 배포판의 분류 및 특징
   1. 레드햇: 고객 유료 서비스를 통한 수익 창출 추구, 일반 사용자를 위한 무료 배포판
   2. 데비안: 기업, 재단보다 자발적 커뮤니티에 의한 배포판, APT 패키지 관리자를 통한 패키지 설치 및 업그레이드의 편리함
   3. 슬랙웨어: 가장 오래된 배포판, 유닉스다운 리눅스 배포판

3. 배포판 세부 설명
   1. 레드햇 계열
      - RHEL(RedHat Enterprise Linux): 페도라를 기반으로 레드햇에서 개발한 리눅스 배포판, 유로 라이선스로 제공, 기술지원 제공
      - Fedora: 레드햇과 페도라  커뮤니티의 지원, RPM 기반의 소프트웨어가 결합된 리눅스 배포판(MeeGo, SailFish OS, Tizen)
      - CentOS(Community ENTerprise OS): RHEL을 완벽하게 호환하여 무료 기업용 컴퓨팅 플랫폼 제공 목적
      - Oracle Linux: GPL 라이선스에 따라 레드햇 소스코드를 공유하면서 오라클의 어플라이언스에 최적화된 리눅스 배포판
      - Scientific Linux: 상용 기업형 배포판에 근접하도록 만들기 위한 목적, 페르미 국립 가속기 연구소가 개발한 리눅스 배포판
   2. 데비안 계열
      - 우분투: Canonical Ltd에서 개발한 리눅스 배포판, 전세계 누구나 리눅스를 쉽게 사용하자는 미션
      - Raspbian: 라이즈베리파이 제단에 의해 공식 지원받는 라즈베리파이 전용 리눅스
      - ChromeOS: 사용자가 브라우저를 이용하여 인터넷을 탐색한다는 점에 착안, 개발한 리눅스 기반 운영체제
   3. 슬랙웨어 계열
      - Slackware: 대중화된 현존하는 가장 오래된 배포판, 간결함 설계, 유닉스 자체 학습에 적합
      - openSUSE: Slackware 에서 파생, 유럽에서 많이 사용, SUSE Linux Enterprise(유료)와 openSUSE(무료) 두 가지 배포
      - Vector Linux: SOHO, Standard, Light, Live판을 갖는 슬랙웨어 게열 리눅스 운영체제
   4. 안드로이드 계열
      - 안드로이드: 리눅스 커널 기반으로 안드로이드 런타임 실행, 풍부한 런타임 라이브러리 제공
      - AOSP(Android Open Source Project): 소스코드는 AOSP를 통해 운영, 안드로이드를 포팅 및 커스터마이징 가능
   5. 국내 계열
      - 하모니카: 정부 주도로 개발한 리눅스 민트 기반 개방형 운영체제, 한글화가 좋음
      - 넘버원 리눅스: PCLinux 기반 KDE 환경을 제공하는 독자적인 토종 리눅스
      - 구름OS: 한글과 컴퓨터와 국가기관이 개발한 개방형 OS

### 1-2-4. 리눅스의 활용 분야

1. 서버, 메인프레임
   1. 웹 서버를 호스팅하는 대부분 서버들은 리눅스
   2. 메인프레임에서도 낮은 비용, 오픈소스 모델에 힘입어 리눅스 배포판의 채용 꾸준히 증가
   3. 대부분의 슈퍼컴퓨터도 리눅스를 사용
2. 스마트 디바이스
   1. 스마트폰, 태블릿 PC, 스마트 TV, IVI 시스템에 리눅스 탑재
   2. 안드로이드는 리눅스 커널 기반
   3. Parm Pre 스마트폰용으로 개발되었던 webOS 또한 리눅스 기반
   4. 모질라의 FireFoxOS도 하드웨어 추상계층과 웹표준 기반 런타임 환경과 사용자 인터페이스를 웹 브라우저와 통합한 리눅스 기반 운영체제
3. 임베디드 디바이스
   1. 임베디드 시스템은 하드웨어 제어를 통해 특정 기능 수행, 컴퓨터 시스템 내에 존재하는 전자 시스템
   2. 임베디드는 2가지 시스템이 있음, 운영체제 포함x, 펌웨어만으로 동작하는 시스템 / 운영체제를 통해 구동하는 시스템
   3. 이런 운영체제는 주로 리눅스 커널을 포팅, 특수 기능을 수행하는 응용 프로그램을 개발하여 디바이스를 완성
   4. 소형 임베디드 시스템은 IoT 분야에 활용, Android Things, Ubuntu Core 등이 예
   5. 교육용 목적 오픈소스 하드웨어가 널리 보급, 데비안 기반 라즈비안이 라즈베리파이를 위한 운영제제로 사용
4. 게이밍 디바이스
   1. 밸브 사는 스팀 리눅스 버전출시, 리눅스 데스크톱에 게임 엔진을 포팅, VOGL, OpenGL 개발
   2. 밸브 사는 DirectX 11, 12를 구현 스팀 시스템과 통합하는 등 바닐라 와인 기능 개선한 Proton을 출시
   3. 엔비디아(NVIDIA)는 안드로이드 기반 게임플랫폼 Shield를 출시
5. 리눅스 클러스터
   1. 고 계산용 클러스트(HPC: High Performance Cluster)
      - 과학 계산용, 큰 계산을 위해 여러 대를 묶어 효율성 높이는 기술, 리눅스 사용
   2. 부하분산 클러스터(LVS: Linux Virtual Server)
      - 로드 밸런서(Load Balancer)를 운영, 대규모 트래픽을 여러 대의 서버로 분산하는 기술
   3. 고가용 클러스터(High Availability Cluster)
      - 중요한 것은 고가용성 클러스터로 구축
      - 부하 분산 클러스터와 혼합, 주 노드(Primary Node)가 부하 분산 처리를 수행, 부 노드(Backup Node)가 주 노드 상태를 체크, 이상시 서비스를 이어받아 서비스를 지속
      - 이중화 기술이라고 하고 다운로드로 인한 장애 시간을 zero로 만드는 것이 목표
