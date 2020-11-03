## 06-09 하드디스크 관리-RAID 6, RAID0 10의 구축과 문제 발생

### RAID 6와 RAID 1+0 개념

RAID 6은 4개로 구성하게 되면 패리티를 2개 쓰기 때문에 효율이 안나옴,  
그래서 8개~10개 정도로 구성하는게 일반적  

RAID 1+0은 빠르면서 안정적임

### [실습9] RAID 6과 RAID 1+0

실습 목표: 고급 RAID 방식인 RAID 6과 RAID 1+0을 구성해 본다.

실습 구성도

![06-09실습구성도](assets/06-09실습구성도.png)

1. 실습 구성도처럼 8개 부착
2. Terminal 에서
   ```bash
   ls -l /dev/sd*
   fdisk /dev/sdb
        n -> p -> 1 -> enter -> enter -> t -> fd -> w
   # 8개 반복
   ls -l /dev/sd*

   mdadm --create /dev/md6 --level=6 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
   mdadm --detail /dev/md6

   mkfs.ext4 /dev/md6

   mkdir /raid6
   mount /dev/md6 /raid6/

   mdadm --create /dev/md2 --level=1 --raid-devices=2 /dev/sdf1 /dev/sdg2
   mdadm --create /dev/md3 --level=1 --raid-devices=2 /dev/sdh1 /dev/sdi2
   
   mdadm --create /dev/md10 --level=0 --raid-devices=2 /dev/md2 /dev/md3
   mkdir /raid10
   mount /dev/md10 /raid10/
   df

   cp /boot/vmliunz-4* /raid6/testFile
   cp /boot/vmliunz-4* /raid10/testFile

   vi /etc/fstab
          /dev/md6 /raid6 ext4 defaults 0 0
          /dev/md10 /raid10 ext4 defaults 0 0
          :wq
   
   ```

### [실습10] RAID 6과 RAID 1+0의 고장

실습 구성도

![06-09실습구성도2.png](./assets/06-09실습구성도2.png)

1. Server edit virtual machine settings에서
   - SCSI0:2, SCSI0:4, SCSI0:6, SCSI0:8 `remove` 하기

2. Terminal에서
   ```bash
   # 파일 확인
   ls -l /raid6
   ls -l /raid0

   # 작동 확인
   mdadm --detail /dev/md6
   mdadm --detail /dev/md10
   ```