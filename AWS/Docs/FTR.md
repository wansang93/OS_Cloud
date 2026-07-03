# FTR(Foundation Technical Review)

[FTR checklist](https://apn-checklists.s3.amazonaws.com/foundational/index/all/CGFp311uG.html)

## Summary

## CheckList(February 2024 - 2024_q1_v1)

### HOST-001 (Partner Hosted)

Confirm your hosting model.

- [FTR checklist index](https://apn-checklists.s3.amazonaws.com/foundational/index/all/CGFp311uG.html)
- Are the core components of the application (other than CDN, DNS, or Corporate Identify) hosted on AWS or data center you control?

한글 설명

"1. 내용
• 워크로드의 전반적인 아키텍처가 AWS에서 호스팅 된다는 내용
2. 설명
• AWS 외부의 edge 서비스를 (CDN, DNS, 등등) 사용할 경우, 해당
서비스에 대한 설명
• HOST-001.1 – 아키텍처의 주요 컴포넌트가 AWS에서 호스팅 되는지 (Y/N)"

### SUP-001 (Support Level)

Subscribe to the AWS Business Support tier (or higher) for all production AWS accounts or have an action plan to handle issues which require help from AWS Support.

- [AWS Business Support](https://aws.amazon.com/premiumsupport/plans/business/) provides additional benefits
  - [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor)
  - [Personal Health Dashboard](https://aws.amazon.com/premiumsupport/technology/personal-health-dashboard)
- Is your support tier Business or higher on all productions AWS accounts?

"1. 내용
• AWS Business Support 또는 그 이상의 support 티어 구독
2. 설명
• 현재 AWS Support 티어가 무엇인지 (예시: Enterprise Support 사용)
• SUP-001.1 - 모든 프로덕션 AWS 계정에 대한 지원 티어가 비즈니스 또는 그 이상입니까?
(Y/N)"

### WAFR-001 (Architecture Review)

Conduct periodic architecture reviews (minimum once every year).

- Do you do periodic architecture reviews?
- Have you done an architecture review in the last year?
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)

"1. 내용
• 주기적인 아키텍처 검토 수행에 관한 내용
2. 설명
• 아키텍처 검토 프로세스에 대한 간단한 설명
• WAFR-001.1 - 주기적으로 아키텍처 검토를 하십니까? (Y/N)
• WAFR-001.2 – 최근 1년간 아키텍처 검토를 하셨습니까? (Y/N)"

### WAFR-002

Review the AWS Shared Responsibility Model for Security.

- Have you reviewed the AWS Shared Responsibility Models for Security and Resiliency?
- [AWS Shared Responsibility Model for Security](https://docs.aws.amazon.com/whitepapers/latest/aws-risk-and-compliance/shared-responsibility-model.html)
- [AWS Shared Responsibility Model for Resiliency](https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/shared-responsibility-model-for-resiliency.html)
  - We recommend you to use [AWS Resilience Hub](https://aws.amazon.com/resilience-hub/)

"1. 내용
• AWS의 공동 책임 모델 (Shared Responsibility Model) 검토에 관한
내용
2. 설명
• 추가 설명 X
• WAFR-002.1 - AWS의 보안 및 복원력에 대한 공동 책임 모델을 검토하셨습니까? (Y/N)"

### ARC-001 (AWS root account)

- Use root user only by exception.
- Is the AWS root account used for any OTHER tasks than the ones listed in [this link](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html)?
- [best practice](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users)
- [AWS Tasks That Require Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)

"1. 내용
• 루트 사용자를 예외적으로만 사용
2. 설명
• 루트 사용자의 사용 제한 및 관리 방법에 대한 설명
• ARC-001.1 – 링크에 나와있는 시나리오를 제외하고 루트 계정을 사용합니까?
"

아래는 꼭 필요한 경우, 그 이외는 IAM User, Role 기반 관리하기

- Root 계정의 이름, 이메일, 비밀번호, 엑세스 키 관리
- IAM User permissions 권한 관리
- IAM 결제 정보 관리
- AWS Support Plan 변경 및 관리
- S3 버킷 MFA 삭제할 때
- S3 버킷 정책(VPC ID, VPC endpoint ID를 포함)을 수정, 삭제할 때
- 대한민국 미해당
  - GovCloud(미국 정부 클라우드)에 가입할 때
  - RI 마켓플레이스 판매자 등록할 때

### ARC-003

Enable multi-factor authentication (MFA) on the root user for all AWS accounts (CIS 1.5/Security Control IAM.9)

- Is MFA enabled for root user on all accounts (i.e development, test, production, etc.)?
- [virtual MFA](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html#enable-virt-mfa-for-root) or [hardware MFA device](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_physical.html#enable-hw-mfa-for-root)

"1. 내용
• AWS 계정의 루트 사용자 MFA 활성화에 관한 내용
2. 설명
• CIS 통해 증명
• ARC-003.1 - 모든 계정(개발, 테스트, 프로덕션 등)에서 루트 사용자에 대해 MFA가
활성화되어 있습니까? (Y/N)"

### ARC-004

Remove access keys for the root user (CIS 1.4/Security Control IAM.4).

- Do you have access keys provisioned for the root user?

"1. 내용
• 루트 사용자의 액세스 키 제거에 관한 내용
2. 설명
• CIS 통해 증명
• ARC-004.1 - 루트 사용자를 위해 액세스 키가 제공되었습니까? (Y/N)"

### ARC-005

Develop incident management plans.

- Is there a documented process to respond, mitigate, and recover  from security incidents?

Root 계정 사고 대응 가이드 문서화 필요

- 참고자료1 [침해 대응](https://customer.gabia.com/manual/cloud/16801/16840)
- 참고자료2 [침해 대응](https://www.awsstartup.io/security/network-security/account-security-how-to)

"1. 내용
• 루트 계정 인시던트 대응 가이드에 대한 내용
2. 설명
• 추가 설명 x
• ARC-005.1 – 루트 계정 보안 사고에 대응, 완화 및 복구하기 위한 문서화된 프로세스가
있습니까? (Y/N)"

### ACOM-001

Configure AWS account contacts.

- Are AWS alternate contacts configured?

"1. 내용
• AWS 계정 연락처 설정에 관한 내용
2. 설명
• 추가 설명 x
• ACOM-001.1 - AWS 대체 연락처 (alternate contact) 가 구성되어 있습니까? (Y/N)"

### ACOM-002

Set account contact information including the root user email address to email addresses and phone numbers owned by your company.

- Are all of the communication emails including the root user, are configured to use company emails (e.g. no personal / Gmail addresses)?

"1. 내용
• 회사 소유의 이메일 주소와 전화 번호를 사용하여 계정 연락처 정보
설정에 관한 내용
2. 설명
• 추가 설명 x
• ACOM-002.1 - 모든 통신 이메일, 루트 사용자를 포함하여, 회사 이메일을 사용하여
구성되어 있습니까? (예: 개인/gmail 주소는 사용하지 않음) (Y/N)"

### IAM-001 (Identity and Access Management)

Enable multi-factor authentication (MFA) for all Human Identities with AWS access (CIS 1.10/Security Control IAM.5).

- Is MFA enabled for all human users to access AWS accounts? (This may be enabled in your IDP to federate access)

"1. 내용
• 서비스가 아닌 사용자(유저)가 AWS 계정을 엑세스 할때 MFA 활성화
2. 설명
• CIS 통해 증명
• IAM-001.1 - 사용자가 AWS 계정에 액세스하는 데 MFA가 활성화되어 있습니까? (Y/N)"

### IAM-002

Use temporary IAM credentials retrieved by assuming a role whenever possible. (CIS 1.14/Security Control IAM.3)

- Are the credentials and access keys rotated at most every 90 days?
- Do you have a list of all static keys and where they are used?
- Have you implemented monitoring of AWS CloudTrail logs to detect anomalous activity or other potential misuse?
- Do you have a runbook or SOP for revoking credentials in the event you detect misuse?

"1. 내용
• IAM 액세스 키의 정기적인 로테이션
2. 설명
• CIS 통해 증명
• IAM-002.1 - 자격 증명 및 액세스 키를 최대 90일마다 로테이션 합니까? (Y/N)"

### IAM-003

Use strong password policy (CIS 1.8/Security Control IAM.15 and CIS 1.9/Security Control IAM.16).

- Is a strong password policy enforced for users?
- [Setting an Account Password Policy for IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html)

"1. 내용
• 강력한 암호 정책의 시행
2. 설명
• CIS 통해 증명
• IAM-003.1 - 사용자에게 강력한 비밀번호 정책이 강제되고 있습니까? (Y/N)"

### IAM-004

Create individual identities (no shared credentials) for anyone who needs AWS access.

- Does every individual user have their own unique credentials which are not shared with other users?

"1. 내용
• AWS 사용자 한명 당 IAM 유저 한명 생성
2. 설명
• 추가 설명 x
• IAM-004.1 - 모든 개별 사용자가 다른 사용자와 공유되지 않는 고유한 자격 증명을 가지고
있습니까? (Y/N)"

### IAM-005

Use IAM roles and its temporary security credentials to provide access to third parties.

- Are third parties given access to the production workload?
- Do you provide temporary or static credentials?
- [Providing access to AWS accounts owned by third parties](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_third-party.html)

"1. 내용
• 제3자에게 액세스를 제공 할 때 IAM Role 및 임시 보안 자격 증명
(Temporary Credentials) 사용
2. 설명
• 추가 설명 x
• IAM-005.1 - 제3자에게 프로덕션 워크로드 액세스 권한을 부여합니까? (Y/N)
• IAM-005.2 - Temporary 아니면 Static 자격 증명을 제공합니까? (Temporary 자격/Static
증명)
• FTR 통과를 위해선 Temporary를 선택해야함"

### IAM-006

Grant least privilege access (CIS 1.16/Security Control IAM.1).

- Is the principle of least privilege followed while granting access to users?
- You must follow [the standard security advice of granting least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege)

"1. 내용
• 최소 권한 부여 원칙을 따름
2. 설명
• 최소 권한 원칙을 어떻게 따르는지에 대한 간단한 설명
• IAM-006.1 - 사용자에게 액세스 권한을 부여할 때 최소 권한 원칙을 따르고 있습니까? (Y/N)"

### IAM-007

Manage access based on life cycle.

- Is there a policy for when a user leaves the company or changes roles?

"1. 내용
• AWS 사용자 Life Cycle 관리에 대한 내용
2. 설명
• 조직을 떠나거나 역할이 변경될 때 사용자의 액세스 제거 방법에 대한
설명
• IAM-007.1 - 사용자가 회사를 떠나거나 역할을 변경할 때의 정책이 있습니까? (Y/N)"

### IAM-008

Audit identities quarterly.

- Was there an audit conducted for IAM users, roles and permissions in the last quarter?
- Refining permissions in AWS using [last accessed information](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor.html)

"1. 내용
• 정기적인 IAM 사용자, 역할 및 권한에 대한 감사
2. 설명
• 최근 아이덴티티 감사 시기
• IAM-008.1 - 지난 분기에 IAM 사용자, 역할 및 권한에 대한 감사가 수행되었습니까? (Y/N)"

### IAM-009

Do not embed credentials in application code.

- Are there credentials hard-coded in any application code?

"1. 내용
• 어플리케이션 소스 코드에 자격 증명 포함 방지
2. 설명
• 자격 증명 저장 방법에 대한 설명 (예시: 데이터베이스 크리덴셜을 AWS
Secrets Manager에 저장)
• IAM-009.1 - 어플리케이션 코드에 자격증명이 하드코딩 되어 있습니까? (Y/N)"

### IAM-010

Store secrets securely.

- Do you use secret management tools for encryption, access control, access logging?
- We recommend you use a purpose-built secret management service such as [Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html)

"1. 내용
• 시크릿 정보의 안전한 저장
2. 설명
• 사용 중인 시크릿 관리 서비스 및 암호화 방법에 대한 설명 제공
• IAM-010.1 - 암호화, 액세스 제어, 액세스 로깅을 위한 시크릿 관리 도구를 사용합니까?
(Y/N)"

### IAM-011

Encrypt all end user/customer credentials and hash passwords at rest.

- Do you encrypt end-user authentication credentials and passwords at-rest?

"1. 내용
• 데이터베이스에 사용자/고객 자격 증명을 저장하는 경우 자격 증명을
암호화하고 비밀번호를 해시
2. 설명
• 사용 중인 암호화 및 해싱 방법에 대한 설명 제공
• IAM-011.1 - 사용자 비밀번호를 암호화합니까? (Y/N)"

### IAM-012

Use temporary credentials

- Do you use temporary credentials to access AWS accounts or enforce MFA for all human user access?
- Use temporary [security credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html) to access AWS resources.

"1. 내용
• AWS 리소스 액세스를 위한 임시 보안 자격 증명 (Temporary
Credentials) 사용
2. 설명
• Temporary Credential을 사용할 수 없는 경우에, 이에 대한 설명
• IAM-012.1 - AWS에 액세스하기 위해 IAM Role 을 사용하거나 모든 사용자에 대한 MFA를
적용합니까? (Y/N)"

### SECOPS-001 (Operational security)

Perform vulnerability management.

- Is there a process to scan software and patch vulerabilities on a scheduled basis?
- To check for vulnerabilities in software running in Amazon EC2 instances, you can add [Amazon Inspector](https://aws.amazon.com/inspector) to your pipeline to cause your build to fail if Inspector detects vulnerabilities
- You can also use open source products such as [OWASP Dependency-Check](https://owasp.org/www-project-dependency-check/), [Snyk](https://snyk.io/product/open-source-security-management), [OpenVAS](https://www.openvas.org/), package managers and AWS Partner tools for vulnerability management.

"1. 내용
• 취약점 스캔/패치 메커니즘과 빈도에 대한 내용
2. 설명
• 사용된 취약점 관리 도구 및 최근 스캔 결과의 요약 제공
• SECOPS-001.1 - 소프트웨어를 스캔하고 취약점을 패치하는 프로세스가 있습니까? (Y/N)"

### NETSEC-001 (Network Security)

Implement the least permissive rules for all Amazon EC2 security groups.

- Does the default security group restrict all traffic?(CIS 53./Security Control EC2.2)
- Are all security groups configured to not allow ingress from 0.0.0.0/0 to port 22 or 3389?(CIS 5.2)

"1. 내용
• Amazon EC2 보안 그룹에 가장 제한적인 규칙 적용
2. 설명
• CIS 통해 증명
• NETSEC-001.1 - 기본 보안 그룹이 모든 트래픽을 제한합니까? (Y/N)
• NETSEC-001.2 - 모든 보안 그룹이 포트 22 또는 3389로 0.0.0.0/0에서의 수신을 허용하지
않도록 구성되어 있습니까? (Y/N)
• NETSEC-001.3 - 모든 네트워크 ACL이 포트 22 또는 3389로 0.0.0.0/0에서의 수신을
허용하지 않도록 구성되어 있습니까? (Y/N)"

### NETSEC-002

Restrict resources in public subnets.

- Are all of the resources hosted in private subnets?

"1. 내용
• VPC의 Public 서브넷에 리소스 생성을 제한
2. 설명
• Public 서브넷에 리소스를 배포한 경우에, 이에 대한 설명
• NETSEC-002.1 - 모든 리소스가 Private 서브넷에 있습니까? (Y/N)"

### BAR-001 (Backups and recovery)

Configure automatic data backups.

- Is all critical production data backed up automatically?

"1. 내용
• 백업 자동화에 대한 내용
• RDS, EBS, DynamoDB, S3 와 같은 프로덕션 데이터
스토리지/데이터베이스에 대한 자동 복구 구축
• AWS Backup 또는 개별 소프트웨어로 백업 가능
2. 설명
• 현재 데이터를 어디에 저장하고 있고, 백업이 어떻게 진행되는지에 대한
설명
• BAR-001.1 – 중요한 데이터 스토리지/데이터베이스에 자동백업이 진행되는지 (Y/N)"

### BAR-002

Periodically recover data to verify the integrity of your backup process.

- Do you perform periodic recovery of the data?
- Do you test data recovery after making significant changes to the solution?
- [Backup and Restore](https://aws.amazon.com/backup-restore/getting-started/) with AWS

"1. 내용
• 백업 테스트에 대한 내용
• 복구 테스트를 수행하여 백업 프로세스 구현이 RTO 및 RPO를
충족하는지 검증
2. 설명
• 주기적인 데이터 복구 테스트 여부와 프로세스 (진행방식, 주기, 등등)에
대한 간단한 설명
• BAR-002.1 - 주기적인 데이터 복구 테스트가 진행되는지 (Y/N)
• BAR-002.2 - 아키텍쳐 변경 또는 솔루션에 대한 중요한 변경을 가한 후에 데이터 복구
테스트가 진행되는지 (Y/N)"

### RES-001 (Resiliency)

Define a Recovery Point Objective (RPO).

- Is RPO defined for the solution?
- [disaster-recovery-dr-objectives](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/disaster-recovery-dr-objectives.html)

"1. 내용
• Recovery Point Objective (RPO) 에 대한 내용
• RPO는 마지막 데이터 복구 시점 이후 허용되는 최대 시간으로,
마지막 복구 시점과 서비스 중단 시점 사이에 허용되는 데이터
손실량을 의미
2. 설명
• 솔루션의 RPO 제공 (예시: RPO - 6시간)
• RES-001.1 – 솔루션 RPO가 정의 되었는지 (Y/N)"

### RES-002

Establish a Recovery Time Objective (RTO).

- Is RTO defined for the solution?
- [disaster-recovery-dr-objectives](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/disaster-recovery-dr-objectives.html)

"1. 내용
• Recovery Time Objective (RTO) 에 대한 내용
• RTO는 서비스 중단 시점과 서비스 복원 시점 간에 허용되는 최대
지연 시간으로, 서비스를 사용할 수 없는 상태로 허용되는 기간을
의미
2. 설명
• 솔루션의 RTO 제공 (예시: RTO - 2시간)
• RES-002.1 – 솔루션 RTO가 정의 되었는지 (Y/N)"

### RES-004

Resiliency Testing

- Is resiliency testing conducted for the solution?
- You can use [AWS Resilience Hub](https://aws.amazon.com/resilience-hub/) to test and verify your workloads to see if it meets its resilience target.
- AWS Resilience Hub works with [AWS Fault Injection Service (AWS FIS)](https://aws.amazon.com/fis/), a chaos engineering service, to provide fault-injection simulations of real-world failures to validate the application recovers within the resilience targets you defined.

"1. 내용
• 재해 복구(DR) 에 대한 내용
• 프로덕션 환경의 스트레스에 대한 복원력을 가지도록 워크로드를
설계한 후 설계대로 작동하고 예상한 복원력을 제공하는지
주기적으로 테스트 (최소 1년에 한번)
• 데이터 손실, 인스턴스 손상, AZ 장애와 같은 시나리오 포함
2. 설명
• 가장 최근에 진행된 재해복구 테스트 날짜, 결과, 그리고 절차에 대한
간단한 설명
• RES-004.1 – 재해복구 테스트가 진행되는지 (Y/N)"

### RES-005

Communicate customer responsibilities for resilience.

- Is there documentation outlining the responsibilities of the customer for backup, recovery, and availability?
- These responsibilities may be outlined in public sites, or privately communicated to customers as part of onboarding.

"1. 내용
• 솔루션을 사용할때 백업, 복구, 또는 가용성에 대한 책임이 고객에게
있는 경우 이에 대한 내용을 정확히 제시
2. 설명
• 고객 커뮤니케이션에 대한 간단한 설명
• RES-005.1 – 위 내용이 웹사이트 또는 별도 문서를 통해 고객에게 전달 되는지 (Y/N)"

### RES-006

Architect your product to meet availability targets and uptime service level agreements (SLAs).

- Does the solution have SLAs defined for availability and uptime?
- Does your architecture support the SLA?

"1. 내용
• 솔루션의 가용성 목표와 운영 SLA가 정의된 경우, 이를 충족시키기 위해
아키텍처를 설계
2. 설명
• 가용성 목표와 운영 SLA가 정의된 경우 표기
• RES-006.1 – 가용성 목표와 운영 SLA가 정의 되었는지 (Y/N)
• RES-006.2 – 솔루션 아키텍처가 실제로 운영 SLA를 충족 시키게 설계 되었는지 (Y/N)"

### RES-007

Define a customer communication plan for outages.

- Is there a customer communication plan for solution outages?

"1. 내용
• 서비스 장애발생시 고객 커뮤니케이션 계획에 대한 내용
• 서비스 중단 중에 고객과 이해 관계자에게 지속적으로 정보를
제공하는 데 사용할 수 있는 커뮤니케이션 계획을 정의하고 테스트
2. 설명
• 고객 커뮤니케이션에 대한 간단한 설명 (예시: Amazon CloudFront을
통한 오류 응답, Amazon Pinpoint 또는 기타 도구를 사용하여 메시징
캠페인을 자동화, 이메일 커뮤니케이션, 등등)
• RES-007.1 – 장애발생시 커뮤니케이션 계획이 있는지 (Y/N)"

### S3-001 (Amazon S3 bucket access)

Review all Amazon S3 buckets to determine appropriate access levels.

- Is there a process in place to periodically review access levels of S3 buckets?
- When assigning access permissions, follow the [principle of least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege), an AWS best practice. For more information, refer to [overview of managing access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html).

"1. 내용
• S3 버킷의 엑세스 권한을 주기적으로 검토하고, 최소권한만 부여
2. 설명
• S3 버킷을 사용하는 경우에, 버킷 엑세스를 어떻게 관리하고
부여하는지에 대한 간단한 설명
• S3-001.1 – S3 엑세스를 주기적으로 검사하는 프로세스가 있는지 (Y/N)"

### CAA-000 (Cross-account access)

Do you access customer AWS accounts?

- Do you use cross-account roles to access customer AWS accounts?
- [Cross-account roles](https://aws.amazon.com/blogs/apn/securely-accessing-customer-aws-accounts-with-cross-account-iam-roles/)

"1. 내용
• APN 파트너 소프트웨어가 고객의 AWS 계정에 엑세스 해야되는 경우
2. 설명
2. 정적 IAM 자격증명 (엑세스키, 시크릿 엑세스키)이 아닌 크로스 계정 IAM Role을 사용
2. 고객 계정에 크로스 계정 IAM Role을 자동으로 생성 (예시: CloudFormation), 또는
IAM Policy를 고객에게 직접적으로 제공
• 이때, IAM Policy는 최소한의 권한을 가져야함
3. 파트너사에서 생성하고 관리하는 고유 External ID를 사용
4. 고객 제공 IAM 자격증명이 있다면 사용 중단 권장"

### SDAT-000 (Sensitive Data)

- Does the architecture/solution store any PII(Personally Identifiable Information) data?

### SDAT-001

Identify sensitive data (for example, Personally Identifiable Information (PII) and Protected Health Information (PHI))

- Is there a process to perform reviews to classify your data?

"1. 내용
• 민감한 데이터 식별 및 분류에 대한 내용
2. 설명
• 저장하는 민감한 데이터의 종류와 식별/분류 프로세스에 대한 간단한
설명 (예시: PHI 데이터 저장, Glue Data Catalog를 통해 데이터 식별과
엑세스 컨트롤 진행)
• SDAT-001.1 – 데이터 식별 및 분류 프로세스가 있는지? (Y/N)"

### SDAT-002

Encrypt all sensitive data at rest.

- Is all sensitive data being encrypted at rest?

"1. 내용
• 저장 데이터 암호화에 대한 내용
2. 설명
• 저장 데이터 암호화에 대한 간단한 설명 (예시: KMS 키를 사용한 s3
버킷 암호화)
• SDAT-003.1 – 저장 데이터가 암호화 되고 있는지 (Y/N)"

### SDAT-003

Only use protocols with encryption when transmitting sensitive data outside of your VPC.

- Is all sensitive data being encrypted in transit?

"1. 내용
• 전송 데이터 암호화에 대한 내용
2. 설명
• 전송 데이터 암호화에 대한 간단한 설명 (예시: TLS/SSL 자격증을 통한
전송 데이터 암호화)
• SDAT-003.1 – 전송 데이터가 암호화 되고 있는지 (Y/N)"

### RCVP-001 (Regulatory Compliance Validation Process)

Establish a process to ensure that all required compliance standards are met.

- Do you advertise that the solution meets any compliance standards?
- Do you have a process to ensure being compliant with the standards?

"1. 내용
• 규정 준수에 대한 내용
• 솔루션이 특정 규정을 (FEDRAMP, HIPAA, 등등) 준수한다는 내용을
고객에게 알리는 경우에 해당
2. 설명
• 1/ 어떠한 규정을 준수하는지 2/ 규정 준수 검증을 위한 프로세스에
관한 간단한 설명
• RCVP-001.1 – 솔루션이 특정 규정을 (FEDRAMP, HIPAA, 등등) 준수한다는 내용을
광고하는지 (Y/N)
• RCVP-001.2 – 규정 준수를 위한 프로세스가 존재하는지 (Y/N)"

## 자료 조사

- 참고자료
  - [IAM 관리 문서](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
  - [IAM 관리 Youtube](https://www.youtube.com/watch?v=pDg7qxQMNFo)
  - [장기 액세스 키 대안](https://docs.aws.amazon.com/ko_kr/IAM/latest/UserGuide/security-creds.html#sec-alternatives-to-long-term-access-keys)

### 개별 IAM User 생성해서 사용하기

사용자 한 명당 하나의 User 사용, 공유x

### AWS 계정 루트 사용자 액세스 키 사용X, 필요한 경우에만 사용

루트 액세스 키 사용X, IAM -> Security credentials -> Access keys 에서 확인

### IAM User Access Key 주기적 교체

사용자 당 Access Key 2개 가능, 주기적 교체 목적, 교체 시 충분한 테스트 필요 권장

### IAM 그룹에 User를 추가하여 그룹 기반으로 권한 관리하는지?

### 개별 IAM User 최소 권한 할당했는지?

최소 권한의 원칙을 지킬 수 있는 팁 보는 법: 그룹에 들어가서 Access Advisor로 마지막 엑세스 된 서비스 확인

IAM Access Analyzer로 권한이 과도하게 주어진 리소스를 판별

### IAM 사용자가 올바르게 설정되어 있는지 확인하기

Credential Report로 한눈에 확인 가능

### IAM 정책을 잘 작성한건지?

IAM Policy Simulator로 안전하게 IAM 정책을 사전 검증
