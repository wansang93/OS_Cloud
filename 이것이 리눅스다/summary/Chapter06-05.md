## 06-05 하드디스크 관리-Linear RAID 구축

### Linear RAID, RAID0, RAID1, RAID5 구현

### [실습3] Linear RAID 구축

실습 목표: Linear RAID 구축, mdadm 사용법을 익힌다.

실습 구성도

![실습구성도](./assets/06-05실습구성도.png)

1. Terminal 에서
   ```bash
   # 1. 확인하기
   ls -l /dev/sd*  # 연결된 장치들 보기
   fdisk -l /dev/sdb  # sdb 정보 보기
   fdisk -l /dev/sdc  # sdc 정보 보기
   # 2. 논리 볼륨 만들기(껍데기 설정)
   mdadm --create /dev/md9 --level=linear --raid-devices=2 /dev/sdb1 /dev/sdc1
   # create at /dev/md9, linear by 2 devices(/dev/sdb1, /dev/sdc1)
   mdadm --detail --scan  # 확인하기
   # 3. 논리 볼륨 만들기(파일 시스템 생성)
   mkfs.ext4 /dev/md9  # format 하기
   # 4. mount 하기
   mkdir /raidLinear  # make folder
   mount /dev/md9 /raidLinear/  # monut
   df  # disk free
   # 5. mount 고정하기
   vi /etc/fstab
        /dev/md9 /raidLinear ext4 defaults 0 0
        :wq
   mdadm --detail /dev/md9
   ```