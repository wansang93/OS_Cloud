## 06-10 하드디스크 관리-LVM 개념과 구현

### LVM 개념

LVM(Logical Volume Manage)

- Physical Volume: /dev/sda1, /dev/sdb1 등의 파티션
- Volume Group: 물리 볼륨을 합쳐서 1개의 물리 그룹으로 만드는 것
- Logical Volume: 볼륨 그룹을 1개 이상으로 나눠서 논리 그룹으로 나눈 것

![LVM개념](./assets/06-10LVM개념.png)

### [실습11] LVM 구성

실습 목표: LVM 구현, 관련 명령어 pvcreate, vgcreate, lvcreate를 익힌다.

![06-10실습구성도](./assets/06-10실습구성도.png)

1. 디스크 2개 추가하기
   - SCSI 2G Single, SCSI 3G Single
2. Terminal에서
   ```bash
   # 디스크 껍데기 만들기
   fdisk /dev/sdb
        n -> p -> 1 -> enter -> enter -> t -> 8e
   fdisk /dev/sdb
        n -> p -> 1 -> enter -> enter -> t -> 8e
   
   # physical volume 만들기
   pvcreate /dev/sdb1
   pvcreate /dev/sdb1

   # volume group 만들기
   vgcreate /dev/myVG /dev/sdb1 /dev/sdc1
   
   # volume group 확인하기
   vgdisplay

   # volume group을 Logical volume으로 나누기
   lvcreate --size 1G --name myLG1 myVG
   lvcreate --size 3G --name myLG2 myVG
   lvcreate --extents 100%FREE --name myLG3 myVG  # 나머지 용량 쓰기
   
   # 확인하기
   ls -l /dev/myVG  # 링크 파일임을 확인

   # 포멧하기
   mkfs.ext4 /dev/myVG/myLG1
   mkfs.ext4 /dev/myVG/myLG2
   mkfs.ext4 /dev/myVG/myLG3

   # 마운트 하기
   mkdir /lvm1 /lvm2 /lvm3
   mount /dev/myVG/myLG1 /lvm1
   mount /dev/myVG/myLG2 /lvm2
   mount /dev/myVG/myLG3 /lvm3

   # f stab에 등록하기
   vi /etc/fstab
        /dev/myVG/myLG1   /lvm1   ext4   defaluts    0    0
        /dev/myVG/myLG2   /lvm2   ext4   defaluts    0    0
        /dev/myVG/myLG3   /lvm3   ext4   defaluts    0    0
   ```