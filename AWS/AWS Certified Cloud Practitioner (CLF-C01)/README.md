# AWS Certified Cloud Practitioner (CLF-C01)

- 21-07-20 ~ 21-07-26(Finished)
- [링크](https://learn.acloud.guru/course/aws--certified-cloud-practitioner/)

## [summary](./summary.md)

## Tips

## 01 Introduction

- 시험 가이드 -> [링크](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)
- Interactive Diagram -> [웹 교재](https://acloudguru.visme.co/view/mxz10wwn-s01-l00-table-of-contents)
- 3장 요약 -> [https://acloudguru.visme.co/view/vdky0j4z-s03-l21-section-review](https://acloudguru.visme.co/view/vdky0j4z-s03-l21-section-review)
- 4장 요약 -> [https://acloudguru.visme.co/view/vdky0j4z-s03-l21-section-review](https://acloudguru.visme.co/view/vdky0j4z-s03-l21-section-review)
- 5장 요약 -> [https://acloudguru.visme.co/view/768pxk4x-s05-l07-section-review-pricing-billing-and-governance](https://acloudguru.visme.co/view/768pxk4x-s05-l07-section-review-pricing-billing-and-governance)

## 02 Foundations of Cloud Computing

### 02-01 Understanding Cloud Computing

1. Learn the categories
   - Lambda and EC2 are compute services.
2. Read the whitepaper
   - Read the "Overview of Amazon Web Services" whitepaper, and review it again the day before your exam.

### 02-02 Exploring the Advantages of Cloud Computing

1. Understand the 6 advantages
   - Explain the 6 advantages and understand how the cloud saves you money.
2. Understand cloud terminology
   - Explain high availability, elasticity, agility, and durability.

### 02-03 Reviewing Cloud Computing and Deployment Models

1. Know the computing models
   - Explain the 3 common cloud computing models.
2. Know the deployment models
   - Explain the differences and understand that hybrid deployments are supported by Direct Connect.

### 02-04 Leveraging the AWS Global Infrastructure

1. Multi-AZ deployments provide high availability.
   - Systems that are highly available are dependable enough to operate continuously without failure.
2. A Region is global and has 2 or more AZs.
   - Regions are geographically isolated locations around the globe.
3. An AZ has multiple data centers.
   - You can think of an AZ as a collection of data centers.
4. Edge locations ensure low latency by placing content closer to users.
   - There are more edge locations than Regions and AZs.

### 02-05 Exploring Your Amazon Web Services (AWS) Account

1. Protect the root user
   - The root user should be protected with MFA.
2. The power of the root user
   - There are certain things that only the root user can do.
3. The CLI
   - Understand what's stored on your local machine to access AWS via the CLI.

## 03 Technology

### 03-01 Section Introduction

### 03-02 Exploring Compute Services: EC2

1. EC2 pricing options
   - Understand On-Demand, Spot, Reserved Instances, Dedicated Hosts, and Savings Plans.
2. Know the types of load balancers
   - Classic, Application, Gateway, and Network
3. Understand real-world usage of EC2 instances
   - Deploying a database or a web application
4. Horizontal scaling vs. vertical scaling
   - Horizontal scaling(or scaling out) adds or replaces instances, while vertical scaling(or scaling up) upgrades an existing instance.
5. Understand the benefits of Auto Scaling
   - Remember Auto Scaling improves the availability of your applications, and don't confuse it with load balancing.
6. Understand how to connect to an EC2 instance from your local machine
   - A key pair is needed to access an EC2 instance from your local machine.

### 03-03 Exploring Compute Services: EC2 in Action

### 03-04 Exploring Compute Services: Lambda

1. Your responsibility
   - You are only responsible for your application code. AWS manages servers, coding environment, and language support.
2. Always free
   - Even after the free-usage tier expires, you'll have access to 1 million free Lambda calls each month.

### 03-05 Exploring Compute Services: Additional Compute Services

1. Fargate
   - AWS Fargate is considered serverless and is used to manage containers.
2. Outposts
   - AWS Outposts supports a hybrid deployment model.
3. Lightsail
   - Amazon Lightsail is a compute service that is used to quickly launch preconfigured applications for small projects.
4. Batch
   - AWS Batch is a compute service that is used to process large workloads in smaller batches.

### 03-06 Leveraging Storage Services: S3

1. S3
   - S3 is a regional service but has a global namespace.
2. S3 storage classes
   - S3 offers unlimited storage with many storage classes. Understand the use cases for each storage class.

### 03-07 Leveraging Storage Services: S3 in Action

### 03-08 Leveraging Storage Services: Additional Storage Services

1. EBS
   - Understand the use cases for EBS.
2. EFS
   - Don't forget EFS only supports Linux file systems.
3. Instance store
   - Don't forget instance store volumes are ephemeral or temporary.
4. Storage Gateway
   - Storage Gateway supports hybrid models.

### 03-09 Understanding Content Delivery Services

1. CloudFront
   - Don't forget CloudFront allows for global distribution of content.
2. Global Accelerator
   - Remember Global Accelerator provides low latency.
3. Security Features
   - Don't forget CloudFront has security features like DDoS protection and geo-restriction.
4. S3 Transfer Acceleration
   - Remember S3 Transfer Acceleration provides fast transfer of files over long distances.

### 03-10 Understanding Networking Services: VPC and Subcomponents

1. VPC
   - Don't forget an internet gateway allows traffic to the public internet and peering connects 2 VPCs together.

### 03-11 Understanding Networking Services: Additional Networking Services

1. Route 53
   - Don't forget Route 53 performs health checks on AWS resources and supports a hybrid model.
2. Direct Connect
   - Remember that Direct Connect supports a hybrid model.
3. Site-to-Site VPN
   - Remember that a Site-to-Site VPN supports a hybrid model. Don't forget to review components such as the virtual private gateway and customer gateway.

### 03-12 Utilizing Databases

1. RDS
   - RDS is only for relational databases. Don't forget the supported database engines: Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server.
2. Aurora
   - Don't forget Aurora only supports PostgreSQL and MySQL.
3. Neptune
   - Don't forget Neptune helps you create social media graphs.
4. DynamoDB
   - Going into the exam, don't forget DynamoDB is a NoSQL database.
5. ElastiCache
   - Keep in mind that ElastiCache is an in-memory datastore.
6. DocumentDB
   - Keep in mind that DocumentDB supports MongoDB.

### 03-13 Exploring Migration and Transfer Services

1. Snowball Edge
   - When going into the exam, don't forget the services natively supported by Snowball Edge, like EC2 and Lambda.
2. Snowball
   - Remember that Snowball transfers petabytes of data and is cheaper than transferring over the internet.
3. Snowmobile
   - Don't forget Snowmobile is the largest member of the transport family and supports exabyte-scale data.
4. DataSync
   - Don't forget DataSync transfers data online and can be used to replicate data cross-Region or cross-account.

### 03-14 Leveraging Analytics Services

1. Athena
   - Going into the exam, don't forget Athena is used to query S3.
2. Redshift
   - Going into the exam, don't forget the real-world use cases of Redshift.

### 03-15 Leveraging Machine Learning Services

1. Comprehend
   - Don't forget Comprehend is used for natural language processing (NLP).
2. Rekognition
   - Don't forget Rekognition processes videos and images.

### 03-16 Understanding Developer Tools

1. CodeCommit
   - Don't forget CodeCommit offers a service similar to GitHub that works with Git repositories.
2. CodeDeploy
   - Remember that CodeDeploy allows you to deploy an application to servers running on-premises and in the cloud.
3. Cloud9
   - Don't forget Cloud9 offers an integrated development environment (IDE) that runs inside a web browser.
4. CodePipeline
   - Don't forget CodePipeline allows you to implement a CI/CD pipeline.

### 03-17 Exploring Deployment and Infrastructure Management Services

1. CloudFormation
   - Don't forget CloudFormation supports infrastructure automation using Infrastructure as Code (IaC).
2. OpsWorks
   - Remember that OpsWorks can deploy applications on-premises, and it also automates infrastructure management using Chef or Puppet.
3. Elastic Beanstalk
   - Don't forget Elastic Beanstalk is only used to deploy applications to the AWS Cloud — it is not used to deploy applications on-premises.

### 03-18 Utilizing Messaging and Integration Services: SQS

1. SQS
   - Don't forget messages in queues are processed in FIFO order.
   - Remember that message queues support loose coupling.

### 03-19 Utilizing Messaging and Integration Services: SNS and SES

1. SNS
   - Don't forget SNS sends text messages and plain text emails.
2. SES
   - Remember that SES sends HTML-formatted emails for marketing campaigns.

### 03-20 Exploring Auditing, Monitoring, and Logging Services

1. CloudWatch
   - Don't forget you can use CloudWatch to monitor your EC2 instances and notify you when certain events occur.
2. CloudTrail
   - Don't forget the things you can track with CloudTrail: username, event time and name, IP address, access key, Region, and error code.

### 03-21 Section Review

## 04 Security and Compliance

### 04-01 Section Introduction

### 04-02 Understanding the Shared Responsibility Model

1. Shared Responsibility Model
   - Going into the exam, remember what you are responsible for and what AWS is responsible for.

### 04-03 Leveraging the Well-Architected Framework

1. Well-Architected Framework
   - Going into the exam, remember the 5 pillars and their real-world use cases.

### 04-04 Understanding IAM Users

1. Users and groups
   - Going into the exam, understand the differences between users and group.
2. Root user tasks
   - Remember the tasks that only the root user can do.
3. Principle of least privilege
   - Don't forget about the principle of least privilege.
4. Real-world use cases
   - Don't forget the real-world use cases for IAM.

### 04-05 Understanding IAM Permissions

1. Users, groups, roles, and policies
   - Going into the exam, understand the differences between users, groups, roles, and policies.
2. IAM best practices
   - Don't forget to familiarize yourself with IAM best practices.
3. Real-world use cases
   - Don't forget the real-world use cases for IAM.
4. IAM credential report
   - Don't forget the importance of the IAM credential report.

### 04-06 Exploring Application Security Services

1. WAF
   - Going into the exam, don't forget WAF protects against SQL injection and cross-site scripting attacks.
2. Shield
   - Don't forget Shield provides DDoS protection and works with CloudFront, Route 53, Elastic Load Balancing, and AWS Global Accelerator.
3. Macie
   - Remember that Macie helps you find sensitive information.

### 04-07 Exploring Additional Security Services

1. Config
   - Remember that Config allows you to identify changes to various resources over time.
2. GuardDuty
   - Don't forget GuardDuty identifies malicious or unauthorized activities in your AWS account.
3. Inspector
   - Don't forget Inspector only works for EC2 instances.
4. Artifact
   - Don't forget Artifact provides you with compliance reports.

### 04-08 Utilizing Data Encryption and Secrets Management Services

1. KMS
   - Going into the exam, don't forget AWS manages KMS keys.
2. CloudHSM
   - Don't forget you manage the keys generated with CloudHSM.
3. Secrets Manager
   - Don't forget Secrets Manager has built-in integration for RDS, Redshift, and DocumentDB.

### 04-09 Section Review

## 05 Pricing, Billing, and Governance

### 05-01 Section Introduction

### 05-02 Understanding AWS Pricing

1. Pricing Calculator
   - Don't forget the Pricing Calculator helps you calculate the TCO.
2. TCO
   - Don't forget the ways a company can reduce their TCO.
3. Pricing
   - Don't forget how pricing is calculated for EC2, Lambda, S3, and RDS.

### 05-03 Understanding Billing Services

1. Budgets
   - Going into the exam, don't forget you can be alerted when your usage exceeds a defined threshold using Budgets.
2. Cost and Usage Report
   - Remember that the Cost and Usage Report provides the most detailed set of AWS cost and usage data available.
3. Cost Explorer
   - Don't forget Cost Explorer helps you visualize and forecast spending.

### 05-04 Exploring Governance Services

1. Organizations
   - Don't forget Organizations saves you money through consolidated billing. Also, remember the importance of SCPs.
2. Control Tower
   - Don't forget Control Tower helps you enforce the best use of services across your organization.
3. Systems Manager
   - Remember that Systems Manager helps you maintain your resources through automatic patching and updates.
4. Trusted Advisor
   - Remember the recommendations made by Trusted Advisor.

### 05-05 Utilizing Management Services

1. Managed Services
   - Don't forget Managed Services augments your staff and helps improve your overall operational efficiency.
2. Marketplace and APN
   - Remember that AWS recognizes partners and providers from these networks.
3. Professional Services
   - Don't forget Professional Services can help you migrate from on-premises to the cloud.

### 05-06 Exploring Support Plans

1. Basic Support
   - Don't forget how to open tickets and the types of tickets you're allowed to open.
2. Developer Support
   - Don't forget how to open tickets and the types of tickets you're allowed to open.
3. Business Support
   - Remember this support plan includes the full set of Trusted Advisor checks.
4. Enterprise Support
   - Remember this support plan includes the full set of Trusted Advisor checks.
   - Don't forget this support plan provides access to a Technical Account Manager (TAM) and the Concierge Support Team.

### 05-07 Section Review

## 06 Conclusion

## Finished 😊
