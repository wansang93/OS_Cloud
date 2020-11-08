## 06-11 하드디스크 관리-CentOS를 RAID에 설치

### RAID에 CentOS 설치하기

운영체제의 디스크가 고장나도 백업형태로 다른 디스크에 있는 운영체제를 불러 올 수 있다.

### [실습12] RAID1에 CentOS 설치

실습 목표: 2개의 80GB 하드디스크에서 RAID 1으로 안전하게 작동되는 CentOS를 새로 설치한다.

1. `Create a New Virtual Machine`

   `I will install ~` -> `Linux`, `Red Hat ~ Linux 8 ~` -> `Next` -> `Next` -> `Finish`
2. `Edit virtual Machine settings`
   1. `Add` -> `Hard disk` -> `SCSI` -> `80G`, `single` -> `Finish`
   2. `Add` -> `Hard disk` -> `SCSI` -> `80G`, `single` -> `Finish`
   3. 기존 하드디스크 `Remove`
   4. Centos 설치 파일 이미지 넣기
3. `Play ~`로 가상머신 설치 시작
   1. 한국어로 설치
   2. `시스템`에서 `설치 목적지` 클릭
      1. 하드디스크 두개 클릭 -> `custom`
      2. LVM -> `표준 파티션`
      3. `swap` -> `4G` -> `추가`, 장치유형 RAID -> RAID1 -> 설정 업데이트
      4. `+` -> `/` -> `추가`, 장치유형 RAID -> RAID1 -> 설정 업데이트
      5. `완료` -> `변경사항 저장`
4. 다 설치 후 Terminal에서
   ```bash
   mdadm --detail --scan
   # swap 파티션과 root 파티션이 두개 작동하는 것을 확인
   mdadm --detail /dev/md/root  # 작동 확인하기
   ```

5. 시스템 종료 후 디스크 하나 삭제 후
6. 다시 접속 후 Terminal에서 상황보기
   ```bash
   mdadm --detail /dev/md/root  # 작동 확인하기
   # 하나만 작동하는 것을 확인 가능
   ```
