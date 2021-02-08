# Introduction to AWS

- 2021-02-08

[Link](https://learn.acloud.guru/course/aws-technical-essentials/dashboard)

# 1. An Important Note About A Cloud Guru and Linux Academy Courses

# 2. Introduction

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597872657910-Lesson_01_Introduction_Introduction%20to%20AWS.pdf)

## WHY Learn AWS?

- Fastest growing cloud computing platform on the planet
- Largest public cloud computing platform on the planet
  - AWS: 90%, MS: 5%, etc: 5% (on PPT in 2016)
  - AWS: 33%, MS: 18%, google: 9%, Alibaba, IBM, ...(Q2 2020)
- More and more organisations are outsourcing their IT to AWS
- The AWS certifications are the most popular IT certifications right now
- Top Paid IT Certification for 2016 according to Forbes

## AWS New Service Announcement & Updates

Many Many~, 1000+ in 2016

## The Partner Program

2 different types of partners

1. Technology Partner: People who are provided technology that interact to AWS
   - Alert Logic
   - CloudBerry Lab
   - Sumo Logic
   - Datadog
   - New Relic etc

2. Consulting Partner: People who are provided consulting on AWS
   - Logicworks
   - Rackspace
   - Accenture
   - Booz Allen Hamilton
   - Datapipe

## The AWS Partner Program

| Partner  | Associate Certs | Professional Certs |
| -------- | --------------- | ------------------ |
| Standard | 2               | 0                  |
| Advanced | 4               | 2                  |
| Premier  | 20              | 8                  |

## How The Exams Fit Together

- Associate Tier
  - Certified Solutions Architect Associate
  - Certified Developer Associate
  - Certified Sysops Administrator Associate
- Professional Tier
  - Certified Solutions Architect Professional
  - Devops Professional
- Speciality
  - Security
  - Advanced Networking
  - Big Data

## How The Exams Fit Together

- Developer Associate
- Solutions Architect Associate
- Sysops Administrator Associate
- Security Specialty
- Big Data Specialty
- Devops Pro
- Advanced Networking Specialty
- Solutions Architect Professional

## About A Cloud Guru

- Check out our website https://acloud.guru
- Founded in May 2015
- Interactive Discussion Forums
- Reach us directly via the site

# 3. Keeping Up To Date - AWS This Week!

AWS continuously innovate and update their services.

You can check what's happening below the link.

[https://acloud.guru/aws-this-week](https://acloud.guru/aws-this-week)

# 4. AWS History

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597864276000-Lesson_02_AWS_History_Introduction%20to%20AWS.pdf)

## The Power of AWS

Invention requires two things
1. The ability to try a lot of experiments
2. not having to live with the collateral damage of failed experiments

> Andy Jassy - CEO AWS

**You can literally provision really complex environments**

## A Brief Time Line of AWS

- 2003: Chris & Benjamin present a paper
- 2004: SQS officially launched
- 2006: AWS officially launched
- 2007: over 180,000 devlopers on the platform
- 2010: all of amazon.com moved over
- 2012: First re:Invent Confernce
- 2013: Certifications Launched
- 2014: Committed to achieve 100% renewable energy usage for its global footprint
- 2015: AWS breaks out its revenue: $6 Billion USD per annum and growing close to 90% year on year

## Gartner's Magic Quadrant

AWS was named as a leader in the IaaS Magic Quadrant for the 5th consecutive year.

# 5. 10,000 ft Overview 1: Networking & Compute

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597866222144-Lesson_03_Networking_and_Compute_Introduction%20to%20AWS.pdf)

