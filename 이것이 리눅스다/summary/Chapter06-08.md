## 06-08 하드디스크 관리-Linear RAID, RAID0, 1, 5 원상 복구

### [실습8] RAID의 하드디스크 교체

실습 목표: Linear RAID, RAID0, RAID1, RAID5 의 장치의 고장 난 하드디스크를 새로운 하드디스크로 교체한다.

복구 전후의 내부적 변화

![06-08 실습구성도](assets/06-08실습구성도.png)

1. Server virtual machine settings
   - `Add` -> `SCSI` -> `Next` -> `1G, Single File` -> `Finish`
   - 4가지 모두 설정 후 부팅

2. Terminal 에서
   ```bash
   mdadm --detail /dev/md1
   # fdisk 로 파티셔닝을 해줘야 함
   fdisk /dev/sdc
        n -> p -> 1 -> enter -> enter -> t -> fd -> w
   fdisk /dev/sde
        n -> p -> 1 -> enter -> enter -> t -> fd -> w
   fdisk /dev/sdg
        n -> p -> 1 -> enter -> enter -> t -> fd -> w
   fdisk /dev/sdi
        n -> p -> 1 -> enter -> enter -> t -> fd -> w
   ls -l dev/sd*  # 파티셔닝 확인하기
   # 작동이 안됬기 때문에 중지 후 다시만들기
   mdadm --stop /dev/md9
   mdadm --create /dev/md9 --level=linear --raid-devices=2 /dev/sdb1 /dev/sdc1
        y
   mdadm --stop /dev/md0
   mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdd1 /dev/sde1
        y
   mdadm --detail /dev/md9
   mdadm --detail /dev/md0
   
   # 작동이 된 RAID1, RAID5는 add만 하면 저절로 작동이 됨
   mdadm /dev/md1 --add /dev/sdg1
   mdadm /dev/md5 --add /dev/sdi1

   mdadm --detail /dev/md1
   mdadm --detail /dev/md5

   vi etc/fstab
        주석처리 지우고 다시 시작
   
   # 재부팅 후 잘 작동하는지 확인하기
   reboot
   ls -l /raid0  # 50%만 남아있는 파일
   ls -l /raidLinear  # 저장 방식상 파일이 살아있음
   ```
