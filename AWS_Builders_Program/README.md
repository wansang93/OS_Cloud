# AWS Builders 프로그램 온라인 정기 세미나

- 2021-06-21 ~

Link -> [https://aws.amazon.com/ko/events/seminars/aws-builders/](https://aws.amazon.com/ko/events/seminars/aws-builders/)

# [210621] AWS BUILDERS 100 HANDS ON LAB

Link -> [https://aws-builders-kr.workshop.aws/ko/10-intro.html](https://aws-builders-kr.workshop.aws/ko/10-intro.html)

![01-LAB.png](./.assets/01LAB.png)

웹 서버를 구축

|AWS가 없다면?|AWS로 구현|
|:---:|:---:|
|서버 컴퓨터 구매|EC2|
|OS(Windows Server, Linux)|AMI|
|CPU, Memory, Storage|Instance, Storage|
|네트워크 장비 구매|VPC|
|방화벽 장비 구매|Security Group|
|로드벨런서 장비 구매|Load Balancer|

AWS 가입, 한글로 설정, Seoul Region으로 설정

## 3. 네트워크 구성하기

VPC(Virtual Private Cloud)란?
- 사용자가 정의한 가상의 네트워크 공간 안에서 AWS 리소스를 시작
- AWS의 확장 가능한 인프라를 사용한다는 이점과 함께 고객의 데이터 센터에서 운영하는 기존 네트워크와 매우 유사

### 3-1. VPC 생성하기

**VPC 마법사 시작**을 하면 단일 퍼블릭 서브넷이 있는 VPC로 가능

CIDR이란?
- CIDR(Classless Inter-Domain Routing)로 네트워크의 주소와 크기를 표현하는 방식
- 예를 들어 10.0.0.0/16 은 10.0.0.0 + /16 으로 구성
- 네트워크 고정 범위 + 호스트 주소(가변 범위)
- CIDR 블록 서브넷에는 5개의 IP 주소가 예약
  - 0: 네트워크
  - 1: AWS에서 VPC라우터용으로 예약
  - 2: DNS 서버 주소
  - 3: AWS에서 나중에 사용하려고 예약
  - 255: 브로드캐스트 주소

### 3-2. 추가 서브넷 생성하기

서브넷을 하는 이유?
- 고가용성을 확보하기 위해, 다중 가용 역역(AZ)에 서비스를 배포해야 함
- 가용 영역 A 외의 C 영역에 서브넷을 생성

### 3-3. 라우팅 테이블 편집하기

VPC 라우팅 테이블 개념
- 서브넷 또는 게이트 웨이의 네트워크 트래픽이 전송되는 위치를 결정하는데 사용되는 라우팅이라는 규칙 집합이 포함
- **기본 라우팅 테이블**은 VPC와 함께 자동으로 생성되는 라우팅 테이블
  - 명시적으로 연결되지 않은 모든 서브넷의 라우팅을 제어하는 역할
- **사용자 지정 라우팅 테이블**은 기본 라우팅 테이블 외에 사용자가 생성한 라우팅 테이블

### 3-4. 보안 그룹 생성하기

보안 그룹의 역할
- 인스턴스에 대한 인바운드 및 아웃바운드 트래픽을 제어하는 가상 방화벽 역할

## 4. 웹 서버 생성하기

EC2(Elastic Compute Cloud) 이해
- 확장 가능한 컴퓨팅 용량
- 하드웨어 선투자할 필요가 없어 더 빠르게 애플리케이션을 개발하고 배포
- 원하는 만큼 가상 서버를 구축하고 보안 및 네트워크 구성과 스토리지 관리가 가능
- 신속하게 규모를 확장하거나 축소할 수 있어 서버 트래픽 예측 필요성이 줄어듬

### 4-1. 웹 서버 인스턴스 생성하기

쉘 스크립트를 작성하여 인스턴스 생성과 동시에 쉘 스크립트 실행

```bash
#!/bin/sh
yum -y install httpd php mysql php-mysql
chkconfig httpd on
systemctl start httpd
if [ ! -f /var/www/html/immersion-day-app.tar.gz ]; then
   cd /var/www/html
   wget https://kr-id-general.workshop.aws/sh/immersion-day-app.tar.gz
   tar xvfz immersion-day-app.tar.gz
   chown apache:root /var/www/html/rds.conf.php
fi
yum -y update
```

### 4-2. AMI 생성하기

Amazon Machine Image(AMI)란?
- 동일한 구성의 인스턴스가 여러 개 필요할 때는 한 AMI를 사용하여 여러 인스턴스를 시작할 수 있음

### 4-3. AMI 기반 인스턴스 생성하기

AMI 기반 인스턴스 생성하면 편하게 Instance를 복붙 가능

## 5. 로드밸런서 구성하기

ELB(Elastic Load Balancing)란?
- 애플리케이션 트래픽을 Amazon EC2 인스턴스, 컨테이너, IP 주소, Lambda 함수, 가상 어플라이언스와 같은 여러 대상에 자동으로 분산
- 단일 가용 영역 또는 여러 가용 영역에서 다양한 애플리케이션 부하를 처리
- Elastic Load Balancing이 제공하는 네 가지 로드 밸런서는 모두 애플리케이션의 내결함성에 필요한 고가용성, 자동 조정, 강력한 보안기능 제공
  - Application Load Balancer(L7)
  - Network Load Balancer(L4)
  - Gateway Load Balancer
  - Classic Load Balancer
