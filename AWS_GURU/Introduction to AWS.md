# Introduction to AWS

- 2021-02-08 ~ 2021-02-22

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
        We have Direct Connect as a way of connecting up your office or connecting up your physical data centers to AWS directly using a dedicated line, dedicated telephone line.
        So instead of going over the internet, you're going over a dedicated line into AWS, and there's a few reasons you want to do that it might be around security but most of the time.
        it's because you need a very reliable internet connection, because you're pushing a lot of data up to AWS and down from AWS, and then you would use Direct Connect.
        ```
  - **Compute**
    - **EC2**
      - EC2 stands for Elastic Compute Cloud.
      - EC2 is simply the virtual machines that run on AWS.
    - **EC2 Container Service**
      - EC2 Container Services is basically a highly scalable, high performance container management service that supports Docker containers.
      - It basically allows you to run applications on a managed cluster of Amazon EC2 instances.
    - **Elastic Beanstalk**
      - If you don't know anything about AWS, and you want to deploy your code up into Amazon Web Services, you can actually just upload it to Elastic Beanstalk.
      - Elastic Beanstalk will then have a look at your code.
    - **Lambda**
      - Lambda is what we call serverless.
      - So you don't actually go into the operating system, you don't do anything with the underlying host at all.
      - It is basically one of the most revolutionary services of cloud computing.
      - You'd be able to login using SSH or RDP, if it was windows. And you'd be able to install things on this.
    - **Lightsail**
      - It's basically out-of-the-box cloud.
      - So if you want a WordPress site or Joomla site, for example, Lightsail will deploy that for you automatically.

# 6. 10,000 ft Overview 2: Storage, Databases, Migration & Analytics

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597867082600-Lesson_04_Storage%2C%20Databases%2C%20Migration%20%26%20Analytics_Introduction%20to%20AWS.pdf)

- **Services**
  - **Storage**
    - **S3**
      - S3 is almost as old as AWS itself.
      - S3 is Simple Storage Service, S, S, S.
      - S3 is always for object-based storage.
      - Just think of it as a virtual disk in the cloud where you can store objects like ppt, pictures, movies or etcetera.
      - What you don't use S3 for is things like, a place to install a database or a place to install an application may be a computer game. This is called object based storage. You'd need block-based storage.
      - Dropbox actually stores all the metadata inside their own data centers. So, metadata is just basically data about data
    - **Glacier**
      - Glacier is a place in which you archive your files from S3 off
      - It's extremely, unbelievably low cost than S3.
      - But You can't access them immediately.
    - **EFS(Elastic File Service)**
      - It's called Elastic File Service.
      - S3 is where you store objects, EFS is file-based storage and you can share it. 
    - **Storage Gateway**
      - Storage Gateway is a way of connecting up S3 to your on-Premise data center or to your headquarters.
      - It can, is normally a virtual machine that you install on-Premise. So you get a virtual machine image and then it communicates with S3.
      - EBS is Elastic Block Store and that's just basically a virtual disk that you attach to your EC2 instances.
  - **Databases**
    - **RDS**
      - RDS is relational database service.
      - We've got MySQL, we've got PostgreSQL, MariaDB, SQL Server, Oracle, and a new beta database technology
called Aurora.
    - **DynamoDB**
      - DynamoDB is basically a NoSQL database.
      - It's really scalable, and it's got super high performance.
    - **RedShift**
      - Redshift is Amazon's data warehousing solution.
      - You wanna basically transfer a copy of your production database over into Redshift. And then in Redshift you can run queries on that data.
    - **Elasticache**
      - Elasticache basically is a way of caching your data in the cloud.
      - It means that that data will be returned much quicker than if you're pulling it from your database.
  - **Migration**
    - **Snowball**
      - The AWS Snowball service uses physical storage devices to transfer large amounts of data between Amazon Simple Storage Service (Amazon S3) and your onsite data storage location at faster-than-internet speeds.
      - Snowball devices are physically rugged devices that are protected by the AWS Key Management Service (AWS KMS).
    - **DMS(Database Migration Service)**
      - AWS Database Migration Service (AWS DMS) is a cloud service that makes it easy to migrate relational databases, data warehouses, NoSQL databases, and other types of data stores.
    - **Server Migration Service(SMS)**
      - SMS stands for Server Migration Services.
      - Basically This does exactly the same as database migration services, but instead of targeting databases, this targets virtual machines, specifically the VMware virtual machines.
  - **Analytics**
    - **Athena**
      - Athena basically allows you to run SQL queries on S3.
      - You can actually run SQL queries on CSV files or JSON files.
    - **EMR(Elastic MapReduce)**
      - Elastic MapReduce(EMR) is used for big data processing and used to process large amounts of data.
      - It's using a framework called Hadoop.
      - There's other frameworks available including Apache spark, Apache HBase, Presto or Flunk.
    - **Cloud Search**
      - Cloud search is a fully managed service that's provided by AWS.
      - If you need to create a search engine for your website or for your application, you know, you can use either cloud search or elastic search.
      - We used to use cloud search ourselves, but then we moved over to Algolia.
      - if you want to, you know, get off AWS and use a third party, I'd definitely recommend Algolia.
    - **Elastic Search**
      - Elastic Search, it's a service that's using an open source framework, but essentially it allows you to create search capabilities within your website or application.
    - **Kinesis**
      - Kinesis is a way of streaming and analyzing real time data, massive scale.
      - You can capture and store terabytes of data per hour.
      - you'd use this for things like financial transactions. You might be wanting to analyze the market or even things like social media streams.
    - **Data Pipeline**
      - It's a service that allows you to move data from one place to another.
    - **Quick Sight**
      - It's a business analytics tool.
      - It helps you create visualizations and rich sort of dashboards for your data that exist in AWS.
      - It can analyze data in S3, in DynamoDB, in RDS, in RedShift, etcetera.

# 7. 10,000 ft Overview 3: Security, Management Tools, Application Services, Developer Tools, Mobile Services & IoT

[PDF Link](https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1597868142858-Lesson_05_Security%2C%20Management%20Tools_Introduction%20to%20AWS.pdf)

- **Services**
  - **Security & Identify**
    - **IAM(Identity Access Management)**
      - IAM is Identity Access Management.
      - This is the fundamental sort of identity and access management service to use AWS.
    - **Inspector**
      - Inspector is an agent that you install on your virtual machines and it basically inspects those virtual machines and it does security reporting as to what's going on.
    - **Certificate Manager**
      - This gives you free SSL certificates for your domain names.
    - **Diretory Services**
      - Directory Service is basically a way of using Active Directory, which you use with Microsoft, with AWS.
    - **WAF(Web Application Firewall)**
      - WAF is Web Application Firewall.
      - Basically this allows you to give application-level protection to your website.
      - Traditionally firewalls will give you network protection, WAFs give you application-level protection.
      - They stop things like SQL injections or cross-site scripting, or basically anyone doing anything dodgy at the application layer.
    - **Artifacts**
      - AWS Artifact provides on-demand downloads of AWS security and compliance documents, such as AWS ISO certifications, Payment Card Industry (PCI), and Service Organization Control (SOC) reports.
  - **Management Tools**
    - **Cloud Watch**
      - Cloud Watch is used to monitor performance of your, basically your AWS environment, in particular things like EC2.
      - You can monitor disk utilization, RAM utilization, CPU utilization, etcetera.
    - **Cloud Formation**
      - Cloud Formation is basically a document that describes your AWS environment.
      - Cloud Formation is a way of turning your infrastructure into code so instead of having physical firewalls, network switches, load balancers, physical servers, etcetera.
    - **Cloud Trail**
      - Cloud Trail is a way of auditing your AWS resources.
    - **Opsworks**
      - OpsWorks is basically a way of automating deployments using Shift.
    - **Config**
      - Config Manager is a way, basically it automatically monitors your environment and gives you warnings when your environment might break specific configurations that you set.
    - **Service Catalog**
      - Service Catalog basically allows you as an enterprise to build out what it is that you authorize within your organization and what services are not authorized, and that's Service Catalog.
    - **Trusted Advisor**
      - It's an automated way of scanning your environment and giving you different tips.
      - Trusted Advisor was actually designed by the AWS solutions architecture team, and basically when they would go into customers environments, they would make a series of ecommendations.
  - **Application Services**
    - **Step Functions**
      - It's a way of visualizing what's going on inside your application or basically what different microservices it's using.
    - **SWF((Simple Work Flow)**
      - Simple Work Flow service is actually what they use in the Amazon fulfillment center, and it's a way of coordinating both automated tasks and human-led tasks.
    - **API Gateway**
      - Basically think of API Gateway as a door.
      - It allows you to create, publish, maintain, and monitor and also secure APIs at scale.
    - **AppStream**
      - It's a way of basically streaming desktop applications to your users.
    - **Elastic Transcoder**
      - Elastic Transcoder basically, you upload a video and it's going to transcode that video into all these different formats.
  - **Developer Tools**
    - **Code Commit**
      - It's a way of, it's a place to store your code securely in the cloud like kinds of GitHub.
    - **Code Build**
      - CodeBuild is a way of compiling your code.
      - It's just a way of compiling your code in different environments.
      - But you pay by the minute for CodeBuild.
    - **Code Deploy**
      - It's a way of deploying you code to your EC2 instances.
      - It does it in a very automated and regulated fashion.
    - **Code Pipeline**
      - CodePipeline is a way of keeping track of all your different basically versions of codes.
  - **Mobile Services**
    - **Mobile Hub**
      - It lets you add, configure, and design features for your mobile apps.
      - This includes things like user authentication, data storage, backend logic, push notifications, content delivery, and analytics.
    - **Cognito**
      - Cognito makes it easy for you to have users sign up and sign into your apps using things like social identity providers.
    - **Device Farm**
      - Basically this enables you to improve the quality of your Android, iOS and Fire OS apps by quickly and securely testing them on hundreds of real smartphones.
    - **Mobile Analytics**
      - This is a service that lets you basically simply and cost-effectively collect and analyze app usage data so it's a way of analyzing your mobile data.
    - **Pinpoint**
      - You use Pinpoint to gather data on what your users are doing with the apps that you've built, where they are in world, how they do different purchases, etcetera.
  - **Business Productivity**
    - **WorkDocs**
      - WorkDocs is a way of securely basically storing your important work documents in the cloud.
    - **WorkMail**
      - Think of it as Exchange for AWS, So it's a way of sending and receiving email.
  - **IOT**
    - It's basically a way of having thousands or millions or billions of devices out there and then keeping track of them.
    - You use IoT gateway.
  - **Desktop & Appstreaming**
    - **Workspaces**
      - WorkSpaces is just Virtual Desktop Infrastructure(VDI).
    - **Appstream 2.0**
      - It's just a way of streaming desktop applications to your users.

# 8. 10,000 ft Overview 4: A.I., Messaging & Conclusion

[PDF Link](https://acloud.guru/learn/aws-certified-solutions-architect-associate?_ga=2.50738218.287293286.1613436486-496063395.1613436486)

- **Services**
  - **A.I.**
    - **Alexa**
      - Alexa is Amazon's voice service in the cloud.
      - You use it, basically, communicate to Alexa using an Echo, and essentially all you're doing is you're talking to Lambda.
      - What drives that service is actually what's inside the Alexa service, and it's called Lex.
    - **Polly**
      - Polly basically takes any text and turns it into voice.
    - **Machine Learning**
      - **Rekognition**
        - You can upload a picture to it, and it will tell you what's in that picture.
  - **Messaging**
    - **SNS(Simple Notification Services)**
      - SNS is Simple Notification Services, this is a way of notifying you, either via email or via text message, for example.
    - **SQS(Simple Queue Service)**
      - Basically, it's a queue system, so you can post jobs to a queue.
      - SQS is a way of decoupling your applications.
    - **SES(Simple Email Service)**
      - Simple Email Service is basically a way of sending and receiving emails using AWS.

# 9. Keep Up to Date with AWS This Week

# Finished 😊
