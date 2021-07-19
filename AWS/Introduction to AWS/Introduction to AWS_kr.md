# 아마존 웹 서비스(AWS) 기본

- 2021-02-08 ~ 2021-02-22

[링크](https://learn.acloud.guru/course/aws-technical-essentials/dashboard)

# 1. Cloud Guru 및 Linux Academy 과정에 대한 중요 참고 사항

# 2. 소개

[PDF 링크](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597872657910-Lesson_01_Introduction_Introduction%20to%20AWS.pdf)

## 왜 AWS를 배워야 하나요?

- AWS는 세상에서 제일 빠르게 성장하는 컴퓨팅 클라우드 플랫폼입니다.
- 세상에서 가장 큰 퍼블릭 클라우드 컴퓨팅 플랫폼입니다.
  - AWS: 90%, MS: 5%, etc: 5% (2016 PPT 기준)
  - AWS: 33%, MS: 18%, google: 9%, Alibaba, IBM, ...(2분기 2020)
- 점점 더 많은 기관들이 사내IT 에서 AWS로 옮기고 있습니다.
- The AWS certifications are the most popular IT certifications right now
- 현재 AWS 자격증이 IT 자격증에서 가장 유명합니다.
- 포브스 선정 2016년 가장많이 지불한 IT 자격증 1위입니다.

## AWS의 새로운 서비스 발표와 업데이트

정말 많아요, 2016년에는 1000 이상

## 파트너 프로그램

2가지 종류의 파트너 프로그램이 있어요.

1. 기술 파트너: AWS와 상호 작용하는 기술을 제공하는 회사들
   - Alert Logic
   - CloudBerry Lab
   - Sumo Logic
   - Datadog
   - New Relic etc

2. 컨설팅 파트너: AWS에 대해 컨설팅을 제공하는 회사들
   - Logicworks
   - Rackspace
   - Accenture
   - Booz Allen Hamilton
   - Datapipe

## AWS 파트너 프로그램

| 파트너   | 관련 자격증 | 전문 자격증 |
| -------- | ----------- | ----------- |
| 기본     | 2           | 0           |
| 고급     | 4           | 2           |
| 프리미어 | 20          | 8           |

## 서로 잘맞는(Fit together) 시험은 어떻게 되는지

- 협력자 티어(Associate Tier)
  - 공인 솔루션 아키텍쳐(Certified Solutions Architect Associate)
  - 공인 개발자(Certified Developer Associate)
  - 공인 시스템 관리자(Certified Sysops Administrator Associate)
- 전문가 티어(Professional Tier)
  - 솔루션 아키텍쳐 전문가(Certified Solutions Architect Professional)
  - 데브옵스 전문가(Devops Professional)
- 전문성(Speciality)
  - 보안(Security)
  - 고급 네트워킹(Advanced Networking)
  - 빅데이터(Big Data)

## 클라우드 그루란?

- Check out our website https://acloud.guru
- 다음 웹사이트에서 확인하기 -> https://acloud.guru
- 2015년 5월에 설립
- 상호작용의 논의 포럼
- 사이트를 통해 직접 연락

# 3. 최신 정보를 알려줌 - 이번주의 AWS!

AWS는 지속적으로 발전하고 업데이트 됩니다.

아래 링크에서 확인할 수 있어요.

[https://acloud.guru/aws-this-week](https://acloud.guru/aws-this-week)

# 4. AWS 역사

[PDF 링크](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597864276000-Lesson_02_AWS_History_Introduction%20to%20AWS.pdf)

## AWS의 강점

발명하려면 2가지가 필요해요.
1. 많은 실험을 할수 있는 능력
2. 실패한 실험들의 부수적인 피해를 감수할 필요가 없음

> Andy Jassy - CEO AWS

**정말 복잡한 환경에서도 손쉽게 대처가 가능합니다.**

## AWS의 타임라인 요약

- 2003: 크리스 & 벤자민, 논문 발표
- 2004: SQS 공식 출범
- 2006: AWS 공식 출시
- 2007: 180,000명 이상 플랫폼 구축
- 2010: amazon.com 전부가 이전
- 2012: 첫 재개발 컨퍼런스
- 2013: 인증 시작
- 2014: 글로벌 풋프린트를 위해 100% 재생 에너지 사용 달성을 위해 노력
- 2015: AWS 매출 창출: 연간 60억 달러, 전년 대비 90%에 육박

## 가트너의 매직 쿼드런트(Gartner's Magic Quadrant)

AWS는 매직 쿼드런트의 IaaS 부분 5년 연속 1위로 이름을 올렸습니다.

# 5. 10,000 ft 개요 1: 네트워킹 & 컴퓨팅

[PDF 링크](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597866222144-Lesson_03_Networking_and_Compute_Introduction%20to%20AWS.pdf)

- **AWS 글로벌 인프라(AWS Global Infrastructure)**
  - 실제로 AWS의 물리적 인프라입니다.
  - AWS에서 실행되는 물리적 기능입니다.
  - 3가지 영역으로 나누면 지역(Regions), 가용 영역(Availability Zones), 엣지 로케이션(Edge Locations).
  - **지역(Regions)**
    - 지역은 AWS 자원이 존재하는 세계
    - 지리적 영역입니다.
  - **가용 영역(Availability Zones)**
    - 각 지역은 둘 이상의 가용 영역으로 구성
    - 가용 영역은 단순히 데이터 센터입니다.
    - 가용 영역은 기술적으로 데이터 센터의 집합이지만 매우 가까운 시설이며, 각 가용 영역은 다른 가용 영역과 떨어져 있습니다.
  - **엣지 로케이션(Edge Locations)**
    - 엣지 로케이션은 클라우드프론트의 CDN 끝점입니다.
    - CDN은 캐시 또는 캐시하는 방식입니다.
    - CDN이 뭔가요? 링크 -> [https://goddaehee.tistory.com/173](https://goddaehee.tistory.com/173)

- **서비스**
  - **네트워크 및 컨텐츠 제공(Network and Content delivery)**
    - **VPC(Virtual Private Cloud)**
      - 가상 프라이빗 클라우드(Virtual Private Cloud)의 약자입니다.
      - VPC는 가상 데이터 센터와 같습니다.
      - 전 세계 모든 지역에 VPC가 있습니다.
    - **Route 53(라우트 53)**
      - Route 53은 아마존의 DNS 서비스입니다.
      - 53은 DNS 포트입니다.
      - Route 53을 통해 도메인 이름을 등록할 수 있습니다.
    - **CloudFront(클라우드프론트)**
      - CloudFront는 AWS의 스토리지 섹션에 있었습니다.
      - 하지만 지금은 네트워킹 및 컨텐츠 제공으로 전환했습니다.
      - 예시
        ```
        NAT은 전용 전화선을 사용하여 사무실을 연결하거나 물리적 데이터 센터를
        AWS에 직접 연결하는 방법으로 Direct Connect를 제공합니다.
        따라서 인터넷을 통해 이동하는 대신 AWS 전용 라인을 통해 연결합니다.
        몇 가지 이유 중 하나는 보안과 관련된 것일 수 있습니다.
        왜냐하면 매우 안정적인 인터넷 연결이 필요하기 때문입니다.
        AWS에서 AWS로 많은 데이터를 푸쉬하고 Direct Connect를 사용할 수 있기 때문입니다.
        ```
  - **컴퓨트(Compute)**
    - **EC2(EC2)**
      - EC2는 **엘라스틱 컴퓨트 클라우드**(Elastic Compute Cloud)의 줄임말입니다.
      - EC2는 AWS에서 동작하는 간단한 가상 머신입니다.
    - **EC2 컨테이너 서비스(EC2 Container Service)**
      - EC2 컨테이너 서비스는 도커 컨테이너를 지원하는 확장성이 뛰어난 고성능 컨테이너 관리 서비스입니다.
      - 아마존 EC2 인스턴스의 관리된 클러스터에서 앱을 실행할 수 있습니다.
    - **엘라스틱 빈스톡(Elastic Beanstalk)**
      - AWS에 대해 아무것도 모르지만 Amazon Web Services에 코드를 배포하고 싶다면 Elastic Beanstalk에 업로드하면 됩니다.
      - Elastic Beanstalk이 코드를 확인하고 배포합니다.
    - **람다(Lambda)**
      - 람다(Lambda)는 서버리스(serverless)라고 합니다.
      - OS에도 들어가지 않고 기본 호스트에도 전혀 영향을 주지 않습니다.
      - 클라우드 컴퓨팅의 가장 혁신적인 서비스중 하나입니다.
      - Windows에선 SSH나 RDP로 로그인할 수 있습니다. 그리고 이것들을 설치할 수 있습니다.
    - **라이트세일(Lightsail)**
      - 즉시 사용할 수 있는 클라우드입니다.
      - 예를 들어 WordPress 사이트나 Joomla 사이트를 원하면 라이트세일이 자동으로 배포합니다.

# 6. 10,000 ft 개요 2: 저장소, 데이터배이스, 마이크래이션 & 분석

[PDF 링크](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597867082600-Lesson_04_Storage%2C%20Databases%2C%20Migration%20%26%20Analytics_Introduction%20to%20AWS.pdf)

- **서비스**
  - **저장소(Storage)**
    - **S3**
      - S3는 AWS 자체만큼 오래되었습니다.
      - S3는 **심플 스토리지 서비스(Simple Storage Service)**, S, S, S입니다.
      - 객체 기반만 저장하는 저장소(object-based storage)입니다.
      - ppt, 사진, 영화 등의 개체를 저장할 수 있는 클라우드 내 가상 디스크라고 생각해보세요. 이를 객체 기반 저장소라고 합니다.
      - S3는 데이터베이스를 설치하는 장소나 응용 프로그램을 설치하는 장소와 같은 용도로 사용하지 않습니다. 이는 블록 기반 스토리지가 필요합니다.
      - 드롭박스(Dropbox)는 실제로 모든 메타데이터를 자체 데이터 센터 내에 저장합니다. 메타데이터는 데이터에 대한 데이터(날짜, 크기 등)입니다.
    - **글랜시어(Glacier)**
      - 글랜시어는 **S3의 파일들을 아카이브하는 장소**입니다.
      - S3보다 매우 저렴하지만 즉시 접속할 수 없습니다.
    - **EFS(Elastic File Service)**
      - EFS는 **엘라스틱 파일 서비스**(Elastic File Service)입니다.
      - S3는 객체를 저장하는 곳이고 EFS는 파일 기반 스토리지를 공유할 수 있습니다.
    - **스토리지 게이트웨이(Storage Gateway)**
      - 스토리지 게이트웨이는 **S3를 온프레미스 데이터 센터 또는 본사에 연결**을 해줍니다.
      - 온 프레미스 환경에서 설치한 가상머신들을 이미지로 얻어와 S3와 통신합니다.
      - EBS는 엘라스틱 블록 스토어(Elastic Block Store)로 EC2 인스턴스와 연결하는 가상 디스크입니다.
  - **데이터베이스(Databases)**
    - **RDS**
      - RDS는 **관계형 데이터베이스 서비스**입니다.
      - MySQL, PostgreSQL, MariaDB, SQL Server, Oracle과 Aurora라는 새로운 베타 데이터베이스 기술이 있습니다.
    - **다이나모DB(DynamoDB)**
      - DynamoDB는 **NoSQL 데이터베이스**입니다.
      - 확장성과 성능 모두 뛰어납니다.
    - **레드쉬프트(RedShift)**
      - Redshift는 **Amazon의 데이터 웨어하우징 솔루션**입니다.
      - 당신의 상품 데이터베이스의 복사본을 Redshift로 전송하면 해당 데이터를 쿼리로 실행할 수 있습니다.
    - **엘라스틱캐쉬(Elasticache)**
      - Elasticache는 **클라우드에서 데이터를 캐쉬**합니다.
      - 즉 데이터베이스에서 데이터를 가져오는 것 보다 더 빠르게 데이터를 받을 수 있습니다.
  - **마이그레이션(Migration)**
    - **스노우볼(Snowball)**
      - AWS 스노우볼 서비스는 물리적 저장 장치를 사용해 Amazon Simple Storage Service (Amazon S3)와 온사이트 데이터 스토리지 위치 간에 **데이터를 인터넷 속도보다 빠르게 전송**합니다.
      - 스노우볼 디바이스들은 AWS KMS에 의해 보안이 되는 물리적으로 견고한 장치입니다.
    - **DMS(Database Migration Service)**
      - AWS Database Migration Service (AWS DMS)는 관개형 DB, DB 웨어하우스, NoSQL DB와 기타 유형의 **Data 저장소를 쉽게 마이그레이션**할 수 있는 클라우드 서비스입니다.
    - **Server Migration Service(SMS)**
      - SMS는 **서버 마이그레이션 서비스**(Server Migration Services)입니다.
      - 데이터베이스 마이그레이션 서비스와 거의 같지만, 데이터베이스 대신에 VMware같은 가상머신을 대상으로 합니다.
  - **분석(Analytics)**
    - **아테나(Athena)**
      - Athena는 **S3에서 SQL 쿼리를 실행**할 수 있습니다.
      - 실제로 CSV 파일이나 JSON 파일을 SQL 쿼리로 실행할 수 있습니다.
    - **EMR(Elastic MapReduce)**
      - Elastic MapReduce(EMR)는 **빅데이터 처리, 대용량 데이터에 사용**됩니다.
      - 하둡이라는 프레임워크를 사용하고 있습니다.
      - Apache spark, Apache HBase, Presto or Flunk 등의 다른 프레임워크를 사용할 수도 있습니다.
    - **클라우드 검색(Cloud Search)**
      - Cloud search는 AWS에서 완전히 관리되는 서비스입니다.
      - 웹 사이트 또는 응용 프로그램에 대한 **검색 엔진을 생성해야 하는 경우 클라우드 검색이나 엘라스틱 검색을 사용**할 수 있습니다.
      - 우리는 클라우드 검색을 사용했지만 지금은 Algolia(알골리아)로 넘어갔습니다.
      - AWS의 서드 파티를 이용하고 싶다면 Algolia를 추천합니다.
    - **엘라스틱 검색(Elastic Search)**
      - Elastic Search은 오픈 소스 프레임워크이지만 **웹이나 앱 안에 검색 기능**을 만들 수 있습니다.
    - **키네시스(Kinesis)**
      - Kinesis는 **실시간 데이터를 스트리밍하고 분석하는 대규모 확장** 을 도와줍니다.
      - 시간당 테라바이트를 저장하거나 캡처할 수 있습니다.
      - 금융 거래 같은 용도로 사용할 수 있습니다. 시장이나 소셜미디어 스트리밍같은 분석을 원할 때 사용할 수 있습니다.
    - **데이터 파이프라인(Data Pipeline)**
      - **데이터를 한 장소에서 다른 장소로 이동할 수 있는 서비스** 입니다.
    - **퀵 사이트(Quick Sight)**
      - **비즈니스 분석 도구** 입니다.
      - 여러분을 AWS에 존재하는 데이터에 대한 다양한 종류의 대시보드를 만들 수 있습니다.
      - S3, DynamoDB, RDS, RedShift 등에서 데이터를 분석할 수 있습니다.

# 7. 10,000 ft 개요 3: 보안, 관리 도구, 앱 서비스, 개발자 도구, 모바일 서비스 & 사물인터넷

[PDF 링크](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597868142858-Lesson_05_Security%2C%20Management%20Tools_Introduction%20to%20AWS.pdf)

- **서비스**
  - **보안 & 식별**
    - **IAM(Identity Access Management)**
      - IAM **식별 관리 매니저**(Identity Access Management)입니다.
      - AWS를 사용하기 위한 기본적인 ID 및 액세스 관리 서비스입니다.
    - **인스펙터(Inspector)**
      - 인스펙터는 가상 시스템에 설치하는 에이전트며 이러한 **가상 시스템을 검사하고 진행 상황에 대해 보안을 알려줍**니다.
    - **인증서 매니저(Certificate Manager)**
      - **도메인 이름에 대해 SSL 인증서를 무료로 제공**합니다.
    - **디렉토리 서비스(Diretory Services)**
      - Directory Service는 **마이크로소프트에서 사용하는 AD(Active Directory)를 AWS와 함께 사용해** 줍니다.
    - **WAF(Web Application Firewall)**
      - WAF는 **웹 앱 방화벽**(Web Application Firewall)입니다.
      - 웹을 앱(OSI 7)단계에서 보호를 할 수 있습니다.
      - 기존 방화벽은 네트워크(OSI 4)를 보호하며 WAF는 앱단계에서 보호합니다.
      - SQL 인젝션(SQL injections)이나 크로스사이트 스크립팅(cross-site scripting)등 수행하는 모든 사용자를 앱 계층에서 차단합니다.
    - **아티팩츠(Artifacts)**
      - AWS Artifact는 AWS ISO 인증(AWS ISO certifications), 지불 카드 산업(PCI: Payment Card Industry)과 서비스 관리자 컨트롤(SOC: Service Organization Control) 등 **AWS 보안과 규정 문서를 다운로드**를 언제든지 제공해 줍니다.
  - **관리 도구(Management Tools)**
    - **클라우드 워치(Cloud Watch)**
      - Cloud Watch는 **AWS 환경, 특히 EC2와 같은 환경의 성능을 모니터링** 하는데 사용됩니다.
      - disk 사용률, RAM 사용률, CPU 사용률 등을 모니터링 합니다.
    - **클라우드 구성(Cloud Formation)**
      - Cloud Formation은 **AWS의 환경을 설명하는 문서**입니다.
      - Cloud Formation은 물리적 방화벽, 네트워크 스위치, 로드 벨런서, 물리 서버 등을 사용하지 않고 인프라를 코드로 전환하는 방법입니다.
    - **클라우드 트레일(Cloud Trail)**
      - Cloud Trail는 **AWS 리소스를 감사**(auditing)합니다.
    - **옵스워크(Opsworks)**
      - OpsWorks는 **Shift를 사용해 배포를 자동화** 합니다.
    - **구성(Config)**
      - Config Manager는 환경을 **자동으로 모니터링하고 사용자가 설정한 특정 구성을 손상시킬 경우 경고**해 줍니다.
    - **서비스 카탈로그(Service Catalog)**
      - Service Catalog는 기업으로서 **조직 내에서 허가한 내용과 허가되지 않은 서비스를 구축을 지원**합니다.
    - **신뢰 조언자(Trusted Advisor)**
      - **자동으로 환경을 검색하고 다양한 팁을 제공**합니다.
      - Trusted Advisor는 실제로 AWS 솔루션 아키텍처 팀에 의해 설계되었고 고객 환경에 진입할 때는 일련의 권장 사항을 제시합니다.
  - **앱 서비스(Application Services)**
    - **스텝 펑션(Step Functions)**
      - **앱이나 사용중인 다른 마이크로 서비스가 무엇인지 시각화**합니다.
    - **SWF(Simple Work Flow)**
      - 단순 업무 흐름 서비스(Simple Work Flow service)는 아마존의 이행 센터에서 사용하는 서비스이고 **자동화된 업무와 사람이 주도하는 업무 모두를 조정**합니다.
    - **API 게이트웨이(API Gateway)**
      - API 게이트웨이를 문이라고 생각해 보세요.
      - **API를 생성, 게시, 유지 관리 및 모니터링할 수 있고 규모에 맞게 API를 보호**할수 있습니다.
    - **앱스트리밍(AppStream)**
      - **PC의 프로그램을 스트리밍하는 서비스** 입니다.
    - **엘라스틱 트랜스코더(Elastic Transcoder)**
      - Elastic Transcoder는 **비디오를 업로드하면 다양한 형태로 변환**시켜 줍니다.
  - **개발자 도구**
    - **코드 커밋(Code Commit)**
      - GitHub같은 **클라우드에 코드를 안전하게 저장**할 수 있습니다.
    - **코드 빌더(Code Build)**
      - CodeBuild는 **코드를 컴파일** 해줍니다.
      - 여러분의 코드를 다양한 환경에서 컴파일 할수 있습니다.
      - 하지만 코드 빌더를 사용하면 실시간으로 돈을 냅니다.
    - **코드 배포(Code Deploy)**
      - **EC2 인스턴스에 코드를 배포**할 수 있습니다.
      - 자동화되고 제한된 방식으로 동작합니다.
    - **코드 파이프라인(Code Pipeline)**
      - 코드파이프라인은 **코드들의 모든 기본 버전을 추적**해 줍니다.
  - **모바일 서비스(Mobile Services)**
    - **모바일 허브(Mobile Hub)**
      - **모바일 앱의 기능을 추가, 구성, 설계**할 수 있습니다.
      - 유저 인증, 데이터 보관, 백엔드 로직, 알림 설정, 컨텐츠 제공과 분석 등이 있습니다.
    - **코그니토(Cognito)**
      - Cognito는 **소셜 ID같은 기능을 사용해 사용자가 쉽게 앱에 가입하고 로그인**할 수 있습니다.
    - **디바이스 팜(Device Farm)**
      - **수 많은 스마트폰에서 빠르고 안전하게 테스트**해 Android, iOS 나 Fire OS 앱의 질을 올릴 수 있습니다.
    - **모바일 분석(Mobile Analytics)**
      - 간편하고 효율적인 비용으로 **모바일 앱 사용 데이터를 수집 및 분석**할 수 있습니다.
    - **핀포인트(Pinpoint)**
      - 다양한 구매 방법, 사용자가 앱으로 무엇을 하는지, 어디에 있는지 등을 **데이터를 수집**합니다.
  - **비즈니스 생산성(Business Productivity)**
    - **워크독스(WorkDocs)**
      - WorkDocs는 **중요한 업무 문서를 클라우드에 안전하게 저장**합니다.
    - **워크 메일(WorkMail)**
      - **AWS용 email 서비스** 입니다.
  - **사물 인터넷(IOT)**
    - **수십 수백만의 IoT 장치들을 추적**합니다.
    - IoT 게이트웨이를 사용합니다.
  - **데스크탑 & 앱스트리밍(Desktop & Appstreaming)**
    - **워크스페이스(Workspaces)**
      - WorkSpaces는 **가상 데스크탑 인프라**(VDI: Virtual Desktop Infrastructure)입니다.
    - **앱스트리밍 2.0(Appstream 2.0)**
      - **데스크톱 프로그램을 사용자에게 스트리밍** 합니다.

# 8. 10,000 ft 개요 4: 인공지능, 메시지 & 결론

[PDF 링크](https://acloud.guru/learn/aws-certified-solutions-architect-associate?_ga=2.50738218.287293286.1613436486-496063395.1613436486)

- **서비스**
  - **인공지능(A.I.)**
    - **알렉서(Alexa)**
      - Alexa는 **Amazon의 음성 서비스** 입니다.
      - 이 서비스는 사실 Alexa 서비스 안의 Lex입니다.
      - 에코를 사용해 알렉사와 통신합니다. 사실은 여러분들은 람다와 대화합니다.
    - **폴리(Polly)**
      - Polly는 **모든 텍스트를 음성으로 변환**합니다.
    - **머신 러닝(Machine Learning)**
      - **레코니션(Rekognition)**
        - 사진을 업로드하면 **사진에 무엇이 있는지 알려줍**니다.
  - **메시지(Messaging)**
    - **SNS(Simple Notification Services)**
      - SNS는 간단한 알림 서비스(Simple Notification Services)이며 예시로 **이메일이나 문자로 알려줍**니다.
    - **SQS(Simple Queue Service)**
      - 큐 시스템이며 큐에 작업들을 머무르게 할수 있습니다.
      - SQS는 앱과 분리해 관리하게 해줍니다.
    - **SES(Simple Email Service)**
      - 간단한 이메일 서비스(Simple Email Service)는 **AWS를 사용해 이메일을 주고 받습**니다.

# 9. AWS의 이주의 최신 정보 보기

# 끝 😊

번역하고 느낀 점은 영어에서 한글로 매끄럽게 번역이 어려웠습니다.

내가 아는 개념이 영어 영역과 한글 영역이 충돌하는 느낌이 들면서 개념을 더 확실히 잡아야 겠다는 생각이 들었습니다.

번역일이 쉽지 않다는 것을 느꼈지만 이해하는데 큰 도움이 됬습니다.