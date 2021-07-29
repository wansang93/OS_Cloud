# AWS Certified Solutions Architect Associate 2021

- 2021-07-27 ~

## Sildes

- 교재 링크 -> [https://media.datacumulus.com/aws-saa/AWS%20Certified%20Solutions%20Architect%20Slides%20v4.2.pdf](https://media.datacumulus.com/aws-saa/AWS%20Certified%20Solutions%20Architect%20Slides%20v4.2.pdf)
  - 교재가 정말 잘 되 있음
- 시험 관련 링크 -> [https://aws.amazon.com/certification/certification-prep/](https://aws.amazon.com/certification/certification-prep/)

## Tips

강의를 들으면서 꿀팁을 적어봅니다.

### Section 3: Getting started with AWS

1. AWS에서 UI 개선 중임, 점차 개선 중이라 안바뀐 UI가 있음
2. 왼쪽 위에 버튼 누르면 옛날 버전으로 바뀜

### Section 4: IAM & AWS CLI

1. 서비스를 들어가서 지역을 보면 Global인지 아닌지 알 수 있음
2. 계정@계정은 IAM 계정임을 알 수 있음
3. MFA를 지원하는 3rd-party 장비가 많은게 신기했음, 나는 안 쓸듯
4. AWS CLI windows용 다운 링크 -> [https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)
5. CouldShell은 안되는 지역이 많음(Seoul도 안됨ㅜㅜ)
6. IAM Security Tools은 **Credentials Report**와 **Access Advisor**로 나뉨

### Section 5: EC2 Fundamentals

1. 루트 계정으로 `내 계정`들어가서 내리면 Billing을 공유할 수 있는 설정이 나옴, 거기서 체크해줘야 나중에 다른 유저가 볼 수 있음
2. budget 설정 때 Email 하나당 threshold가 1개여야됨
3. `echo "<h1>$(hostname -f)</h1>" > /var/www/html/index.html` 하면 hostname의 private ip주소를 볼 수 있음
4. 인스턴스 타입 읽는법: m5.2xlarge -> m은 **인스턴스 클래스**, 5는 **제너레이션**, 2xlarnge는 **인스턴스 클래스의 사이즈**
5. 인스턴스 클래스 타입들
   1. Compute용: [C] 컴퓨트의 약자, 배치 프로세싱 워크로드, 게임 서버, 머신러닝, 하이 퍼포먼스 컴퓨터, 웹 서버, 동영상 파일 변환 등
   2. In-Memory용: [R, X, Z] Ram의 약자, 높은 퍼포먼스, DB용, 웹 캐쉬용, 인메모리 DB, 리얼타임에 적합한 앱
   3. Storage용: [I, D, H], OLTP(online transaction processing) 시스템(빈번한 호출), Redis같은 캐쉬 인메모리 DB, 유, Data 웨어하우스 앱, 분산 파일 시스템
6. Security groups은 EC2의 방화벽 역활 -> 포트 열고, 인/아웃 바운드 규칙 설정, IP 인증
7. windows10이상에서 ssh 접속이 가능함, `ssh -i <key_location> <ec2-user>@<ip-address>`로 접속(권한 오류발생)
   1. 이러면 권한 설정 때문에 `chmod` 처럼 권한을 바꿔야 함
   2. 파일에서 오른쪽버튼 `속성` -> `보안` -> `고급` -> `소유자 변경` -> `해당 유저`로 변경
   3. 해당 유저만 권한을 남기고 저장
   4. Full control인지 확인하고 다시 위에 명령어 실행
8. 스팟 인스턴스는 EC2 종료(terminate)해도 다시 생김으로 Spot request를 삭제해야 함

### Section 6: EC2 - Solutions Architect Associate Level

### Section 7: EC2 Instance Storage

### Section 8: High Availability and Scalability: ELB & ASG

### Section 9: AWS Fundamentals: RDS + Aurora + ElastiCache

### Section 10: Route 53

### Section 11: Classic Solutions Architecture Discussions

### Section 12: Amazon S3 Introduction

### Section 13: AWS SDK, IAM Roles & Policies

### Section 14: Advanced Amazon S3 & Athena

### Section 15: CloudFront & AWS Global Accelerator

### Section 16: AWS Storage Extras

### Section 17: Decoupling applications: SQS, SNS, Kinesis, Active MQ

### Section 18: Containers on AWS: ECS, Fargate, ECR & EKS

### Section 19: Serverless Overviews from a Solution Architect Perspective

### Section 20: Serverless Solution Architecture Discussions

### Section 21: Databases in AWS

### Section 22: AWS Monitoring & Audit: CloudWatch, CloudTrail & Config

