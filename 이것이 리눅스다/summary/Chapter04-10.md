## 04-10 필수 개념과 명령어-시스템 설정, CRON과 AT

### 시스템 설정

시간: 설정 -> 자세히 보기 -> 날짜 및 시간 -> 표준 시간대 자동
방화벽: ```firewall-config```
서비스 켜기/끄기: ```ntsysv```

### CRON과 AT

1. cron
   - 주기적으로 반복되는 일을 자동적으로 실행될 수 있도록 설정
   - 관련된 데몬은 crond, 관련 파일은 ```/etc/crontab```
   - ```/etc/crontab``` 예시 -> 실습시간에 자세히
     -  min(0~9), hour(0~23), day of month(1-31), month(1~12 or jan, feb, mar, ...), day of week(sun(0, 7), mon(1), tue(2), ...)
     - 01 **** root run-parts/etc/cron.hourly
     - 02 4*** root run-parts/etc/cron.daily
     - 03 4**0 root run-parts/etc/cron.weekly
     - 42 41** root run-parts/etc/cron.monthly

2. at
   - at은 일회성 작업을 예약

[실습13] cron, at 실습

1. cron을 활용 매월 15일 새벽 3시 1분에 /home과 그 하위 디렉토리를 /backup 디렉토리에 백업하는 방법을 익힌다.
2. at 사용법을 익힌다.

``` bash
# 1. cron
wget http://download.hanbit.co.kr/centos/8/openrdate-1.2-14.fc30.x86_64.rpm  #  시간설정rpm 파일 다운로드(시간을 바꿔 업데이트 됬는지 확인)
dnf -y install openrdate-1.2-14.fc30.x86_64.rpm  # rpm 파일로 다운로드
systemctl status crond  # crond 작동 확인
systemctl start crond  # crond 작동이 안될 경우 시작
vi /etc/crontab
    01 3  15 *  *  root      run-parts  /etc/cron.monthly
:wq
cd  /etc/cron.monthly/  # 다달이 실행할 디렉토리 들어가기
vi  myBackup.sh  # 스크립트 파일 만들기
    #!/bin/sh

    set $(date)
    fname="backup-$2$3tar.xz"

    tar  cfJ  /backup/$fname  /home
:wq
chmod 755 myBackup.sh  # 실행권한 주기
mkdir  /backup  # 저장할 디렉토리 생성
systemctl  restart  crond  # crond 재시작
date  011503002027  # 1월15일03시00분2027년 시간설정
# 1분 기다린 후
date  # 현재 시간 보기
ls -l /backup/  # 백업 폴더 확인
date  021503002027  # 2월 15일 03시00분2027년 시간설정
rdate -s time.bora.net  # 시간 표준시간대로 변경

# 2. at
at 4.00am tomorrow  # 내일 4시에 at 만들기
    dnf -y update  # dnf update
    reboot
    Ctrl + D  # 빠져나오기
at -l  #  at 목록보기
atrm  1  # 1번 삭제하기
```
