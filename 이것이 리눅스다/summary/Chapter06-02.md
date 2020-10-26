## 06-02 하드디스크 관리-RAID 개념1(Linear, RAID0, RAID1)

### RAID 정의 및 개념

RAID 정의
- RAID: Redundant Array of Inexpensive Disks
- 여러 개의 디스크를 하나의 디스크처럼 사용함
- 비용 절감 + 신뢰성 향상 + 성능 향상의 효과를 냄

Hardware RAID
- 하드웨어 제조업체에서 여러 개의 하드디스크를 가지고 장지를 만들어서 그 자체를 공급
- 좀 더 안정적이지만 비쌈

Software RAID
- 고가의 하드웨어 RAID의 대안
- 운영체제에서 지원하는 방식
- 저렴한 비용으로 좀 더 안전한 데이터의 저장이 가능
- 우리가 공부하는 것은 software RAID 임

### RAID 기술

- Striping: Share data
- Mirroring: Copy data
- Parity: Check error

### RAID 방식의 비교

|                      | Linear RAID | RAID 0 | RAID 1       | RAID 5               | RIAD 6            | RAID 1+0                     |
| -------------------- | ----------- | ------ | ------------ | -------------------- | ----------------- | ---------------------------- |
| Minimum Drives       | 2           | 2      | 2            | 3                    | 4                 | 4                            |
| READ Performance     | -           | High   | High         | High                 | High              | High                         |
| WRITE Performance    | -           | High   | Medium       | Low                  | Low               | Medium                       |
| Capactiy Utilization | 100%        | 100%   | 50%          | 67 ~ 94%             | 50% ~ 88%         | 50%                          |
| Data Protection      | NO          | NO     | Single-drive | Single-drive faliure | Two-drive faliure | Up to 1 disk in each subarray |

### Linear RAID

- 갯수: 2개 이상
- 방식: 앞 디스크부터 차례로 저장
- 효율성: 100% 공간 효율성
- 신뢰성: 보통
- 특징: 2개 이상의 하드디스크를 1개의 볼륨으로 사용

### RAID 0

- 갯수: 2개 이상
- 방식: 모든 디스크에 동시에 저장됨
- 효율성: 100% 공강효율성
- 신뢰성: 낮음
- 특징: 빠른 성능, 하나만 고장나더라도 모두가 고장

### RAID 1

- 하드디스크 갯수: 2개 이상
- 방식: 미러링(Mirroring)
- 신뢰성: 높음
- 공간 효율성: 50%
- 특징: 결함 허용(Fault tolerance)

![06-02RAID방식](./assets/06-02RAID방식.png)

### RAID 표 참고

![06-02RAID.png](./assets/06-02RAID.png)