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
   1. 이식성
   2. 무료 소프트웨어(Free Software)
   3. 멀티 유저(Multi-User)
   4. 멀티프로그래밍(Multiprogramming)
   5. 셸(Shell)
   6. 보안(Security)

3. 리눅스의 기술적 특징
   1. 모놀리딕 커널(monolithic kernel)
   2. 장치의 파일화
   3. 다양한 파일시스템의 지원
   4. 가상메모리
   5. 스왑
   6. 동적 라이브러리와 정적 라이브러리
   7. 파이프
   8. 리다이렉션
   9. 가상 콘솔

4. 리눅스의 장단점
   1. 리눅스의 장점
   2. 리눅스의 단점

### 1-2-2. 리눅스와 GNU 그리고 오픈소스 라이선스

1. 리눅스와 GNU(GNU's not Unix)
   1. GNU GPL 라이선스(General Public Lincense)를 갖는 리눅스
   2. GNU(GNU's Not Unix)
   3. 자유 소프트웨어(free software)의 정의
   4. 카피레프트(copyleft)

2. 오픈소스(Open Source)
   1. 특징들~

3. 다양한 오픈소스 라이선스
   1. GPL(General Public License) 라이선스
   2. LGPL(Library/Lesser General Public License) 라이선스
   3. BSD(Berkley Software Distribution) 라이선스
   4. 아파치(Apache) 라이선스
   5. MPL(Mozzilla Public License) 라이선스
   6. MIT(Massachusetts Institute of Technology) 라이선스

### 1-2-3. 리눅스의 역사와 리눅스 배포판

1. 리눅스의 역사
   1. 연도 ~

2. 리눅스 배포판의 분류 및 특징
   1. 슬랙웨어
   2. 데비안
   3. 레드햇

3. 배포판 세부 설명

### 1-2-4. 리눅스의 활용 분야

1. 서버, 메인프레임
2. 스마트디바이스
3. 임베디드 디바이스
4. 게이밍 디바이스
5. 리눅스 클러스터
