# 2. 장치 관리

## 2-1. 장치의 설치 및 관리

### 2-1-1. 리눅스 커널

1. 커널의 개요
   1. 설명
   2. 버전 관리 및 배포

2. 커널의 컴파일 순서
   1. 커널 소스코드 다운로드
   2. 커널 컴파일에 필요한 필수 도구 설치
   3. 커널 환경설정
   4. 커널 컴파일

3. 그 외 커널 컴파일 명령
   1. 클린 타겟(clean targets)
   2. 커널 환경설정

### 2-1-2. 모듈(Module)

1. 모듈의 개요
   1. 정의
   2. 필요성
   3. 특징

2. 모듈 관련 명령어
   1. lsmod
   2. insmod
   3. rmmod
   4. modprobe

3. 모듈 관련 설정 파일
   1. /etc/modprobe.d
   2. modeules.dep

### 3-2. 주변 장치 관리

### 3-2-1. 디스크 확장

1. 디스크 확장의 개요
   1. ~

2. 하드디스크 추가
   1. 하드디스크 시스템에 부착
   2. 확장 파티션 생성
   3. 논리적 파티션 생성
   4. 파티션 포맷
   5. 마운트
   6. 확인
   7. /etc/fstab 파일 등록

### 3-2-2. 프린터

1. 리눅스 프린팅 시스템(Linux Printing System)의 개요
   1. ~

2. CUPS(Common Unix Printing System)
   1. CUPS의 개요
   2. CUPS의 특징

3. 프린터 추가하기
   1. 프린터 설정 방법
   2. 로컬 프린터 추가하기
   3. 네트워크 프린터 추가하기

4. 프린트 출력하기
   1. lpr(BSD)
   2. lp(System V)

5. 프린트 취소하기
   1. lprm(BSD)
   2. cancel(System V)

6. 프린트 작업 및 큐 관리하기
   1. lpc(BSD)
   2. lpq(BSD)
   3. lpstat(System V)

### 3-2-3. 사운드 카드

1. 사운드의 개요
   1. ~

2. 오픈 사운드 시스템(OSS: Open Sound System)
   1. 정의
   2. 목표
   3. OSS의 API(Application Programming Interface)
   4. 라이선스

3. 고급 리눅스 사운드 아키텍처(ALSA: Advanced Linux Sound Architecture)
   1. 정의
   2. 목표
   3. 특징
   4. 라이선스

4. 사운드 명령어
   1. alsactl
   2. alsamixer
   3. cdparanoia

### 3-2-4. 스캐너

1. SANE(Scanner Access Now Easy)
   1. 설명
   2. 아키텍처
   3. 지원 OS
   4. 오픈소스 라이선스

2. XSANE(X based interface for the SANE)
   1. 설명
   2. 기능
   3. 설치
   4. 실행

3. 스캐너 관련 명령어
   1. sane-find-scanner
   2. scanimage
   3. scanadf
   4. xcam