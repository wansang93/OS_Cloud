# Chapter 2. 클라우드 개념과 기술(Cloud Concepts and Technology)

- AWS 백서에는 아래 내용이 포함되어 있습니다.

## 2-1. 클라우드 컴퓨팅이란?(What is Cloud Computing?)

- AWS White Paper Link -> [https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html)

### 2-1-1. 클라우드 컴퓨팅이란?(What Is Cloud Computing?)

- 컴퓨터 파워, DB, 스토리지, 앱 등 IT 리소스들을 인터넷을 통해 클라우드 서비스 플랫폼을 이용해 사용한 만큼 지불하는 온디멘드(요구하는 만큼 사용) 방식

### 2-1-2. 클라우드 컴퓨팅의 6가지 장점(Six Advantages of Cloud Computing)

- 가용 비용 대비 거래 자본 비용: 필요한 양만큼 비용을 지불
- 대규모 경제 규모의 이점: 클라우드 컴퓨팅을 사용시 낮은 비용 지불
- 예상 사용량 추측 멈춤: 필요하거나 적은 용량으로 액세스, 스케일 업, 스케일 다운 가능
- 속도와 민첩성 향상: 쉽게 속도 증가 향상 가능
- 데이터 센터에 대한 유지비와 운영비를 멈춤: 프로젝트에 포커스를 할 수 있음
- 세계화를 몇분만에 가능: 쉽게 앱을 다양한 지역에 배포 가능

### 2-1-3. 클라우드 컴퓨팅 타입(Cloud Computing Types)

- Infrastructure As A Service(IAAS): 인프라 구축 서비스, ex) EC2
- Platform As A Service(PAAS): 앱을 위한 서비스, ex) Elatic Beanstalk, Lightsail
- Software As A Service(SAAS): 앱 ex) Gmail

### 2-1-4. 클라우드 컴퓨팅 배포 모델(Cloud Computing Deployment Models)

- 퍼블릭(Public): AWS, Azure, GCP 등 모든 것이 클라우드에서 돌아감
- 하이브리드(Hybrid): Public과 Private의 혼합, 예시로 데이터 센터는 우리가 관리, 나머지는 AWS에서 관리
- 프라이빗(Private): On-Premise

### 2-1-5. AWS 시험에 나오는 범위

- AWS Global Infrastructure
- Compute, Storage, Databases
  - EC2, Lambda
  - Relational Database Services(RDS)
  - DynamoDB(NoN Relational Databases)
  - S3(Simple Storage Services), Glacier
- Security, Indentify & Compliance
- AWS cost Management
- Migrations & Transfer, Network & Content Delivery
  - VPC, Route53

### 2-1-tips. 클라우드 컴퓨팅이란?(What Is Cloud Computing?)

- Know the 6 Advantages of Cloud
  - Trade Capital Expense For Variable Expense
  - Benefit from massive economies of scale
  - Stop guessing about capacity
  - Increase speed and agility
  - Stop spending money running and maintaining data centers
  - Go global in minutes
- Know 3 different types of Cloud Computing
  - Infrastructure As A Service(IAAS): EC2
  - Platform As A Service(PAAS): Elatic Beanstalk, Lightsail
  - Software As A Service(SAAS): Gmail
- Know 3 types of Cloud Computing Deployments
  - Public Cloud: AWS, Azure, GCP
  - Hybrid: Mixture of public and private
  - Private Cloud(Or on Premise): You manage it, in your datacenter. Openstack or Vmware

## 2-2. AWS와 세계 둘러보기(Around THe World With AWS)

