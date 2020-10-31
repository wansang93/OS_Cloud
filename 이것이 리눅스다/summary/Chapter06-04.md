## 06-04 하드디스크 관리-RAID용 디스크 9개 장착

### Linear RAID, RAID0, RAID1, RAID5 구현

[실습2] 하드디스크 9개 준비

실습 목표: 하드 9개를 장착하고, fdisk로 파티셔닝 한다.

1. 하드디스크 장착하기
   - Server 설정 창에서 -> `add` -> `hard disk` -> `scsi` -> `create a new` ~ ->`2, single` -> `finish` -> `Advenced`를 눌러 확인
2. Terminal 에서
   1. dev/sdb 설정하기
      ```bash
      ls -l /dev/sd*
      fdisk /dev/sdb
         n -> p -> 1 -> enter -> enter
         p -> Type이 리눅스
         l -> 83(Linux), fd(Linux raid auto)
         t -> fd
         p -> Type이 Linux and autodetect
         w
      ls -l dev/sd*
      ```
   2. dev/sdc 설정 빠르게 하기
      ```bash
      fdisk /dev/sdc
      n -> p -> 1 -> enter -> enter -> t -> fd -> w
      ```
   3. dev/sdj 까지 위와 같이 실행하기
   4. `ls -l /dev/sd*` 로 확인 후 스냅샷
