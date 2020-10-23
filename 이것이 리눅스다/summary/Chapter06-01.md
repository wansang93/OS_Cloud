## 06-01 IDE 및 SCSI 장치 개념, 하드디스크 1개 추가

### 하드디스크 연결 방식에 따른 분류

1. IDE(Intergrated Drive Electronics)
   - PATA(Parallel Advanced Tachnology Attachment) 라고도 불림
   - 병렬로 데이터를 전송
   - 옛날 규격
2. SATA(Serial Advanced Technology Attachment)
3. SCSI(Small Computer System Interface)
4. SAS(Serial Attached SCSI)
5. HDD -> SSD(Solid State Drive(Disk))

### IDE 장치와 SCSI 장치의 구성

![06-01 하드웨어 구성도](./assets/06-01하드디스크.png)

- IDE는 옛날 방식으로 2개씩 장착 할 수 있음
- 요즘은 SATA 방식으로 장착
- SCSI 하드를 사용한다면
  - SCSI 는 4개를 사용하고
  - 0 ~ 15 까지 16개 중에 7번은 예약이 되어 있어 15개를 사용 가능
  - 4 * 15개 60개를 사용할 수 있음
- 하드 디스크를 물리적으로는 `/dev/sda`, `/dev/sdb`, `/dev/sdc` ... 로 부름
- 디스크 파티션이 나눠진 것을 논리적으로는 `/dev/sda1`, `/dev/sda2`, `/dev/sda3`,` /dv/sdb1`, `/dev/sdb2` ... 로 부름

![06-01 하드디스크 추가](./assets/06-01하드디스크추가.png)

- 장착된 디스크의 이름은 /dev/sdb
- 논리적인 파티션의 이름은 /dev/sdb1
- 파티션을 그냥 사용할 수 없으며 반드시 특정한 디렉토리에 마운트 시켜야 함

### [실습1] 하드디스크 1개 장착

개념도

![06-01 하드디스크 장착](./assets/06-01하드디스크장착.png)

1. 물리적인 하드디스크 장착하기
   - `Add` -> `SCSI` -> `New` -> `1GB`, `Single` -> `Finish`
2. root로 로그인 후 -> Terminal
   ```bash
   fdisk
   ls -l /dev/sd*
   fdisk /dev/sdb  # 하드디스크 들어가기
   m  # 도움말
   n  # new (파티션 만들기)
   # p 주 파티션
   # e 확장 파티션
   p  # primary 파티션 만들기
   p  # default
   1  # default
   `enter`  # 처음부터 끝까지 잡기
   `enter`  # 처음부터 끝까지 잡기
   p  # print info
   w  # write
   ```
3. format 하기, mount 하기
   ```bash
   mkfs.ext4 /dev/sdb1
   
   mkdir /mydata  # scsi0:0 /dev/sdb1 으로 연결할 폴더 생성
   # 사실 현재 /dev/sda2에 연결한거나 마찬가지
   mount /dev/sdb1 /mydata/  # 연결
   mount
   cp anaconda~ /mydata/test1  # 아나콘다 파일을 scsi0:1로 보냄
   # 사실 scsi0:1은 scsi0:0의 /dev/sda2로 연결되어 있는 상태
   umount /dev/sdb1
   ls -l /mydata  # umount 한 상태이기 때문에 데이터가 없음
   ```
 