- AWS Products Link -> [https://aws.amazon.com/products/](https://aws.amazon.com/products/)

### 2-2-1. Introduction to AWS에서 배운 것들을 다시 설명

- AWS Console(2015~2019), 많은 기능들이 있음
- AWS Infrastructure
- Availability Zones, Regions, Edge Location(CDN)
  - Region: 물리적 장소(2~3개로 구성된 가용지역의)
  - AZ: Region은 1개 이상의 AZ로 구성, 다른 AZ로부터 격리(백업용), 전용선 연결로 빠른 속도
  - Edge Locations: AWS의 캐쉬정보가 있는 endpoint, 특히 클라우드프론트(CloudFront)나 아마존 CDN 등으로 구성된 것
  > 참고 블로그 [갓대희](https://goddaehee.tistory.com/178)

### 2-2-tips. AWS와 세계 둘러보기(Around THe World With AWS)

- Understanding the difference between a Region, an Availability Zones(AZ) and an Edge Location
  - A Region is a physical location in the world which consists of two or more Availability Zones(AZ's).
  - An AZ is one or more discrete data centers, each with redundant power, networking and connectivity, housed in separate facilities.
  - Edge Locations are endpoints for AWS which are used for caching content. Typically this consists of CloudFront, Amazon's CDN.
- Choosing the right AWS Region?
  - Data Sovereignty Laws
  - Latency to end users
  - AWS Services

## 2-3. AWS 로그인 하기(Let's Log In To AWS)

- Free Tier 가입하기 링크 -> [https://aws.amazon.com/free](https://aws.amazon.com/free)
- [한도 알람 공지](https://aws.amazon.com/about-aws/whats-new/2017/12/aws-free-tier-usage-alerts-automatically-notify-you-when-you-are-forecasted-to-exceed-your-aws-service-usage-limits/)
- 가입하려면 카드 정보를 입력해야 되서 일단 보류함

### 2-3-tips. AWS 로그인 하기(Let's Log In To AWS)

- Understand the difference support packages
  - Basic: Free
  - Developer: $29 a month(scales based on usage)
  - Business: $100 a month(scales based on usage)
  - Enterprise: $15,000 a month(scales based on usage)

## 2-4. Mac에서 세팅하기(Setting Up On A Mac)

- Windows 유저는 건너 뛰세요
- `bbedit`, `rdp` 프로그램 다운하세요

## 2-5. Windows에서 세팅하기(Setting Up On A Windows PC)

- `putty 64bit`, `notepad++` 다운하세요
- AWS에 로그인하고 가장 가까운 `지역`을 선택하세요
- `EC2`를 클릭하고 `Key Pairs`를 클릭하고 키 생성을 하세요
- 다운로드하고 `putty Generator`에서 키로 로그인하세요

## 2-6. 가격 알람 받기(Setting Up A Billing Alarm)

- AWS 콘솔에서 `CloudWatch`를 클릭하세요
- `Billing`을 클릭하고 `Alarm`을 생성하세요
- Alarm할 돈의 단위, 범위를 설정하세요
- 생성 후 email인증을 하시면 알람 생성이 됩니다

## 2-7. [LAB: Cloud 시작하기! IAM(Identity Access Management)]

IAM이란 여러분이 그룹이나 사용자, 규칙을 만들게 해줘요.

이 랩은 aws.amazon.com에서 로그인하고 진행하세요~

1. AWS 콘솔에서 지역은 `US-East(N.Virginia)` 선택하고 `IAM`을 클릭하세요.
2. Security Status에서 4개의 느낌표를 완료해야 해요
   1. root 계정의 `MFA`를 활성화를 클릭하세요.
      1. `Multi Factor Authentication`의 약자로 보안을 강화하기 위해 `OTP`처럼 2중 보안 체계
      2. MAF 활성화를 클릭하고 `Virtual MFA device`를 클릭하세요. 그러면 앱으로 인증하는 방법입니다.
      3. QR 코드를 입력하고 코드를 입력해 `MFA`를 등록하세요.
   2. IAM 개인 유저를 생성하세요.
      1. IAM users sign-in link의 주소를 수정하고 복사해서 알려주세요.
      2. Manage Users를 누르고 유저를 추가하세요.
      3. 유저가 들어올 수 있는 접근 권한 타입을 설정하세요.
      4. 그룹을 생성해서 유저를 추가하세요. 그룹을 생성할 때는 여러 룰을 설정해 주세요.
         1. 룰은 JSON 형태로 되어있어서 볼 수 있어요.
      5. 태그를 추가해주세요. 부가 정보를 넣을 수 있어요.
      6. 유저를 잘 만들었으면 다른사람에게 email이나 직접 알려줄 수 있어요.
   3. 허가를 내줄 수 있는 그룹을 사용하세요.
      1. IAM 개인 유저에서 그룹을 생성했어요.
   4. IAM 비밀번호 정책을 설정하세요.

### 2-7-tips. [LAB: Cloud 시작하기! IAM(Identity Access Management)]

- IAM
  - IAM stands for **Identity Access Management**.
  - It's **Global**, you do not specify a region when dealing with IAM.
  - When you create a user or group, this is created GLOBALLY

- You can access the AWS platform in 3 ways
  - Via the Console
  - Programatically(Using the Command Line)
  - Using the Software Developers Kit(SDK)

- root account
  - Your root account is the email address you used to set up your AWS account.
  - The root account always has full administrator access.
  - You should not give these account credentials away to anyone.
  - Instead create a user for each individual within your organization.
  - You should always secure this root account using multi-factor authentication.

- group
  - A group is simply a place to store your users.  
  - Your users will inherit all permissions that the group has.  
  - Examples of groups might be developers, system administrators, human resources, finance etc.  

- policies
  - To set the permissions in a group you need to apply a policy to that group.
  - Policies consist of JSON.
  - These are referred to as key value pairs.
  - You have your key, such as name and then the value eg.

## 2-8. IAM 모범 사례(IAM Best Practices)

- Root Account
  - Only use the root account to create your AWS account. Do not use it to log in.
- Users
  - One user should equal one real human being. Don't create phantom users.
- User/Groups/Policies
  - Always place users in groups, and then apply policies to the groups. This makes management easier.
- Password Policies
  - Have a strong password rotation policy.
- MFA
  - Always enable MFA wherever possible.
- Roles
  - Use roles to access various other AWS services.
- Access Keys
  - Use access keys for programmatic access to AWS.
- IAM Credential Report
  - Use IAM credential reports to audit the permissions of your users/accounts.

## 2-9. IAM 자격 증명 기록(IAM Credential Reports)

자격 증명 기록으로 모든 유저 정보 리스트
- 비밀번호
  - 비밀번호 활성화 여부
  - 마지막 사용 날짜
  - 마지막 변경 날짜
  - 마지막으로 변경해야 되는 날짜
- 접근키
  - 접근키의 활성화 여부
  - 마지막 사용 날짜
  - 마지막 회전(rotated) 날짜
  - 마지막으로 사용된 서비스
- MFA 활성화 여부

### 2-9-tips. IAM 자격 증명 기록(IAM Credential Reports)

- You can generate and download a **credential repor**t that lists all users in your account.
  - Passwords
  - Access Keys
  - MFA

## 2-10. [LAB: Managing AWS IAM User Permissions Using Groups and Policies]

- [Managing AWS IAM User Permissions Using Groups and Policies](../HandsOnLab/Managing%20AWS%20IAM%20User%20Permissions%20Using%20Groups%20and%20Policies.md)

## 2-11. S3 101

### 2-11-1. S3 기본(S3 - The Basics)

S3란?

S3는 개발이나 IT팀에게 보안, 내구성, 확장성이 뛰어난 오브젝트 스토리지 입니다.
- 파일을 안전하게 보관하는 장소입니다.
- Object 기반 스토리지 입니다.
- 데이터는 다양한 장소와 시설에 분리 보관합니다.

S3의 기본적인 것들
- S3는 Object 기반입니다. 여러분의 파일을 올릴 수 있습니다.
- 파일은 0~5TB까지 가능합니다.
- 무제한 스토리지 입니다.
- 파일은 **Buckets**에 저장됩니다.
- S3는 **universal namespace**입니다. 세계적으로 유일해야 합니다.
  - ex) https://s3-eu-west-1.amazonaws.com/acloudguru
- 성공적으로 업로드 하면 **HTTP 200 code**를 받습니다.

Objects는 그냥 파일입니다. 구성요소들
- Key - 파일 이름
- Value - 내용물
- Version ID - 버전관리의 중요한 것들
- Metadata - 데이터에 대한 데이터(날짜, 크기 등)
- 하위 항목
  - 접근 권한 리스트
  - 토렌트

### 2-11-2. S3의 데이터 일관성 모델(Data Consistency Model For S3)

S3는 어떻게 작동하나요?
- Read after Write consistency for PUTS of new Objects
- Eventual Consistency for overwrite PUTS and DELETES(can take some time to propagate)

다른 말로 하면
- 새 파일(objects)이 생성되고 즉시 읽으면 적절히 잘 읽습니다.
- 파일을 수정하거나 삭제하고 그 파일을 즉시 읽으면 해당 내용이 변경되지 않고 읽어들일 수도 있습니다.(if you update an existing file or delete a file and read it immediately, you may get the older version, or you may not.)
basically changes to objects can take a little bit of time to propagate.

### 2-11-3. S3 - 보장성(S3 - Guarantees)

S3는 아마존의 guarantees를 따릅니다.
- s3 플랫폼의 99.99% 가용성을 위해 구축되요.
- 99.9%의 가용성을 보장해요.
- 99.999999999%의 내구성을 보장해요.

### 2-11-4. S3 - 기능들(S3 - Features)

- 티어별 스토리지 사용 가능(Tiered Storage Available)
- 라이프사이클 관리(Lifecycle Management)
- 버전 관리(Versioning)
- 암호화(Encryption)
- 액세스 제어 목록 및 버킷 정책을 사용해 데이터 보호 기능(Secure your data using Access Control Lists and Bucket Policies)

### 2-11-5. S3 스토리지 클라스(S3 Storage Classes)

참고 링크 -> [https://aws.amazon.com/ko/s3/storage-classes/](https://aws.amazon.com/ko/s3/storage-classes/)

1. S3 Standard
   - 자주 엑세스, 빠르게 처리, 높은 내구성, 가용성
2. S3 - IA(Infrequently Accessed)
   - 자주 엑세스x, 빠르게 처리, retrieval 요금
3. S3 One Zone - IA
   - 단일 AZ에 데이터 저장, 비용 절감
4. S3 Intelligent Tiering
   - 운영 오버헤드 없이 가장 비용이 효과적인 액세스 티어, 머신러닝에 최적화
5. S3 Glacier
   - 저럼, 안정적, 장기 아카이브에 이상적
6. S3 Glacier Deep Archive
   - 가장 저렴한 비용의 스토리지 클래스, 1년에 한 두번 액세스 용, 장기 보관
7. S3 Outpost
   - 온프레미스 AWS Outposts 환경에 객체 스토리지를 제공

### 2-11-6. S3 요금(S3 - Charges)

- 스토리지(Storage)
- 요구(Requests)
- 스토리지 관리 요금(Storage Management Pricing)
- 데이터 전송 요금(Data Transfer Pricing)
- 전송 가속(Transfer Acceleration)
  - 클라우드프론트의 분산된 엣지 로케이션의 이점을 활용한 것!
- 지역 간 복제(Cross Region Replication Pricing)

### 2-11-tips. S3 101

- S3
  - S3 is **Object-based**: i.e. allows you to upload files.
  - Files can be from 0 ~ 5 TB.
  - There is unlimited storage.
  - Files are stored in Buckets.
  - S3 is a universal namespace. That is, names must be unique globally.
  - Not suitable to install an operating system on.
  - Successful uploads will generate a HTTP 200 status code.

- The Key Fundamentals of S3 Are
  - Key(This is simply the name of the object)
  - Value(This is simply the data and is made up of a sequence of bytes)
  - Read after Write consistency for PUTS of new Objects
  - Eventual Consistency for overwrite PUTS and DELETES(can take some time to propagate)

- 7 different storage classes
  - S3 Standard 
  - S3 IA
  - S3 One Zone - IA
  - S3 Intelligent Tiering
  - S3 Glacier
  - S3 Glacier Deep Archive
  - S3 Outposts

![s3_comparison](./images/s3_comparison.png)

## 2-12. [LAB: S3 버킷 만들기(Let's Create An S3 Bucket!)]

이 랩은 aws.amazon.com에서 로그인하고 진행하세요~

1. AWS 콘솔에서 `S3`를 들어가면 지역은 `Global`로 변경되요.
2. `버킷 생성`을 눌러주세요.
   1. 버킷 이름을 정하고, 지역을 설정해주세요.
   2. 환경 옵션은 건너 뛰고 권한은 Public으로 설정하게 `체크`를 풀어주고 생성해주세요.
3. 만든 버킷을 클릭해서 들어가주세요.
4. 업로드 버튼을 눌러서 업로드 해주세요.
   1. 업로드를 한 파일들은 자동으로 프라이빗인거 같아요.
   2. `Actions` 버튼을 클릭해 퍼블릭으로 바꿔주세요.
5. 업로드 한 파일의 속성을 눌러주세요.
   1. 우리가 배운 다양한 설정을 할 수 있어요.

### 2-12-tips. [LAB: S3 버킷 만들기(Let's Create An S3 Bucket!)]

- Bucket
  - Bucket names share **a common name space**. You can't have the same bucket name as someone else.
  - When you view your buckets you biew them **globally** but you can have buckets in **individual regions**.
  - You can replicate the contents of one bucket to another bucket automatically by using **cross region replication**.

- Restricting Bucket Access
  - Bucket Policies - Applies across the whole bucket
  - Object Policies - Applies to individual files
  - IAM Policies to Users & Groups - Applies to Users & Groups

## 2-13. [LAB: S3에서 WebSite 만들기(Let's Create A Website On S3)]

1. AWS 콘솔에서 `S3`를 들어가면 지역은 `Global`로 변경되요.
2. `버킷 생성`을 눌러주세요.
   1. 버킷 이름을 정하고, 지역을 설정해주세요.
   2. 환경 옵션은 건너 뛰고 권한은 Public으로 설정하게 `체크`를 풀어주고 생성해주세요.
3. `index.html` 등의 웹 파일을 업로드 해주세요.
   1. 해당 파일을 클릭하고 `Actions`를 눌러서 퍼블릭으로 바꿔주세요.
4. Bucket Policy를 수정을 누르세요.
   1. 정책을 JSON 파일로 추가해주세요.
   2. 정책의 Resource부분을 버킷 ARN으로 정해주세요.
5. 버킷의 속성을 들어가세요.
   1. 가장 아래에 `Static website hosting`을 클릭해주세요.
   2. index document를 index.html로 설정하세요.
   3. error document를 error.html로 설정하세요.
   4. 변경을 저장하면 새로운 도메인이 있어요.

### 2-13-tips. [LAB: S3에서 WebSite 만들기(Let's Create A Website On S3)]

- bucket
  - You can use bucket polices to make entire S3 buckets public.
  - You can use S3 to host STATIC websites(such as .html). Websites that require database connections such as Wordpress etc cannot be hosted on S3.
  - S3 Scales automatically to meet your demand. Many enterprises will put static websites on S3 when they think there is going to be a large number of requests(such as for a movie preview for example).

## 2-14. S3 버전 관리(S3 Versioning)

## 2-15. CloudFront 탐험하기(Let's Explore CloudFront)

## 2-16. EC2 101

## 2-17. EC2 시작하기(Let's Use EC2)

## 2-18. [LAB: Launching an EC2 instance in a Custom Virtual Private Cloud (VPC)]

## 2-19. 명령어 사용하기(Using The Command Line)

## 2-20. 규칙 사용하기(Using Roles)

## 2-21. 웹 서버 빌드하기(Let's Build A Web Server)

## 2-22. 로드벨런서 사용하기(Let's Use A Load Balancer)

## 2-23. Databases 101

## 2-24. RDS 인스턴스 제공하기(Let's provision an RDS instance)

## 2-25. 자동 규모조정(Autoscaling)

## 2-26. 주소 등록하기(Let's Register A Domain Name)

## 2-27. 엘라스틱 빈토크(Elastic Beanstalk)

## 2-28. 클라우드 포매이션(CloudFormation)

## 2-29. Architecting For The Cloud Best Practices - Part 1

## 2-30. Architecting For The Cloud Best Practices - Part 2

## 2-31. 글로벌 AWS 서비스(Global AWS Services)

## 2-32. 회사에서 구축할 수 있는 AWS 서비스(What AWS Services Can Be Deployed On Premise)

## 2-33. CloudWatch 101

## 2-34. AWS 시스템 매니저(AWS Systems Manager)

## 2-35. 서비스 상태 보기(Service Health Dashboard)

## 2-36. 개인 상태 보기(Personal Health Dashboard)

## 2-37. S3 vs EBS vs EFS

## 2-38. 글로벌 가속기(Global Accelerator)

## 2-39. Cloud Concepts & Technology Summary - Part 1

## 2-40. Cloud Concepts & Technology Summary - Part 2

## 2-41. AWS Certified Cloud Practitioner 2020 - Cloud Concepts And 

## 2-42. Technology Quiz
