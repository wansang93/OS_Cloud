## 06-12 사용자별 공간할당-쿼터 개념과 실습

### 사용자별 공간 할당 - 쿼터

- 쿼터(Quota) 개념
  - 파일시스템마다 사용자나 그룹이 생성할 수 있는 파일의 용량 및 갯수를 제한
  - 파일시스템을 "/"로 지정하는 것보다는, 별도의 파일시스템을 지정해서 해당 부분을 쓰도록 하는 것이 좋음
  - "/"파일시스템을 많은 사용자가 동시에 사용하게 되면, CentOS 서버를 운영하기 위해서 디스크를 읽고 쓰는 작업과 일반 사용자가 디스크를 읽고 쓰는 작업이 동시에 발생하므로 전반적으로 시스템의 성능이 저하됨  

### [실습13] 쿼터 실습

실습 목표: 사용자를 만들고, 해당 사용자에게 공간을 할당하고 쿼터의 설정 및 작동에 대해 익힌다.

실습 순서: /edt/fstab 수정 -> 재부팅 or 리마운팅 -> 쿼터 DB 생성 -> 개인별 쿼터 설정

1. 10G 디스크 장착하기
   
   많이 해봐서 생략

2. Terminal에서
   ```bash
   # 10G 하드디스크를 쿼터용으로 만들기
   # 1. 하드디스크 연결하기 
   fdisk /dev/sdb
        n -> p -> 1 -> enter -> enter -> w
   mkfs.ext4 /dev/sdb1
   mkdir /userHome
   monut /dev/sdb1 /userHome/

   vi /etc/fstab
        /dev/sdb1   /userHome   ext4    defaults    0   0

   # 2. 사용자 2명 만들기
   useradd -d /userHome/john john
   useradd -d /userHome/bann bann

   passwd john
   passwd bann

   ls -l /userHome/

   # 3. 쿼터 추가하기(옵션을 quota로 설정하여서)
    vi /etc/fstab
        /dev/sdb1   /userHome   ext4    defaults,usrjquota=aquota.user,jqfmt=vfsv0    0   0

   # 4. monut 다시하기
   mount --options remount /userHome/

   # 5. mount 확인하기
   mount

   # 6. 쿼터 DB 생성하기
   cd /userHome/

   quotaoff -avug  # 쿼터 끄기
   quotacheck -augmn  # 쿼터 체크하기
   rm -rf aquota.*
   quotacheck -augmn  # 쿼터 체크하기
   touch aquota.user aquota.group
   chmod 600 aquota.*  # 일반 사용자는 볼 수 없게 설정
   quotacheck -augmn  # 쿼터 체크하기
   quotaon -avug  # 쿼터 켜기

   # 7. 쿼터 할당하기
   edquota -u john  # john 쿼터 설정하기, vieditor로 설정
   # soft가 경고 수준, hard는 아에 못만듬
   20480(20MB), 30720(30MB)
   
   su - john
   cp /boot/vmlinuz-4* test1
   cp /boot/vmlinuz-4* test2
   cp /boot/vmlinuz-4* test3  # 경고 출력
   cp /boot/vmlinuz-4* test3  # 오류 출력, 파일이 짤림
   
   quota  # 얼마나 사용할 수 있는지 확인 **가능**

   exit  # 루트로 돌아와서
   # 사용자별 할당량 보기
   repquota /userHome/

   # john에 설정된 내용을 bann에게도 똑같이 적용
   edquota -p john bann
   ```
