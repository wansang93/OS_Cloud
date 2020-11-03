## 06-06 하드디스크 관리-RAID 0, 1, 5 구축

### [실습4] RAID0 구축

Linear RAID 구축과 비슷함, 옵션만 변경하면 사실상 같음

1. Terminal 에서
   ```bash
   # 1. 확인하기
   ls -l /dev/sd*  # 연결된 장치들 보기
   fdisk -l /dev/sdd  # sdd 정보 보기
   fdisk -l /dev/sde  # sde 정보 보기
   # 2. 논리 볼륨 만들기(껍데기 설정)
   mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdd1 /dev/sde1
   # create at /dev/md0, RAID0 by 2 devices(/dev/sdd1, /dev/sde1)
   mdadm --detail --scan  # 확인하기
   # 3. 논리 볼륨 만들기(파일 시스템 생성)
   mkfs.ext4 /dev/md0  # format 하기
   # 4. mount 하기
   mkdir /raid0  # make folder
   mount /dev/md0 /raid0/  # monut
   df  # disk free
   # 5. mount 고정하기
   vi /etc/fstab
        /dev/md0 /raid0 ext4 defaults 0 0
        :wq
   mdadm --detail /dev/md0
   ```

### [실습5] RAID1 구축

Linear RAID 구축과 비슷함, 옵션만 변경하면 사실상 같음

1. Terminal 에서
   ```bash
   mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdf1 /dev/sdg1
   y
   mkfs.ext4 /dev/md1
   mkdir /raid1
   mount /dev/md1 /raid1/
   df
   vi /etc/fstab
        /dev/md1 /raid1 ext4 defaults 0 0
        :wq
   mdadm --detail /dev/md1
   ```

### [실습6] RAID5 구축

Linear RAID 구축과 비슷함, devices를 3개로 설정

1. Terminal 에서
   ```bash
   mdadm --create /dev/md5 --level=5 --raid-devices=3 /dev/sdh1 /dev/sdi1 /dev/sdj1
   mkfs.ext4 /dev/md5
   mkdir /raid5
   mount /dev/md5 /raid5/
   df
   vi /etc/fstab
        /dev/md5 /raid5 ext4 defaults 0 0
        :wq
   mdadm --detail /dev/md5
   ```
