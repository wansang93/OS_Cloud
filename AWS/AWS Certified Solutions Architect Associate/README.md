# AWS Certified Solutions Architect Associate SAA-C03

Ultimate AWS Certified Solutions Architect Associate SAA-C03(Udemy 강의)를 공부했습니다.

- [교재 링크](https://courses.datacumulus.com/downloads/certified-solutions-architect-pn9/)
  - 교재가 정말 잘 되 있음
- [시험 관련 링크](https://aws.amazon.com/certification/certification-prep/)
- 공부 기간
  - 2021-07-27 ~ 2021-09-13 (~ Section 6)
  - 2023-11-23 ~ 2023-12-26 (~ Section 8)

## Slides Summary & Tips

강의를 들으면서 꿀팁과 요약을 적어봅니다.

강의에서 배우는 Service들

![photo/Untitled%2018.png](photo/Untitled%2018.png)

## Section 3: Getting started with AWS

### AWS Overview - Regions & AZ

#### Regions & AZ, Points of Presence

- Region(지역)
  - data는 명시적 허가없이 절대 지역 밖으로 나가지 않음
  - 저 지연성으로 고객에게 제공
  - 리전별로 서비스 제공
  - 지역별로 가격이 다르며 가격 페이지에서 투명하게 제공
- Availability Zones(AZ, 가용영역)
  - 각 지역은 3~6개의 가용용역이 있음(ex. ap-southeast-2a, 2b, 2c)
  - AZ는 1개 이상의 떨어진 data centres가 있음, 이중화 전력, 네트워킹, 연결가능한
  - AZ는 각자 따로 존재, 재앙으로 부터 격리
  - 높은 대역폭과 초저지연성으로 연결
- Points of Presence(Edge Locations)
  - 400+ Edge Locations
  - 10+ Regional Caches
  - 40+ 나라의 90+ 도시의 Points of Presence 존재
  - Content를 end-user에게 저지연성으로 전달

#### AWS 글로벌 서비스들

- AWS Identity and Access Management(IAM)
- AWS Organizations
- Amazon CloudFront
- Amazon Route53
- AWS Global Accelerator
- AWS Direct Connect
- AWS Firewall Manager
- AWS Web Application Firewall(WAF)
- and AWS Shield

나머지는 Region

### Getting started with AWS Tips

1. AWS에서 UI 개선 중임, 점차 개선 중이라 안바뀐 UI가 있음
2. 왼쪽 위에 버튼 누르면 옛날 버전으로 바뀜

## Section 4: IAM & AWS CLI

### IAM Introduction: Users, Groups, Policies

#### IAM: Users & Groups

- IAM: Identity and Access Management, Global service
- Root account: 기본적으로 존재, 사용 or 공유 금지
- User: 단체의 사람들, 그룹으로 그룹핑 가능, 멀티그룹핑 가능
- Groups: User만 포함, 그룹을 그룹핑 불가

#### IAM Permissions

- User or Groups은 JSON으로 정책 할당 가능
- 유저의 권한을 정책으로 정의
- least privilege principle 으로 필요 이상 권한 주지 말기

### IAM Policies

IAM JSON 구조

- Sid: Statement ID
- Effect: allow or denies
- Principal: 정책이 작동할 주체(Who)
- Action: 정책을 작동할 액션 리스트들(What)
- Resource: 액션할 자원의 리스트들(Where)

![photo/Untitled%200.png](photo/Untitled%200.png) ![photo/Untitled%201.png](photo/Untitled%201.png)

### MFA

비번 관리 잘하고 정책 설정 잘하고 MFA 사용하세요

### AWS Access Keys, CLI and SDK

#### 유저가 AWS에 접근하는 방법

- AWS 접근하는 3가지 방법
  - Console: PW, MFA로 콘솔 접근
  - CLI(Command Line Interface): Access Keys로 접근
  - SDK(Software Developer Kit): Access Keys로 접근
- Access Keys는 Console에서 생성
- 유저가 Access Keys를 관리
- Access Keys는 password 같은 것, 공유 금지
  - Access Key ID: username 같은 거
  - Secret Access Key: password 같은 거

#### AWS CLI

- AWS 서비스를 사용하기 위한 커멘드 라인 인터페이스
- AWS 서비스의 public APIs로 직접 접근
- 오픈소스, AWS Management Console 사용 대안

#### AWS SDK

- AWS Software Development Kit(AWS SDK)
- 라이브러리를 통한 언어 특화 API
- AWS를 프로그래밍 방식으로 관리하고 접근 가능
- 앱에 내장됨(Embedded)
- JS, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++, Android, iOS, Arduino 지원
- ex. AWS CLI는 Python으로 작성된 AWS SDK인 Boto3를 기반으로 통신

### AWS CloudShell

AWS Console에서 직접 실행하는 CLI

- 몇몇 지역만 사용 가능

### IAM Roles

- AWS Roles로 서비스에 권한 할당
- 서비스의 적용 대상 설정 및 여러 권한 설정

### IAM Security Tools

- IAM Credentials Report(account-level)
  - IAM -> Credentials Report -> Download -> 엑셀로 정보 확인
  - 모든 계정의 유저들의 여러 위협의 상태를 보고해줌
- IAM Access Advisor(user-level)
  - IAM -> Users -> 해당 user 클릭 -> Access Advisor 클릭
  - 서비스들의 마지막 접근 시간, 유저에 부여된 권한을 보여줌
  - 이 정보를 사용해 정책을 수정

### IAM Best Practices

- root user: 사용 금지, Account setup을 제외
- user: 한 사람당 하나
- group: 그룹에 정책 설정 후 유저를 그룹에 배치
- password: Strong password policy
- MFA(Multi Factor Authentication): 사용 강제, 사용하기
- Roles: AWS services 권한을 주기위해 만들고 사용
- Access: 프로그래믹 방침(CLI/SDK)은 접근키(Access Key)를 사용
- Audit: IAM Credentials Reoprt로 여러분의 계정 권한을 감사
- Share: IAW Users, Access Keys 절대 금지

### IAM Summary

- User: AWS 콘솔의 실제 사용자(비번 포함)의 맵핑된 유저
- Groups: 유저만 포함할 수 있음
- Policies: 유저나 그룹의 권한을 JSON으로 요약
- Roles: AWS 서비스나 EC2 인스턴스를 위한 것
- Security: MFA + 비밀번호 정책
- AWS CLI: CLI로 AWS 서비스 관리
- AWS SDK: 프로그래밍 언어로 AWS 서비스 관리
- Access Keys: CLI, SDK를 사용해 AWS 접근
- Audit: IAM Credential Reports & IAM Access Advisor

### IAM & AWS CLI Tips

1. 해당 서비스를 들어가서 지역을 보면 Global인지 아닌지 알 수 있음
2. 계정@계정은 IAM 계정임을 알 수 있음
3. MFA를 지원하는 3rd-party OTP 장비가 많음, 나는 안 쓸듯
4. AWS CLI windows용 다운 링크 -> [https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)
5. CouldShell은 안되는 지역이 많음(Seoul도 안됨)
6. IAM Security Tools은 **Credentials Report**(account-level)와 **Access Advisor**(uer-level)로 나뉨

## Section 5: EC2 Fundamentals

### AWS Budget Setup

- IAM User 계정으로 Bill & Cost Management Dashboard 들어가는 방법
  - Root Account 접속 -> My Account -> IAM User and Role Access to Billing Info -> Activate IAM Access 클릭
  - IAM User 계정 들어가서 -> Bill & Cost Management Dashboard -> Charges by services -> EC2 -> 얼마 나왔는지 확인
- Budgets 서비스 -> Create a budget -> budget 정책 설정 -> 메일 설정

### EC2 Basics

- EC2(Elastic Compute Cloud): Infrastructure as a Service
  - Virtual machines 렌탈(EC2)
  - 다양한 저장 장치(EBS)
  - 여러 시스템에 로드 분산(ELB)
  - Auto Scaling Group(ASG) 가능

#### EC2 sizing & configuration options

- EC2 Instance

  - AMI(OS)
  - Instance Size(CPU+RAM)
  - Storage(EBS, EFS, EC2 Instance Store)
  - gNetwork Card
  - Security Groups(Firewall rules): EC2 인스턴스에 부착된 방화벽
  - EC2 User Data(Bootstrap script): 인스턴스에서 처음 시작하면 실행되는 스크립트

- EC2 구성 설정
  - SSH: 터미널을 시작해 EC2 인스턴스 접속(Port 22)
  - EC2 Instance Role: IAM Role로 연결됨

### EC2 Instance Types Basics

- 인스턴스 타입 읽는법 예시 m5.2xlarge
  - m: **인스턴스 클래스**
  - 5: **제너레이션**
  - 2xlarnge: **인스턴스 클래스의 사이즈**
- 인스턴스 클래스 타입들
  1.  Compute용: [C] 컴퓨트의 약자, 배치 프로세싱 워크로드, 게임 서버, 머신러닝, 하이 퍼포먼스 컴퓨터, 웹 서버, 동영상 파일 변환 등
  2.  In-Memory용: [R, X, Z] Ram의 약자, 높은 퍼포먼스, DB용, 웹 캐쉬용, 인메모리 DB, 리얼타임에 적합한 앱
  3.  Storage용: [I, D, H], OLTP(online transaction processing) 시스템(빈번한 호출), Redis같은 캐쉬 인메모리 DB, 유, Data 웨어하우스 앱, 분산 파일 시스템

### Security Groups & Classic Ports Overview

![photo/Untitled%202.png](photo/Untitled%202.png)

- Security groups은 EC2의 방화벽 역할
- 포트 열기, 인/아웃 바운드 규칙 설정, IP 인증
- 여러 인스턴스에 부착 가능
- Region / VPC 조합으로 제한, EC2가 밖에 있으면 트래픽 차단
- SSH 접속을 위해 하나의 보안 그룹을 유지하는게 좋음
- 앱이 **시간 초과**로 액세스 못하면 **보안 그룹 문제**임
- 앱이 **연결 거부**면 **앱 오류나 실행x**
- 기본 설정으로 **inbound 트래픽은 차단**, **outbound 트래픽은 허용**

![photo/Untitled%2017.png](./photo/Untitled%2017.png)

- Inbound를 열고 Authorising Security Group1 해서 접속 가능
- Inbound를 열고 Authorising Security Group2 해서 접속 가능
- Inbound를 열었지만 Security Group3에 대해 Authorising 하지 않아 접속 불가

- 기본 포트들
  - 22 SSH(Secure Shell): 리눅스 로그인
  - 21 FTP(File Transfer Protocl): 파일 공유로 파일 업로드
  - 22 SFTP(Secure File Transfer Protocol): SSH로 파일 업로드
  - 25 SMTP(Simple Mail Transfer Protocol): 메일 서버
  - 53 DNS(Domain Service System): 도메인 주소
  - 80 HTTP(Hyper Text Transfer Protocol): 웹 접속
  - 443 HTTPS(Hyper Text Transfer Protocol Secure): 보안 웹 접속
  - 1433 MSSQL
  - 1521 Oracle
  - 3306 MySQL
  - 3389 RDS(Remote Desktop Protocol): 윈도우 로그인

### SSH Overview & SSH Troubleshooting

- SSH 로 Mac, Linux, Window10 이상 접속 가능
  - Windows는 기본적으로 Putty Lecture
- SSH 포트로 원격에 컴퓨터 접속해 CLI 사용 가능
- windows10이상에서 ssh 접속이 가능함, `ssh -i <key_location> <ec2-user>@<ip-address>`로 접속(권한 오류발생)
  1.  이러면 권한 설정 때문에 `chmod` 처럼 권한을 바꿔야 함
  2.  `.pem` 파일에서 오른쪽버튼 `속성` -> `보안` -> `고급` -> `소유자 변경` -> `해당 유저`로 변경
  3.  해당 유저만 권한을 남기고 저장
  4.  `Full control`인지 확인하고 다시 위에 명령어 실행
- Troubleshooting
  - connection timeout: Inbound에서 SSH 있는지 확인, 개인 방화벽 확인
  - Windows에서 SSH 접속 불량: 위 방법, 모르면 구글링
  - connection refused: 인스턴스 재시작, Linux2로 인스턴스 생성
  - 어제는 됬는데 오늘 안됨: EC2의 IP 변경 확인

### EC2 Instance Connect

- Console에서 쉽게 SSH로 연결하는 방법
- Console -> EC2 -> Instance -> 인스턴스 선택 -> Connect -> EC2 Instance Connect -> User-name 입력 후 연결
- 이 방법은 SSH 포트가 열려 있어야 가능
- 이 방법으로 aws 접근하려면 Role을 주어서 사용할 것!
  - 직접 Access Key로 연결할 수 있지만 보안에 매우 안좋음
  - IAM role에서 role 생성
  - EC2 Instance -> 인스턴스 선택 -> Connect -> Security -> Modify IAM role -> role 연결

### EC2 Instance Purchasing Options

구매 옵션들을 호텔에 비유

- On-Demand: 당일날 와서 머무르기
- Reserved: 장기 고객, 할인 많이 해줌
- Savings Plan: 장기 고객, 시간 단위로 아무방 예약 가능
- Spot instance: 빈방을 싸게 사용 가능, 언제든지 쫒겨날 수 있음
- Dedicated Host: 호텔 전체 빌리기
- Capacity Reservations: 특정 방을 항상 빌림, 안머물러도 비용 지불

#### Purchasing Options

- **On-Demand**
  - 사용한 만큼 지불
  - 잠시 사용, 테스트, 비용 및 서비스 예상 불가일 때 사용
- **Reserved**
  - 최대 72% 할인
  - 속성
    - Standard: 1년 or 3년 약정
    - Convertible: instance 타입 변경이 가능(할인율 감소)
  - 지불방식: No Upfront, Partial Upfront, All Upfront(선지불)
  - RI Marketplace에서 사고 팔 수 있음
- **Savings Plans**
  - RI와 비슷하게 할인
  - 시간당 얼마를 1년 or 3년 약정
  - 특정 인스턴스나 패밀리로 락
  - 유연함: Instance Size, OS, Tenancy(Host, Dedicated, Default)
- **Spot**: 제일 쌈, 장애에 대한 복원력이 뛰어난 워크로드에 유용
- **Dedicated Host**
  - EC2 인스턴스가 있는 물리적 서버를 전체를 빌림
  - 서버 바인딩 소프트웨어 라이센스를 사용해 규정 준수 해결 및 비용 절감
    - On-Demand, RI 사용 가능
  - 복잡한 라이센스 모델, 규정 준수 요구가 강한 기업에 적합
  - It's always the same physical machine for as long as you are paying.
- **Dedicated Instance**
  - 사용자 전용 하드웨어에서 실행되는 인스턴스
  - 동일한 계정의 다른 인스턴스와 하드웨어 공유 가능
  - 인스턴스 배치 제어x(Stop/Start 후 하드웨어 이동 가능)
  - Your instance is moved around on different physical servers - whichever is not occupied by others at the time.
- [Dedicated Host VS Dedicated Instance](https://aws.amazon.com/ec2/dedicated-hosts/#:~:text=An%20important%20difference%20between%20a,same%20physical%20server%20over%20time.)

### Spot Instances & Spot Fleet

Spot Instances

- spot price는 최대 가격 설정하고 현재 가격보다 최대 가격이 싸면 실행
- 최근 스팟 가격이 더 커지면 인스턴스가 2분 후 stop or terminate 됨
- 배치 or 데이터 분석, 워크로드 등에 실패해도 괜찮을 때 사용

스팟 인스턴스는 EC2 종료(terminate)해도 다시 생김으로 Spot request를 삭제해야 함

![photo/Untitled%203.png](photo/Untitled%203.png) ![photo/Untitled%204.png](photo/Untitled%204.png)

#### Spot Fleets

- Set of Spot Instances + (optional) Op-Demand Instances
- 자동으로 Spot 인스턴스를 최저가에 적용
- 가격 제한이 걸린 특정 용량 사용을 도와줌
  - 타입, OS, AZ를 launch pools 정의
  - launch pools 을 여러개 설정, 묶음을 선택 가능
  - Capacity나 요금에 도달하면 stops
- Spot Instances 사용 전략
  - 최저 가격: 최저 가격의 pool(비용 최적화, 짧은 워크로드)
  - 변화가 많은: 모든 pool의 분산(사용성 좋은, 긴 워크로드)
  - 용량설정: 인스턴스의 용량 풀
  - 가격용량설정: 최대 용량 + 최저 가격(최고의 방법)

## Section 6: EC2 - Solutions Architect Associate Level

### Private vs Public vs Elastic IP

- 접속 후 `echo "<h1>$(hostname -f)</h1>" > /var/www/html/index.html` 하면 hostname의 private ip주소를 볼 수 있음

### Placement Groups

EC2 인스턴스가 AWS의 물리적 하드웨어에 어떻게 배치될지를 제어하는 기능

누군가가 EC2 인스턴스 대체 정책(Strategy)을 컨트롤하고 싶을 때

1. Placement Groups의 종류

   1. 클러스터(Cluster)

      ![photo/Untitled%205.png](photo/Untitled%205.png)

      - Single AZ에서 저지연성 그룹으로 인스턴스 클러스터링(병렬시스템으로 구축)
      - 장점: 좋은 네트워크(인스턴스 간 10Gbps 대역폭)
      - 단점: rack이 고장나면 모든 인스턴스 동시 고장
      - 사용: 빠르게 완료해야하는 빅데이터, 저지연성, 고효율 네트워크가 필요한 앱

   2. 스프레드(Spread)

      ![photo/Untitled%206.png](photo/Untitled%206.png)

      - 인스턴스를 하드웨어에 따로 분산
      - 장점: 여러 AZ에 분산 배포, 물리적 분리, 동시 실패 리스크 감소
      - 단점: placement group 당 AZ 당 최대 7개
      - 사용: 고가용성이 필요한 앱, 중요한 앱

   3. 파티션(Partition)

      ![photo/Untitled%207.png](photo/Untitled%207.png)

      - 지역 내에 여러 AZ에 인스턴스 분산
      - AZ당 7개까지의 파티션, 파티션 당 100개까지의 인스턴스 배포
      - 다른 rack set의 의존적임
      - 파티션 고장시 많은 EC2 고장, 다른 파티션 영향은 x
      - EC2에서 메타데이터 같은 파티션 정보를 불러올 때
      - 사용: Hadoop, Cassandra, Kafka

2. AWS EC2 -> `Placement groups`를 클릭 -> 정책 생성 -> 그리고 Instance 생성시 `3.Configure Instance`의 `Placement group name` 설정

### ENI(Elastic Network Interfaces)

1. 가상 네트워크 카드, VPC 내에서 EC2 인스턴스에 연결하는 논리적 요소
2. ENI의 속성
   - ENI마다 고유한 MAC 주소가 자동으로 부여됨
   - ENI마다 Primary Private IPv4 반드시 하나의 주소가 있음
   - ENI마다 Secondary Private IPv4 주소를 여러 개 추가할 수 있음
   - 각 Private IPv4 주소마다 하나의 Elastic IP(퍼블릭 IP를 고정)를 연결할 수 있음
   - 서브넷이나 설정에 따라 퍼블릭 IP를 자동으로 할당할 수 있음
   - ENI에 1개 이상의 보안 그룹을 연결할 수 있음
3. ENI는 EC2에서 떼어 다른 인스턴스에 붙일 수 있음
   - 장애가 나도 기존 IP와 설정을 그대로 승계
4. ENI는 생성된 서브넷과 같은 AZ에서만 사용 가능, 다른 AZ로 옮길 수 없음

![photo/Untitled%208.png](photo/Untitled%208.png)

### EC2 Hibernate(절전모드)

EC2의 여러가지 상태

- Stop: EBS 데이터가 남아있음, 다음 시작때 작동
- Terminate: EBS 다 날라감
- Start
  - 첫 시작이면: OS boots를 하고 EC2 유저 데이터 스크립트 실행
  - 두번째 시작이면: OS boots up만
  - 시작 후 app 시작, caches warmed up 등
- Hibernate(절전모드)

  ![photo/Untitled%209.png](photo/Untitled%209.png)

  - In-mermory(RAM) 상태가 보존!
  - Instance boot 스피드가 훨씬 빠름(OS is not stooped, restarted)
  - RAM 상태가 root EBS volume에 쓰여짐, 암호화
  - C3, C4, C5, I3, M3, M4, R3, R4, T2, T3, ... 지원
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

- EBS(Elastic Block Store) Volume은 EC2 인스턴스에 연결하는 네트워크 드라이브
- 비유: 네트워크 USB 스틱과 같음
- 인스턴스 종료 후에도 데이터가 영구 저장 가능
- 동시에 하나의 인스턴스에만 연결 가능 (CCP 수준)
- 가용 영역(AZ)에 종속적 → 같은 리전이라도 다른 AZ로는 직접 이동 불가
- 프리티어: 월 30GB 무료 (General Purpose SSD 또는 Magnetic)

#### EBS Volume

- 네트워크 기반이므로 물리 디스크 아님
- 네트워크를 통해 연결되므로 약간의 지연(latency) 존재
- EC2에서 분리(detach) 후 다른 인스턴스에 빠르게 연결 가능
- **오직 한개의 인스턴스에 하나만** 마운트 가능(SAA 단계에서는)
  - 단 io1/io2 는 같은 AZ 내에서 멀티 마운트 가능
  - 각 인스턴스는 볼륨은 모든 읽기 쓰기 권한을 가짐
  - Must use a file system that’s cluster-aware(not XFS, EX4, etc…)
- 특정 AZ에 종속됨 → us-east-1a 볼륨을 us-east-1b에 연결 불가
  - 이동하려면 반드시 스냅샷(snapshot) 생성 후 복원 필요
- 용량(GB), IOPS를 프로비저닝하고 그에 따라 과금
- 드라이브 용량은 시간이 지나면서 증가시킬 수 있음

- 인스턴스 종료 시 EBS 볼륨 삭제 여부를 제어하는 속성
  - 루트 볼륨(root): 기본적으로 삭제됨 (속성 활성화)
  - 추가 연결된 볼륨(data): 기본적으로 삭제되지 않음 (속성 비활성화)
- 속성은 콘솔 또는 AWS CLI에서 변경 가능
- Use Case: 인스턴스 종료 후에도 루트 볼륨 데이터를 유지하고 싶을 때 설정 변경

![photo/Untitled%2011.png](photo/Untitled%2011.png)

### EBS Snapshots

- 특정 시점의 EBS 볼륨을 백업하는 기능
- 볼륨을 분리하지 않고도 스냅샷 가능 (하지만 권장됨)
- 스냅샷은 다른 AZ나 Region으로 복사 가능
- 특징
  - Archive Tier: 그냥보다 75%정도 저렴, 24~72시간 후 복구 가능
  - Recycle Bin: 실수로 복구했을 때 대비, 1일~1년 이내 복구 가능
  - Fast Snapshot Restore(FSR): 빠르게 스냅샷 복구, 큰 스냅샷 추천, 비쌈

### AMI(Amazon Machine Image)

- AMI는 EC2의 커스터마이제이션임
  - 소프트웨어, 설정, OS, 모니터링 툴 등을 추가해 이미지화
  - 소프트웨어가 미리 패키징됨
  - 빠르게 boot / 환경 설정
- 특정 리전에 종속적으로 생성되지만, 다른 리전으로 복사 가능
- EC2를 런칭하는 방법
  - Public AMI: AWS 제공
  - own AMI: 자체 커스터마이제이션
  - Marketplace AMI: 누군가가 만든 AMI(팔 수 있음)

#### AMI의 절차

![photo/Untitled%2012.png](photo/Untitled%2012.png)

1. EC2 시작, 커스터마이징
2. 데이터 무결성(integrity)를 위해 인스턴스를 멈춤
3. AMI 빌드, 자동으로 EBS 스냅샷도 생성
4. 생성된 AMI를 이용, 동일한 설정 인스턴스를 여러 개 실행 가능

### EC2 Instance Store

- EC2 인스턴스 저장소(EC2 Instance Store)는 물리 서버 디스크 기반
- EBS는 네트워크 드라이브 기반, 성능이 아쉬움
- EC2 인스턴스가 멈추면 저장소는 날라감(ephemeral)
  - 버퍼, 캐쉬, 임시 데이터(scratch data/temporary content)에 적합함
  - 하드웨어 장애시 데이터 손실 위험
  - 백업이나 복구는 사용자 책임

### EBS Volume Types

6개의 EBS 볼륨 타입이 있음

링크 -> <https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html>

#### SSD 타입

- gp2 / gp3(일반 목적의 SSD)
  - 저비용, 범용적 성능, 저지연
  - General purpose(1GB ~ 16TB)
  - 사용 사례: 부팅 볼륨, 가상 데스크탑, 개발/테스트 환경

| 구분                       | **gp2**                                             | **gp3**                                                                |
| -------------------------- | --------------------------------------------------- | ---------------------------------------------------------------------- |
| **스토리지 타입**          | SSD (General Purpose)                               | SSD (General Purpose)                                                  |
| **볼륨 크기 범위**         | 1 GiB \~ 16 TiB                                     | 1 GiB \~ 16 TiB                                                        |
| **기본 IOPS**              | 3 IOPS/GB (볼륨 크기와 비례) 최대 16,000 IOPS       | **3,000 IOPS 고정 (기본)**                                             |
| **Throughput**             | 최대 250 MiB/s (볼륨 크기에 따라 증가)              | **기본 125 MiB/s**, 최대 1,000 MiB/s                                   |
| **IOPS & Throughput 설정** | 볼륨 크기와 종속적 → 따로 조정 불가                 | **독립적으로 조정 가능** IOPS 최대 16,000, Throughput 최대 1,000 MiB/s |
| **성능 특징**              | 볼륨이 작으면 성능이 낮음 크기가 커질수록 성능 향상 | 작은 볼륨도 높은 성능 확보 가능 비용 대비 성능 최적화                  |
| **비용**                   | 크기에 따라 IOPS 성능이 자동 증가 → 비효율 가능     | **더 저렴하고 성능 제어 가능**                                         |

- io1 / io2(SSD)
  - Highest-performance(4GB ~ 64TB)
  - 저지연성 또는 고성능, Database workloads에 적합
  - io1(4GB ~ 16TB), io2 Block Express(4GB ~ 64TB), MAX PIOPS 256,000, IOPS가 16,000 이상
  - IOPS를 수동으로 조절

| 구분                    | **io1**                                                                    | **io2 (Block Express)**                                    |
| ----------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------- |
| **스토리지 타입**       | SSD (Provisioned IOPS SSD)                                                 | SSD (Provisioned IOPS SSD)                                 |
| **볼륨 크기 범위**      | 4 GiB \~ 16 TiB                                                            | 4 GiB \~ 64 TiB                                            |
| **최대 IOPS**           | 최대 **64,000 IOPS** (Nitro EC2 인스턴스) 그 외 인스턴스: 최대 32,000 IOPS | 최대 **256,000 IOPS** (IOPS\:GiB 비율 1,000:1)             |
| **Throughput (대역폭)** | IOPS 비례, 최대 1,000 MiB/s 수준                                           | 최대 4,000 MiB/s (Block Express 기반)                      |
| **지연시간 (Latency)**  | 밀리초 단위 (ms-level)                                                     | **서브 밀리초(sub-ms)** 지연                               |
| **Multi-Attach 지원**   | 지원 (Nitro 인스턴스만)                                                    | **지원 (향상된 성능)**                                     |
| **성능 특징**           | 지정한 PIOPS 성능 제공, 안정적                                             | **더 높은 내구성 (99.999%)**, **최고 성능 및 확장성 제공** |
| **비용**                | 기존 대비 상대적으로 높음                                                  | io1 대비 **비용 효율성 개선**, 고성능 워크로드 최적        |

#### HDD 타입

- st1(HDD)
  - Low cost
  - frequently accessed
  - 125GiB ~ 16TiB
  - Big Data, Data Warehouses, Log Processing
- sc1(HDD)
  - Cold HDD
  - Lowest cost HDD
  - less frequently accessed
- HDD는 부트볼륨으로 사용 불가
- Size, Throughput(처리량), IOPS(I/O Ops Per Sec) 특징

| 구분                      | **st1 (Throughput Optimized HDD)**          | **sc1 (Cold HDD)**                           |
| ------------------------- | ------------------------------------------- | -------------------------------------------- |
| **볼륨 타입**             | HDD (Throughput 최적화)                     | HDD (Cold, 저비용)                           |
| **Boot Volume 가능 여부** | ❌ 불가                                     | ❌ 불가                                      |
| **볼륨 크기 범위**        | 125 GiB \~ 16 TiB                           | 125 GiB \~ 16 TiB                            |
| **최대 Throughput**       | **500 MiB/s**                               | **250 MiB/s**                                |
| **최대 IOPS**             | **500 IOPS**                                | **250 IOPS**                                 |
| **성능 특징**             | 자주 접근되는 대용량 데이터 처리에 최적화   | 접근 빈도가 낮은 데이터에 최저 비용으로 저장 |
| **주요 Use Case**         | 빅데이터 분석, 데이터 웨어하우스, 로그 처리 | 장기 보관, 백업, 거의 접근하지 않는 데이터   |

### EBS Multi-Attach

- **io1 / io2** 타입의 EBS 볼륨만 지원
- **동일 가용 영역(AZ)** 내 최대 **16개 EC2 인스턴스**에 동시에 연결 가능
- 모든 인스턴스가 **읽기/쓰기 권한**을 가짐
- 특징 및 주의사항
  - 고성능 공유 스토리지 제공
  - **클러스터형 Linux 애플리케이션**에서 고가용성 확보
  - **동시 쓰기 충돌**은 애플리케이션 또는 파일 시스템 수준에서 직접 제어해야 함
  - **클러스터 인식 파일 시스템** 필수 (예: GFS2, OCFS2)
  - 일반 파일 시스템 (예: EXT4, XFS)은 사용 불가 – 데이터 손상 위험
- 사용 예시
  - Teradata, Oracle RAC 등 HA 클러스터

![photo/Untitled%2019.png](photo/Untitled%2019.png)

### EBS Encryption

- 암호화 EBS 볼륨을 만들면 아래 자동 적용
  - 볼륨의 내부(at rest) 데이터는 암호화
  - 인스턴스와 볼륨간 전송중인(in transit) 모든 데이터는 암호화
  - 모든 스냅샷도 암호화
  - 스냅샷으로 생성된 새 볼륨도 암호화
- EBS 암호화는 KMS(AES-256)에서 활용
- 암/복호화는 투명하게 다처리(개입x)
- 암호화는 지연(latency) 거의 없음

### 암호화 되지 않은 EBS 암호화하기

1. 비암호화 EBS 볼륨의 스냅샷 생성
2. 해당 스냅샷을 복사하며 암호화
3. 암호화된 스냅샷으로부터 새 EBS 볼륨 생성
4. 새 암호화 볼륨을 기존 인스턴스에 부착

### EFS

EFS(Elastic File System)란? 완전 관리형 NFS(Network File System)

- EC2 인스턴스 여러 대에서 공유 마운트 가능
- Multi-AZ 지원으로 고가용성 보장
- Linux 기반 AMI 전용, Windows와는 호환되지 않음
- POSIX 호환 파일 시스템, 표준 파일 API 사용
- 암호화 지원: KMS 기반 암호화
- 보안 그룹(Security Group)으로 접근 제어
- 자동 스케일링, 용량 계획 불필요
- 비용: gp2 대비 약 3배 높음 (그러나 사용량 기반 과금)
- 사용 사례
  - content 관리(CMS)
  - 파일 공유형 웹사이트(워드프레스 등)
  - 데이터 쉐어링 시스템
  - 워크플로우, 미디어 처리 등 고 병렬 환경

![photo/Untitled%2020.png](photo/Untitled%2020.png)

- 성능
  - 1000s개의 동시 nfs 클라이언트, 10GB+/s 처리량
  - 자동으로 Peta 용량까지 지원
- Storage Classesb
  - 90%까지 할인
  - Storage Tiers
    - Standard: 자주 엑세스 되는 파일
    - Infrequent access: Lifecycle 정책으로 사용이적은 파일 IA로 이동
  - Availability and durability
    - Standard: Multi-AZ, great for prod
    - One Zone: One AZ, dev/backup에 유용, One Zone-IA 호환- Throughput Mode
  - Bursting: 1TB = 50 MiB/s + 최대 ~ 100MiB/s 까지
  - Provisioned: 스토리지 사이즈 당 처리량 ex. 1TB 스토리지당 1GiB/s
  - Elastic(추천): 워크로드에 따라 자동으로 처리량 증감 ex. 3GiB/s 읽기, 1GiB/s 쓰기
- Performance Mode
  - General Purpose: 지연에 민감할 때 사용(web server, CMS)
  - Max I/O: 고효율, 저지연, 고처리량(big data, media processing)

![photo/Untitled%2013.png](photo/Untitled%2013.png)

### EBS vs EFS

![photo/Untitled%2014.png](photo/Untitled%2014.png)

EBS 특징

- 하나의 인스턴스에 연결(io1/io2는 여러개 가능)
- AZ레벨에서 Lock, 옮기고 싶으면 스냅샷 뜨고 복구

![photo/Untitled%2015.png](photo/Untitled%2015.png)

EFS 특징

- 여러 AZ에 약 100개 마운팅 가능
- EFS는 웹사이트 파일을 공유(WordPress), Linux 인스턴스만 가능(POSIX)

## Section 8: High Availability and Scalability: ELB & ASG

### High Availability and Scalability

![photo/Untitled%2016.png](photo/Untitled%2016.png)

- 수직 확장(Vertical Scalability)
  - 인스턴스의 크기 확장, RDS, ElastiCache 등
- 수평 확장(Horizontal, Elasticity Scalability)
  - 인스턴스의 수량 확장, EC2, 최신 앱 등
- 고 가용성(High Availability)
  - 데이터 손실 등 방지, 고 가용성은 수평 확장
  - 예. Auto Scaling Group multi AZ, Load Balancer multi AZ

### ELB(Elastic Load Balancing)

#### Load Balancing & Load Balncer

- 로드 밸런싱이란? 부하 분산, 컴퓨팅 리소스에 들어오는 트래픽을 균형있게 분배
- 로드 밸런스를 사용하는 이유
  - 부하 분산: 부하를 여러 하위 인스턴스 또는 서버에 분산
  - 고가용성: 트래픽 분산, 장애 및 다운타임 방지, 장애를 원활하게 처리
  - DNS 라우팅: 단일 DNS 주소를 통해 여러 서버로 라우팅
  - 세션 유지: 쿠키를 사용해 항상 동일한 서버로 전송, ux 향상
  - SSL 종료: SSL 암호화를 해제, 백엔드 암호화 및 복호화 부담 개선, 속도 개선
  - 헬스 체크: 정기적인 인스턴스 상태 확인
  - 트래픽 분리: 퍼블릭 트래픽과 프라이빗 트래픽 분리

#### ELB(Elastic Load Balancer)

ELB란? Managed된 로드벨런서임

- AWS는 Load Blancer가 잘 작동하게 보장
- AWS가 업그레이드, 유지, 고효율을 유지
- AWS가 관리를 해줘 사용자가 몇개만 구성 변경 가능
- 비용은 저렴하고 엔드쪽에서 많은 효과 발동
- EC2, EC2 Auto Scaling Groups, ECS, ACM, CloudWatch, Route53, WAF, Global Accelerator에 제공

#### Health Checks

- Load Balancer가 잘 작동하는지 확인 하는 것
- 헬스 체크는 port, route로 체크, 200번이 아니면 문제

#### Types of Load Balancer

- Application Load Balancer(ALB)(L7계층): HTTP, HTTPS, WebSocket
- Network Load Balancer(NLB)(L4계층): TCP, TLS, UDP
- Gateway Load Balancer(GWLB)(L3계층): IP protocol
- Classic Load Balancer(L4/7계층): HTTP, HTTPS, TCP, SSL
  - 옛날 서비스로 현재는 종료된 듯

새로운 로드밸런서들이 기능 지원 많이함, internal, external ELB 지원 가능

### Application Load Balancer(ALB)

- Layer7(HTTP)
- 같은 머신에서 여러개의 앱으로 로드 밸런싱, ex. 컨테이너
- HTTP/2 와 WebSocket 지원
- 리다이렉트 지원, ex. HTTP를 HTTPS로
- 다른 그룹에 대해 태이블 라우팅
  - URL path 기반, hostname 기반, Query 스트링, 해더 기반
- ALB는 MSA나 컨테이너 기반 앱에 특화, docker나 ECS 같은
- ECS에서 동적 포트로 리다이렉트해서 포트 매핑
- (참고) 나중에 Hands-On 따라해보기

### Network Load Balancer(NLB)

NLB

- Layer4(TCP & UDP)
- 초당 100만 요청 핸들링
- 저 지연성(~100ms, vs 400 ms for ALB)
- NLB는 AZ마다 고정IP를 가지고 있으며 동적IP 할당 지원, 특정 IP에 접속 유용
- TCP, UDP 트래픽에 대해서 매우 좋은 성능
- (참고) 나중에 Hands-On 따라해보기

타겟 그룹(Target Groups)

- EC2 instances 나 IP Addresses(Private IPs만), 앱 로드밸런서에 타겟팅해서 지원
- 헬스 체크 지원 가능

### Gateway Load Balancer(GWLB)

- TODO

### ELB Sticky Sessions, Cross Zone Load Balancing, SSL Certificates, Connetion Draining

### Auto Scaling Groups(ASG) & Scaling Policies

## Section 9: AWS Fundamentals: RDS + Aurora + ElastiCache

## Section 10: Route 53

## Section 11: Classic Solutions Architecture Discussions

## Section 12: Amazon S3 Introduction

## Section 13: AWS SDK, IAM Roles & Policies

## Section 14: Advanced Amazon S3 & Athena

## Section 15: CloudFront & AWS Global Accelerator

### AWS CloudFront Overview

- CDN: Content Delivery Network
- Edge에서 캐싱컨텐츠를 이용해 읽기 성능 향상
- UX 향상
- 216 개의 글로벌 엣지 로케이션
- DDoS 보호, Web Application Firewall, AWS Shield 설정 가능

### CloudFront Origins

- S3 bucket
  - OAC(Origin Access Control)
- Custom Origin(HTTP)

### CloudFront at a high level

S3 as an Origin

### CloudFront Pricing

- Edge Location 마다 가격이 다름
  - Out to Internet: 북미 = 유럽 < 남미 = 남아프리카, 중동 < 일본 = 오세아니아 < 인도 < 동아시아
  - Out to Origin: 북미 = 유럽 < 남아프리카, 중동 = 일본 = 동아시아 < 오세아니아 < 남미 < 인도
  - All HTTP Methods(per 10,000): 북미 < 유럽 = 남아프리카, 중동 = 일본 = 동아시아 = 인도 <= 오세아니아 < 남아프리카
- 10TB, 40TB, 100TB, 350TB, 524TB, 4PB, Over 5PB 사용시 점점 저렴해짐

### CloudFront vs S3 Cross Region Replication

- CloudFront
  - TODO
- S3 Cross Region Replication
  - TODO

## Section 16: AWS Storage Extras

## Section 17: Decoupling applications: SQS, SNS, Kinesis, Active MQ

## Section 18: Containers on AWS: ECS, Fargate, ECR & EKS

## Section 19: Serverless Overviews from a Solution Architect Perspective

## Section 20: Serverless Solution Architecture Discussions

## Section 21: Databases in AWS

## Section 22: Data & Analytics

## Section 23: Machine Learning

## Section 24: AWS Monitoring & Audit: CloudWatch, CloudTrail & Config

## Section 25: Identity and Access Management (IAM) - Advanced

### AWS Directory Services

Microsoft Active Driectory(AD)란?

- Found on any Windows Server with AD Domain Services
- Database of objects: User, Accounts, Computers, Printers, File Shares, Security Groups
- Centralized security management, create account, assign permissions
- Objects are organized in trees
- A group of trees is a forest
- AD 도메인 서비스가 설치된 윈도우 서버에서 제공

## Section 26: AWS Security & Encryption: KMS, SSM Parameter Store, CloudHSM, Shield, …

## Section 27: Networking - VPC

## Section 28: Disaster Recovery & Migrations

## Section 29: More Solution Architectures

## Section 30: Other Services

## Section 31: WhitePapers and Architectures - AWS Certified Solutions Architect Associate

## Section 32: Preparing for the Exam + Practice Exam - AWS Certified Solutions Architect Associate

## Section 33: Congratulations - AWS Certified Solutions Architect Associate