- **AWS Global Infrastructure**
  - It's the actual physical infrastructure of Amazon Web Services.
  - It's the physical stuff that AWS runs on.
  - We really break it down into three different areas.
  - Regions, Availability Zones, and Edge Locations.
  - **Regions**
    - Region is basically a place in the world where AWS resources exist.
    - Region is a geographical area.
  - **Availability Zones**
    - Each region consists of two or more availability zones.
    - An availability zone is simply a data center.
    - An availability zone could technically be a collection of data centers, but basically they're facilities that are very, very close to each other, and each availability zone is spaced away from another availability zone.
  - **Edge Locations**
    - An edge location is basically a content delivery network(CDN) endpoint for CloudFront.
    - CDN 's a way to cache or to cache
    - What is CDN? (KOR) Link -> [https://goddaehee.tistory.com/173](https://goddaehee.tistory.com/173)

- **Services**
  - **Network and Content delivery**
    - **VPC**
      - It stands for Virtual Private Cloud.
      - VPC is like a virtual data center.
      - You have a VPC in all the different regions around the world.
    - **Route 53**
      - Route 53 is Amazon's DNS service.
      - 53 is the DNS port.
      - You can actually register domain names through Route 53.
    - **CloudFront**
      - CloudFront used to be in the storage section of AWS.
      - But they moved it over to networking and content delivery now.
      - For example
        ```
        We have Direct Connect and Direct Connect as a way of connecting up your office or connecting up your physical data centers to AWS directly using a dedicated line, dedicated telephone line.
        So instead of going over the internet, you're going over a dedicated line into AWS, and there's a few reasons you want to do that it might be around security but most of the time.
        it's because you need a very reliable internet connection, because you're pushing a lot of data up to AWS and down from AWS, and then you would use Direct Connect.
        Direct Connect can come up in the exam here and there.
        It's not a huge feature of the exam, but it can come up.
        It does feature very heavily in the Advanced Networking Specialty Exam.
        ```
  - **Compute**
    - **EC2**
      - EC2 stands for elastic Compute Cloud.
      - EC2 is simply the virtual machines that run on AWS.
    - **EC2 Container Service**
      - EC2 Container Services is basically a highly scalable, high performance container management service that supports Docker containers.
      - It basically allows you to run applications on a managed cluster of Amazon EC2 instances.
    - **Elastic Beanstalk**
      - If you don't know anything about AWS, and you want to deploy your code up into Amazon Web Services, you can actually just upload it to Elastic Beanstalk.
      - Elastic Beanstalk will then have a look at your code.
    - **Lambda**
      - It is basically one of the most revolutionary services of cloud computing.
      - You'd be able to login using SSH or RDP, if it was windows. And you'd be able to install things on this.
      - Lambda is what we call serverless.
      - So you don't actually go into the operating system, you don't do anything with the underlying host at all.
    - **Lightsail**
      - It's basically out-of-the-box cloud.
      - So if you want a WordPress site or Joomla site, for example, Lightsail will deploy that for you automatically.

# 6. 10,000 ft Overview 2: Storage, Databases, Migration & Analytics

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597867082600-Lesson_04_Storage%2C%20Databases%2C%20Migration%20%26%20Analytics_Introduction%20to%20AWS.pdf)

- **Services**
  - **Storage**
    - **S3**
    - **Glacier**
    - **EFS**
    - **Storage Gateway**
  - **Databases**
    - **RDS**
    - **DynamoDB**
    - **RedShift**
    - **Elasticache**
  - **Migration**
    - **Snowball**
    - **DMS**
    - **Server Migration Service(SMS)**
  - **Analytics**
    - **Athena**
    - **EMR**
    - **Cloud Search**
    - **Elastic Search**
    - **Kinesis**
    - **Data Pipeline**
    - **Quick Sight**

# 7. 10,000 ft Overview 3: Security, Management Tools, Application Services, Developer Tools, Mobile Services & IoT

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597868142858-Lesson_05_Security%2C%20Management%20Tools_Introduction%20to%20AWS.pdf)

- **Services**
  - **Security & Identify**
    - **IAM**
    - **Inspector**
    - **Certificate Manager**
    - **Diretory Services**
    - **WAF**
  - **Management Tools**
    - **Cloud Watch**
    - **Cloud Formation**
    - **Cloud Trail**
    - **Cloud Opsworks**
    - **Config**
    - **Service Catalog**
    - **Trusted Advisor**
  - **Application Services**
    - **Step Functions**
    - **SWF**
    - **API Gateway**
    - **AppStream**
    - **Elastic Transcoder**
  - **Developer Tools**
    - **Code Commit**
    - **Code Build**
    - **Code Deploy**
    - **Code Pipeline**
  - **Mobile Services**
    - **Mobile Hub**
    - **Cognito**
    - **Device Farm**
    - **Mobile Analytics**
    - **Pinpoint**
  - **Business Productivity**
    - **WorkDocs**
    - **WorkMail**
  - **IOT**
  - **Desktop & Appstreaming**
    - **Workspaces**
    - **Appstream 2.0**

# 8. 10,000 ft Overview 4: A.I., Messaging & Conclusion

[PDF Link](https://acloud.guru/learn/aws-certified-solutions-architect-associate?_ga=2.50738218.287293286.1613436486-496063395.1613436486)

- **Services**
  - **A.I.**
    - **Lex**
    - **Polly**
    - **Machine Learning**
    - **Rekognition**
  - **Messaging**
    - **SNS**
    - **SQS**
    - **SES**

# 9. Keep Up to Date with AWS This Week

# Finished 😊
