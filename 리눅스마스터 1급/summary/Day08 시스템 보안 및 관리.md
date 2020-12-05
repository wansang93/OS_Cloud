# 3. 시스템 보안 및 관리

## 3-1. 시스템 분석

### 3-1-1. 시스템 로그 개요 및 분석

1. 시스템 로그의 개요
   1. 설명
   2. 로그 확인하기

2. 주요 시스템 로그 파일
   1. ~

3. 시스템 로그 파일 명령어
   1. dmesg
   2. lastlog
   3. last
   4. lastb

### 3-1-2. 시스템 로그 관리

1. 시스템 로그 관리 개요
   1. 시스템 로그의 생성 및 관리
   2. syslog
   3. rsyslog

2. rsyslog를 통한 로그 관리
   1. rsyslog(the rocket-fast system for log processing)설정 및 시작
   2. rsyslog 관련 파일
   3. /etc/rsyslog.conf 파일

3. 로테이션을 통한 로그 용량 관리
   1. logrotate 명령어 설명
   2. logrotate 환경설정하기
   3. 로테이션 이력 확인하기

## 3-2. 시스템 보안 및 관리

### 3-2-1. 시스템 보안 관리

1. 리눅스 보안의 소개
   1. ~

2. 물리적 보안
   1. 물리적 보안의 설명
   2. 물리적 보안 방안

3. 시스템 보안
   1. BIOS 보안
   2. 패스워드 보안
   3. 관리자 계정 보안

4. 서비스 및 운영 보안
   1. 필수 서비스만 사용
   2. 시스템 정보 숨김
   3. 부트로더 패스워드 설정
   4. 보안 서비스 사용

5. 파일 시스템 보안
   1. 소유권과 허가권
   2. lsattr
   3. chattr
   4. getfacl
   5. setfacl

6. 네트워크 보안
   1. sysctl을 통한 보안 강화

### 3-2-2. SELinux(Security-Enhanced Linux)

1. SELinux의 개요
   1. SELinux의 필요성
   2. SELinux의 정의
   3. SELinux의 특징

2. SELinux의 설정 및 해제
   1. SELinux의 동작 모드
   2. SELinux의 모드 확인

### 3-2-3. 시스템 보안 유틸리티

1. ssh(Secure Shell)
   1. ssh의 정의
   2. ssh 연결 준비사항
   3. ssh 서버의 설치
   4. 비밀번호 인증을 통한 ssh 서버 접속
   5. 인증키를 통한 ssh 자동 접속
   6. sshd 환경설정

2. PAM(Pluggable Authentication Module)
   1. PAM 설명
   2. PAM 환경설정하기


3. PAM 환경 설정 샘플
   1. PAM 환경설정 샘플
   2. PAM 환경설정 샘플 설명

4. sudo(Super User DO)
   1. sudo 설명
   2. /etc/sudoers 파일 편집하기
   3. sudo 명령어 사용하기

### 3-2-4. 주요 보안 도구

1. nmap(Network Mapper)
   1. 설명
   2. 동작 원리
   3. nmap의 설치
   4. 사용 예시

2. tcpdump
   1. 설명
   2. 주요 예제

3. tripwire
   1. 설명
   2. tripwire의 설치
   3. tripwire의 실행

4. Nessus
   1. 설명
   2. 특징
   3. Nessus 설치

5. GnuPG(GNU Privacy Guard)
   1. 설명
   2. 공개키 기반 암호화(public-key based encryption, decription)
   3. 디지털 서명(digital signature)

6. John The Ripper
   1. 설명

## 3-3. 시스템 백업

### 3-3-1. 백업의 개요

1. 백업의 필요성
   1. 비지니스 연속성
   2. 데이터의 중요성
   3. 시스템의 장애 발생 위험

2. 백업 전략의 요건

3. 백업 전략 수집 시 고려사항
   1. 무엇을 백업할 것인가?
   2. 어디에 백업할 것인가?
   3. 언제 백업할 것인가?
   4. 적용할 백업 유형은 무엇인가?
   5. 백업의 압축과 암호화를 할 것인가?
   6. 백업을 어떻게 검증할 것인가?
   7. 백업 유틸리티 및 서비스

### 3-3-2. 파일 백업

1. tar
   1. 설명
   2. 전체 백업(full backup)
   3. 증분 백업(incremental backup)

2. cpio

### 3-3-3. 파일시스템 및 디스크 백업

1. dump
   1. 형식
   2. 옵션
   3. 주요 예제

2. dd
   1. 형식
   2. 옵션
   3. 주요 예제

3. restore
   1. 형식
   2. 옵션
   3. 주요 예제

### 3-3-4. 네트워크 백업

1. rsync
   1. 형식
   2. 옵션
   3. 주요 예제
