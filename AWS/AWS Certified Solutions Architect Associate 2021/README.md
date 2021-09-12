# AWS Certified Solutions Architect Associate 2021

- 2021-07-27 ~

# Slides

- 교재 링크 -> [https://media.datacumulus.com/aws-saa/AWS%20Certified%20Solutions%20Architect%20Slides%20v4.2.pdf](https://media.datacumulus.com/aws-saa/AWS%20Certified%20Solutions%20Architect%20Slides%20v4.2.pdf)
  - 교재가 정말 잘 되 있음
- 시험 관련 링크 -> [https://aws.amazon.com/certification/certification-prep/](https://aws.amazon.com/certification/certification-prep/)

# Summary & Tips

강의를 들으면서 꿀팁과 요약을 적어봅니다.

## Section 3: Getting started with AWS

### Tips

1. AWS에서 UI 개선 중임, 점차 개선 중이라 안바뀐 UI가 있음
2. 왼쪽 위에 버튼 누르면 옛날 버전으로 바뀜

## Section 4: IAM & AWS CLI

### Section 4: IAM & AWS CLI Summary(p.35, 37)

1. 한 사람당 하나의 AWS user만!
2. 유저를 그룹으로 배정하고 그룹에 권한을 배정하세요.
3. Strong password policy를 만드세요.
4. MFA(Multi Factor Authentication)를 사용을 강제하고 사용해요.
5. AWS 서비스에 권한을 줘서 역할(Roles)을 사용하거나 만드세요.
6. 프로그램 접근(CLI / SDK)는 접근키(Access Key)를 사용하세요.
7. IAM Credentials Reoprt로 여러분의 계정 권한을 감사받으세요.
8. IAW users 와 Access Keys는 절대 공유 안됨!
9. IAM JSON 파일 읽는 법
   - Sid: Statement ID
   - Effect: allow or denies
   - Principal: 정책이 작동할 주체(Who)
   - Action: 정책을 작동할 액션 리스트들(What)
   - Resource: 액션할 자원의 리스트들(Where)

   ![photo/Untitled%200.png](photo/Untitled%200.png) ![photo/Untitled%201.png](photo/Untitled%201.png)

10. 키워드
    - User: AWS 콘솔의 실제 사용자(비번 포함)의 맵핑된 유저
    - Groups: 유저만 포함할 수 있음
    - Policies: 유저나 그룹의 권한을 JSON으로 요약
    - Roles: AWS 서비스나 EC2 인스턴스를 위한 것
    - Security: MFA + 비밀번호 정책
    - Access Keys: CLI, SDK를 사용해 AWS 접근
    - Audit: IAM Credential Reports & IAM Access Advisor

### Tips

1. 해당 서비스를 들어가서 지역을 보면 Global인지 아닌지 알 수 있음
2. 계정@계정은 IAM 계정임을 알 수 있음
3. MFA를 지원하는 3rd-party OTP 장비가 많음, 나는 안 쓸듯
4. AWS CLI windows용 다운 링크 -> [https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)
5. CouldShell은 안되는 지역이 많음(Seoul도 안됨)
6. IAM Security Tools은 **Credentials Report**(account-level)와 **Access Advisor**(uer-level)로 나뉨

## Section 5: EC2 Fundamentals

### Section 5: EC2 Fundamentals Summary(p.69)

1. EC2 인스턴스 Basic Summary
   - EC2 Instance: AMI (OS) + Instance Size (CPU + RAM) + Storage + security groups + EC2 User Data
   - Security Groups: EC2 인스턴스에 부착된 방화벽
   - EC2 User Data: 인스턴스에서 처음 시작하면 실행되는 스크립트
   - SSH: 터미널을 시작해 EC2 인스턴스 접속(Port 22)
   - EC2 Instance Role: IAM Role로 연결됨
   - Purchasing Options
     - **On-Demand**: 사용한 만큼 지불
     - **Spot**: 제일 쌈, 장애에 대한 복원력이 뛰어난 워크로드에 유용
     - **Reserved**
       - Standard: 1년 or 3년 약정(부분 선지불 가능)
       - Convertible: instance 타입 변경이 가능
       - Scheduled: 예약된 시간에 실행, 1년 단위
     - **Dedicated Host**
       - EC2 인스턴스가 있는 물리적 서버를 빌림
       - 서버 바인딩 소프트웨어 라이센스를 사용해 규정 준수 해결 및 비용 절감
       - 3년동안 계정에 할당, 더 비쌈(잘쓰면 더 쌈)
       - 복잡한 라이센스 모델, 규정 준수 요구가 강한 기업에 적합
       - It's always the same physical machine for as long as you are paying.
     - **Dedicated Instance**
       - 사용자 전용 하드웨어에서 실행되는 인스턴스
       - 동일한 계정의 다른 인스턴스와 하드웨어 공유 가능
       - 인스턴스 배치 제어x(Stop/Start 후 하드웨어 이동 가능)
       - Your instance is moved around on different physical servers - whichever is not occupied by others at the time.
     - [Dedicated Host VS Dedicated Instance in stackoverflow](https://stackoverflow.com/questions/64309679/aws-dedicated-host-vs-dedicated-instance-why-the-first-is-more-expensive-than)
2. Security Groups
   
   ![photo/Untitled%202.png](photo/Untitled%202.png)

   - Security groups은 EC2의 방화벽 역활
   - 포트 열기, 인/아웃 바운드 규칙 설정, IP 인증
   - 여러 인스턴스에 부착 가능
   - Region / VPC 조합으로 제한, EC2가 밖에 있으면 트래픽 차단
   - SSH 접속을 위해 하나의 보안 그룹을 유지하는게 좋음
   - 앱이 **시간 초과**로 액세스 못하면 **보안 그룹 문제**임
   - 앱이 **연결 거부**면 **앱 오류나 실행x**
   - 기본 설정으로 **inbound 트래픽은 차단**, **outbound 트래픽은 허용**

### Tips

1. 루트 계정으로 `내 계정`들어가서 내리면 Billing을 공유할 수 있는 설정이 나옴, 거기서 체크해줘야 나중에 다른 유저가 볼 수 있음
2. budget 설정 때 Email 하나당 threshold가 1개여야됨
3. `echo "<h1>$(hostname -f)</h1>" > /var/www/html/index.html` 하면 hostname의 private ip주소를 볼 수 있음
4. 인스턴스 타입 읽는법: m5.2xlarge -> m은 **인스턴스 클래스**, 5는 **제너레이션**, 2xlarnge는 **인스턴스 클래스의 사이즈**
5. 인스턴스 클래스 타입들
   1. Compute용: [C] 컴퓨트의 약자, 배치 프로세싱 워크로드, 게임 서버, 머신러닝, 하이 퍼포먼스 컴퓨터, 웹 서버, 동영상 파일 변환 등
   2. In-Memory용: [R, X, Z] Ram의 약자, 높은 퍼포먼스, DB용, 웹 캐쉬용, 인메모리 DB, 리얼타임에 적합한 앱
   3. Storage용: [I, D, H], OLTP(online transaction processing) 시스템(빈번한 호출), Redis같은 캐쉬 인메모리 DB, 유, Data 웨어하우스 앱, 분산 파일 시스템
6. windows10이상에서 ssh 접속이 가능함, `ssh -i <key_location> <ec2-user>@<ip-address>`로 접속(권한 오류발생)
   1. 이러면 권한 설정 때문에 `chmod` 처럼 권한을 바꿔야 함
   2. 파일에서 오른쪽버튼 `속성` -> `보안` -> `고급` -> `소유자 변경` -> `해당 유저`로 변경
   3. 해당 유저만 권한을 남기고 저장
   4. Full control인지 확인하고 다시 위에 명령어 실행

## Section 6: EC2 - Solutions Architect Associate Level

### Tips

1. 스팟 인스턴스는 EC2 종료(terminate)해도 다시 생김으로 Spot request를 삭제해야 함
   
   ![photo/Untitled%203.png](photo/Untitled%203.png) ![photo/Untitled%204.png](photo/Untitled%204.png)

### Placement Groups

누군가가 EC2 인스턴스 대체 정책(Strategy)을 컨트롤하고 싶을 때

1. Placement Groups의 종류
   1. 클러스터(Cluster)

      ![photo/Untitled%205.png](photo/Untitled%205.png)

      - Single AZ에서 저지연성 그룹으로 인스턴스 클러스터링(병렬시스템으로 구축)
      - 장점: 좋은 내트워크(인스턴스 간 10Gbps 대역폭)
      - 단점: rack이 고장나면 모든 인스턴스 동시 고장
      - 사용: 빠르게 완료해야하는 빅데이터, 저지연성, 고효율 네트워크가 필요한 앱
   2. 스프레드(Spread)

      ![photo/Untitled%206.png](photo/Untitled%206.png)

      - 인스턴스를 하드웨어에 따로 분산
      - 장점: 여러 AZ에 분산 배포, 물리적 분리, 동시 실패 리스크 감소
      - 단점: placement group 당 AZ 당 최대 7개
      - 사용: 고가용성이 필요한 앱, 중요한 앱
   4. 파티션(Partition)

      ![photo/Untitled%207.png](photo/Untitled%207.png)

      - AZ내에 여러 파티션에 인스턴스 분산
      - AZ당 7개까지의 파티션, 파티션 당 100개까지의 인스턴스 배포
      - 다른 rack set의 의존적임
      - 파티션 고장시 많은 많은 EC2 고장, 다른 파티션 영향은 x
      - EC2에서 메타데이터 같은 파티션 정보를 불러올 때
      - 사용: Hadoop, Cassandra, Kafka
2. AWS 창에서 `Placement groups`를 클릭 -> 정책 생성 -> 그리고 Instance 생성시 `3.Configure Instance`의 `Placement group name` 설정

### ENI(Elastic Network Interfaces)

1. 가상 네트워크 카드를 나타내는 VPC의 논리적 요소
2. ENI의 속성으로 설정 가능한 것들
   - 사설 아이피(Private IPv4)에 하나, 또는 2개의 secondary ENI를 가짐
   - 사설 아이피(Private IPv4)당 하나의 Elastic IP를 가짐
   - 퍼블릭 아이피 할당 가능
   - MAC 주소를 할당 가능
   - 보안 그룹을 하나 이상 설정 가능
3. 실패(failover)가 뜨면 EC2의 ENI를 때서 다른 ENI로 붙일 수 있음
4. 한 AZ에 국한됨(bound)

![photo/Untitled%208.png](photo/Untitled%208.png)

### EC2 Hibernate(EC2 절전모드)

EC2의 여러가지 상태
- Stop: EBS 데이터가 남아있음, 다음 시작때 작동
- Terminate: EBS 다 날라감
- Start
  - 첫 시작이면: OS boots를 하고 EC2 유저 데이터 스크립트 실행
  - 두번째 시작이면: OS boots up만
  - 시작 후 app 시작, caches warmed up 등
- Hibernate

   ![photo/Untitled%209.png](photo/Untitled%209.png)

   - In-mermory(RAM) 상태가 보존!
   - Instance boot 스피드가 훨씬 빠름(OS is not stooped, restarted)
   - RAM 상태가 root EBS volume에 쓰여짐, 암호화
   - C3, C4, C5, M3, M4, M5, R3, R4, R5 지원
   - RAM size가 150GB 이하여야 됨
   - bare metal 인스턴스 지원x
   - AMI: Amazon Linux 2, Linux AMI, Ubuntu & Windows ...
   - Root Volume: EBS여야 하고 크고 암호화됨, 인스턴스 스토어는 안됨
   - On-Demand, Reserved Instances에서 사용 가능
   - 60일 초과 절전모드는 불가

### EC2 Nitro

- **AWS 5세대 인스턴스**로 퍼포먼스가 더 좋고 보안이 강화됨
- 새 가상화 기술, NVMe 스토리지 사용, 네트워크 모듈인 ENA를 사용

### EC2 - vCPU

- 멀티스래딩(Multithreading) 지원, 각 스레드는 Virtual CPU로 표현
- RAM과 vCPU는 함께 조합이 되는데 vCPU를 조절 가능
  - CPU cores수: 높은 RAM과 낮은 CPU 수가 필요한 경우 이를 줄여 라이센스 비용을 절감
  - core 당 스레드 수: CPU당 1개의 스레드를 가지도록 멀티스레딩을 비활성화하여 고성능 컴퓨팅(HPC) 워크로드에 유용
- Istance 생성 중에만 설정 가능

![photo/Untitled%2010.png](photo/Untitled%2010.png)

### EC2 - Capacity Reservations(용량 예약)

- 용량 예약은 용량이 필요할 때 보장해줌
- 수동으로 또는 끝나는 날을 예약함
- 1, 3년 예약을 안해도 됨
- 용량에 대한 접근은 즉시 되고 시작하자마자 비용이 청구됨
- 지정해야할 것
  - 용량을 예약할 AZ(only one)
  - 인스턴스의 수
  - 인스턴스 유형, Tenancy 및 플랫폼/OS를 포함한 인스턴스 속성
- 예약 인스턴스와 세이빙 플랜을 결합해서 비용 절감

## Section 7: EC2 Instance Storage

### EBS(Elastic Block Store)

- 네트워크 USB 스틱이라고 생각하면 됨
  - 지연성이 있을 수도 있음, EC2 instance에 빠르게 탈부착 가능
- 특정 AZ에 바인딩 되어 있음
  - 다른 AZ에 부착 불가, 따라서 snapshot을 찍고 옮겨야 함
- **오직 한개의 인스턴스에 하나만** 마운트 가능
  - 단 io1/io2 는 같은 AZ 내에서 멀티 마운트 가능
  - 각 인스턴스는 
    - Must use a file system that’s cluster-aware
    - not XFS, EX4, etc…
- 프로비저닝된 용량만큼 비용 청구, 용량을 늘릴 수 있음
- EC2 instance가 terminate되면 EBS 동작을 제어함
  - 기본 세팅: root EBS 볼륨 삭제
  - 기본 세팅: 다른 연결된 EBS 볼륨 삭제는 x
- 인스턴스 삭제되도 root volume 유지 가능
- EBS Snapshots
  - AZ나 Region간의 EBS 복사는 스넵샷을 통해서 가능
  
    ![photo/Untitled%2011.png](photo/Untitled%2011.png)
  
  - EBS volume에 백업을 만듬
  - snapshot 찍을 때 탈착이 필수는 아니지만 추천
  - AZ 나 Region 간 shapshot 복사 가능

EBS Volume
- 타입
  - gp2 / gp3(SSD): General purpose(1GB ~ 16TB), low-latency
  - io1 / io2(SSD): Highest-performance(4GB ~ 64TB)
  - st1(HDD): Low cost, frequently accessed
  - sc1(HDD): Lowest cost HDD, less frequently accessed
- SSD만 부트볼륨으로 사용 가능

EBS Encryption
- 암호화 EBS 볼륨을 만들면 다음을 따릅니다.
  - 볼륨의 유휴(at rest)데이터는 암호화됩니다.
  - 인스턴스와 볼륨간 이동중인 모든 데이터는 암호화됩니다.
  - 모든 스냅샷은 암호화됩니다.
  - 모든 볼륨은 스냅샷으로부터 만들어집니다.
- 

### AMI(Amazon Machine Image)

- AMI는 EC2의 커스터마이제이션임
  - 소프트웨어, 환경 구성, OS, 모니터링 등을 추가 가능
  - 빠르게 boot / 환경 설정, 왜냐면 소프트웨어가 프리 패키징됬기 때문
- 특정 지역으로 빌드됨(지역간 이동은 복사를 통해 가능)
- EC2를 런칭하는 방법
  - Public AMI: AWS제공
  - own AMI: 자체 커스터마이제이션
  - Marketplace AMI: 누군가가 만들어 논 AMI(팔 수 있음)

AMI의 절차

![photo/Untitled%2012.png](photo/Untitled%2012.png)

1. EC2 시작, 커스터마이징
2. 인스턴스를 멈춤(데이터 무결성(integrity)를 위해)
3. AMI 빌드(EBS 스냅샷도 생성)
4. 다른 AMIs로 부터 인스턴스 런칭

### EC2 Instance Store

- EBS 볼륨은 네트워크 드라이브로 좋지만 성능에 제한이 있음
- 고성능을 원하면 EC2 인스턴스 저장소(EC2 Instance Store)를 사용해요!
  - 좋은 I/O 퍼포먼스 단, EC2 인스턴스가 멈추면 저장소는 날라감
  - 버퍼, 캐쉬, scratch data/temporary content에 적합함
  - 하드웨어 장애시 데이터 손실 위함
  - 백업이나 복구는 여러분의 책임!

### EFS

![photo/Untitled%2013.png](photo/Untitled%2013.png)

### EBS vs EFS

![photo/Untitled%2014.png](photo/Untitled%2014.png) ![photo/Untitled%2015.png](photo/Untitled%2015.png)

## Section 8: High Availability and Scalability: ELB & ASG

![photo/Untitled%2016.png](photo/Untitled%2016.png)

## Section 9: AWS Fundamentals: RDS + Aurora + ElastiCache

## Section 10: Route 53

## Section 11: Classic Solutions Architecture Discussions

## Section 12: Amazon S3 Introduction

## Section 13: AWS SDK, IAM Roles & Policies

## Section 14: Advanced Amazon S3 & Athena

## Section 15: CloudFront & AWS Global Accelerator

## Section 16: AWS Storage Extras

## Section 17: Decoupling applications: SQS, SNS, Kinesis, Active MQ

## Section 18: Containers on AWS: ECS, Fargate, ECR & EKS

## Section 19: Serverless Overviews from a Solution Architect Perspective

## Section 20: Serverless Solution Architecture Discussions

## Section 21: Databases in AWS

## Section 22: AWS Monitoring & Audit: CloudWatch, CloudTrail & Config

## Section 23: Identity and Access Management (IAM) - Advanced

## Section 24: AWS Security & Encryption: KMS, SSM Parameter Store, CloudHSM, Shield, …

## Section 25: Networking - VPC

## Section 26: Disaster Recovery & Migrations

## Section 27: More Solution Architectures

## Section 28: Other Services

## Section 29: WhitePapers and Architectures - AWS Certified Solutions Architect Associate

## Section 30: Preparing for the Exam + Practice Exam - AWS Certified Solutions Architect Associate

## Section 31: Congratulations - AWS Certified Solutions Architect Associate
