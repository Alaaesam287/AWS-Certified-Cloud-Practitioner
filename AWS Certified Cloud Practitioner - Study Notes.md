# DOMAIN 1 — CLOUD CONCEPTS (24%)

Official objectives: 1. Benefits of AWS Cloud 2. AWS design principles 3. Migration strategies 4. Cloud economics
## 1. Cloud Computing Fundamentals

Cloud computing = obtaining computing resources **on demand over the internet**, instead of owning and maintaining all physical infrastructure yourself. Examples: Compute, Storage, Databases, Networking, Security services, Analytics, AI/ML. AWS provides these resources as services.

## 2. Traditional IT vs Cloud

**Traditional/on-premises** — you generally have to: buy hardware, build data centers, maintain servers, provide physical security, manage power/cooling, forecast capacity, replace hardware, pay large upfront costs. **AWS Cloud** — you can: provision resources quickly, pay according to usage, scale resources, automate provisioning, deploy globally, avoid owning physical infrastructure.

## 3. AWS Cloud Value Proposition

- **Agility**: deploy resources quickly.
- **Elasticity**: resources can automatically increase/decrease according to demand.
- **Scalability**: ability to increase capacity to handle growth.
- **High availability**: design systems to remain available despite failures.
- **Global reach**: deploy applications close to customers around the world.
- **Economies of scale**: AWS purchases/operates infrastructure at enormous scale, helping reduce per-unit costs.
- **Pay-as-you-go**: pay for what you consume rather than purchasing infrastructure upfront.
- **Faster time to market**: resources can be provisioned in minutes instead of waiting for hardware procurement.

## 4. CapEx vs OpEx

**CapEx — Capital Expenditure**: money spent upfront on physical infrastructure. Example: buy $100,000 worth of servers.

- Large upfront investment, hardware ownership, capacity planning, long-term commitment

**OpEx — Operational Expenditure**: ongoing operating costs. Cloud commonly shifts organizations toward **variable operational expenditure**. Example: use EC2 for 10 hours → pay for that usage.

> [!tip] Exam pattern If a question says "Avoid large upfront hardware investment", think **Cloud / OpEx / pay-as-you-go**.

## 5. Fixed Cost vs Variable Cost

- **Fixed costs**: remain relatively constant regardless of usage.
- **Variable costs**: change according to consumption. Cloud enables organizations to move toward variable costs.

## 6. Economies of Scale

AWS operates infrastructure at enormous scale, which can produce lower infrastructure cost, better utilization, and lower per-unit costs. This is one reason cloud providers can offer services economically.

## 7. Rightsizing

**Rightsizing = choosing resources appropriate for the workload.** Example: a workload uses only 10% CPU on a very large EC2 instance. Instead of paying for the oversized instance, move to an appropriately sized instance. Goal: **avoid overprovisioning and reduce cost.**

## 8. Automation

Automation can reduce manual work, reduce human error, improve consistency, speed deployment, and reduce operational cost. Important concept: **Infrastructure as Code (IaC)** — instead of manually creating infrastructure, define it in code/templates. Important service: **AWS CloudFormation**.

## 9. AWS Well-Architected Framework

Provides principles for designing and evaluating cloud workloads. Six pillars:

1. **Operational Excellence**
2. **Security**
3. **Reliability**
4. **Performance Efficiency**
5. **Cost Optimization**
6. **Sustainability**

AWS explicitly includes understanding the differences between these pillars in CLF-C02.

- **Operational Excellence**: ability to run and monitor workloads effectively. Focus: operations, monitoring, automation, continuous improvement.
- **Security**: protect data, systems, assets. Focus: IAM, detection, encryption, incident response, least privilege.
- **Reliability**: ability to recover from failures, meet demand, maintain availability. Think: **recovery + resilience + fault tolerance**.
- **Performance Efficiency**: use computing resources efficiently. Think: "How can we get the required performance without unnecessarily wasting resources?"
- **Cost Optimization**: avoid unnecessary spending. Think: rightsizing, appropriate pricing model, eliminating unused resources, monitoring costs.
- **Sustainability**: reduce environmental impact. Think: efficient resource usage, energy efficiency, better utilization.

> [!tip] Exam distinction **Security ≠ Reliability.** Security = prevent/protect/detect security threats. Reliability = continue operating and recover from failures.

## 10. AWS Cloud Adoption Framework (AWS CAF)

Helps organizations plan their cloud transformation. Six perspectives:

- **Business**: strategy, business value, business outcomes
- **People**: organizational roles, skills, culture, training
- **Governance**: policies, processes, risk, compliance
- **Platform**: technology infrastructure, cloud architecture
- **Security**: security controls, identity, detection, incident response
- **Operations**: operating cloud workloads, monitoring, management

AWS expects knowledge of CAF and its benefits such as reduced business risk, improved ESG performance, increased revenue, and improved operational efficiency.

## 11. Cloud Migration

Know the **concept**, not detailed implementation.

- **Retire**: remove applications that are no longer needed.
- **Retain**: keep the workload where it is.
- **Rehost**: "lift and shift." Move to AWS with minimal modification.
- **Replatform**: make some optimizations while keeping the basic architecture.
- **Refactor / Re-architect**: redesign the application to take better advantage of cloud capabilities.
- **Repurchase**: replace the existing solution with another product/service.
- **Relocate**: move workloads to another AWS environment/service with minimal modification.

> [!tip] Exam thinking Minimal modification → **Rehost**. Some optimization → **Replatform**. Major redesign → **Refactor**.

## 12. AWS Migration Services

- **AWS Application Discovery Service**: discover information about on-premises applications and infrastructure for migration planning.
- **AWS Application Migration Service**: migrate applications/servers to AWS.
- **AWS Database Migration Service (DMS)**: migrates databases.
- **AWS Schema Conversion Tool (SCT)**: converts database schemas when migrating between different database engines.
- **Migration Evaluator**: assess migration and estimate costs.
- **AWS Migration Hub**: central place to track migration progress.

## 13. AWS Snow Family

A group of physical devices used to transfer large amounts of data to and from AWS, especially when transferring over the internet is impractical.
- **Snowcone**: small, portable data-transfer and edge-computing device.
- **Snowball Edge**: large-scale data transfer and edge computing.
- **Snowmobile**: truck used to transfer extremely large amounts of data.
Think: **Snow Family = physical data transfer to or from AWS.**

## 14. AWS OpsHub

A graphical application used to set up, manage, and monitor supported Snow Family devices.
Think: **OpsHub = graphical management for Snow devices.**

## 15. AWS DataSync

Automates moving data between on-premises storage and AWS, or between AWS storage services.
Think: **DataSync = automated online data transfer.**

## 16. AWS Data Transfer Terminal

A physical location where customers can bring storage devices and transfer large datasets to AWS using high-speed connectivity.
Think: **Data Transfer Terminal = bring your storage device to an AWS transfer location.**

## 17. Hybrid Cloud

Hybrid deployment = combination of on-premises infrastructure and cloud infrastructure. Useful when an organization cannot immediately move everything, needs to maintain legacy systems, has regulatory requirements, or wants gradual migration.

# DOMAIN 2 — SECURITY & COMPLIANCE (30%)

The **highest-value security domain** and especially relevant to your background. Official objectives: 1. Shared responsibility 2. Security, governance and compliance 3. Access management 4. Security components/resources

## 18. AWS Shared Responsibility Model

Extremely important.

- AWS is responsible for **security OF the cloud**.
- Customer is responsible for **security IN the cloud**.

**AWS responsibility** — underlying infrastructure: physical data centers, physical servers, networking hardware, physical security, hypervisor, infrastructure supporting AWS services. **Customer responsibility** (depends on the service) — IAM configuration, data, user permissions, encryption configuration, OS patching for EC2, security groups, network configuration, application security.

## 19. Responsibility Changes by Service

A major exam concept.

- **EC2**: customer has significant responsibility — guest OS, applications, security configuration, patches, installed software. AWS manages physical infrastructure, hypervisor, underlying hardware.
- **RDS**: AWS manages much more — database infrastructure, OS, database engine maintenance in many managed operations. Customer still manages data, access, permissions, configuration choices, application-side security.
- **Lambda**: AWS manages servers, OS, runtime infrastructure. Customer mainly manages code, permissions, data, application configuration.

> [!tip] Rule Moving from **EC2 → RDS → Lambda** generally means AWS manages more infrastructure.

## 20. Security in AWS

Principles: least privilege, defense in depth, MFA, encryption, monitoring, logging, identity management, network controls, continuous improvement.

## 21. Encryption

- **Encryption at rest**: protects stored data (S3 objects, EBS volumes, databases).
- **Encryption in transit**: protects data moving across networks. Example: **TLS/HTTPS**.

## 22. AWS Key Management Service (KMS)

Used to create and manage encryption keys. Think: **KMS = managed encryption key service**. Used with many AWS services.

## 23. AWS CloudHSM

Provides dedicated hardware security modules. Think: **CloudHSM = dedicated hardware-based cryptographic key storage**. Compared with KMS: KMS = managed AWS key-management service; CloudHSM = dedicated HSM hardware.

## 24. AWS IAM

**Identity and Access Management** controls who can access what and what they are allowed to do. Core concepts: Users, Groups, Roles, Policies.

## 25. IAM User

Represents an AWS identity for a person/application that requires credentials.

## 26. IAM Group

Collection of IAM users. Useful for assigning common permissions. Example: `Developers` → common developer permissions.

## 27. IAM Role

An identity that can be assumed by AWS services, users, applications, or federated identities. Roles are preferred over embedding long-term credentials into applications. Example: EC2 needs access to S3. Better: attach an IAM role to EC2. Instead of: storing access keys inside application code.

## 28. AWS Security Token Service (STS)

Provides temporary security credentials, commonly used when assuming IAM roles, federating users, or accessing resources across accounts. Think: **STS = temporary AWS credentials.**

## 29. IAM Policy

Defines permissions. Conceptually: who can perform what action on which resource under what conditions?

## 30. Managed vs Custom Policies

- **AWS managed policy**: AWS creates/manages the policy.
- **Customer managed policy**: you create and manage it.
- **Inline policy**: embedded directly into a single identity.

## 31. Principle of Least Privilege

Give an identity **only the permissions it actually needs.** Example: application only needs to read from S3. Don't give `AdministratorAccess`; give read-only access to the required bucket/object.

## 32. Root User

Every AWS account has a root user with extremely powerful permissions. Best practices: don't use root for normal tasks, enable MFA, protect root credentials, use IAM identities instead. AWS specifically tests root-user protection.

## 33. MFA

**Multi-Factor Authentication** requires another authentication factor in addition to password/credentials. Examples: password + authenticator, password + hardware security key. Especially important for privileged accounts.

## 34. Access Keys

Used for programmatic access (AWS CLI/API). Consist of an Access key ID and a Secret access key. Never expose credentials in source code, GitHub, or public files.

## 35. IAM Credential Report

A downloadable report showing credential details for IAM users, such as password and access-key status, age, and MFA usage. Think: **Credential Report = review IAM users' credential security.**

## 36. AWS IAM Identity Center

Centralized workforce access to AWS accounts/applications. Useful for employees, SSO, centralized access, federated identities.

## 37. Federation

Allows users to authenticate through an external identity provider. Example: company employees authenticate using corporate identity systems and receive access to AWS.

## 38. AWS Secrets Manager

Stores and manages secrets such as database passwords, API keys, credentials. Can support secret rotation.

## 39. AWS Systems Manager

Operational management capabilities for AWS resources. Examples: Session Manager, patch management, Automation, Parameter Store. For CCP, think: **operational management of AWS resources**.

## 40. Systems Manager Parameter Store

Stores configuration values and parameters, including encrypted values using AWS KMS.
Think: **Parameter Store = centralized configuration and parameter storage.**

**Parameter Store vs Secrets Manager
- **Parameter Store**: configuration data and parameters; can store encrypted values.
- **Secrets Manager**: secrets such as passwords and API keys; supports automatic rotation.

## 41. AWS Organizations

Central management of multiple AWS accounts. Useful for account management, consolidated billing, governance, policies, organizational structure.

## 42. AWS Control Tower

Helps establish and govern a multi-account AWS environment using landing-zone concepts and guardrails. Think: **Control Tower = easier multi-account governance/setup**.

## 43. AWS Resource Access Manager (RAM)

Share supported AWS resources across accounts, Organizations, or OUs. Think: **share AWS resources between accounts**.

## 44. AWS Artifact

Access to AWS compliance documentation and agreements. Think: **Artifact = compliance documents/reports**. Artifact does **not** automatically make your workload compliant.

## 45. AWS Compliance

AWS supports various compliance programs and certifications. Customers remain responsible for determining which regulations apply, how their workload must be configured, and which controls they must implement. Compliance responsibility is shared depending on the workload/service.

## 46. Amazon GuardDuty

Threat detection service. Analyzes signals such as AWS activity, network activity, account behavior. Think: **GuardDuty = threat detection**.

## 47. Amazon Inspector

Automated vulnerability/security assessment. Think: **Inspector = vulnerability/exposure assessment**. Especially useful for EC2, container workloads, Lambda-related vulnerability assessment.

## 48. Amazon Detective

Helps investigate security findings and understand what happened and how entities are related. Think: **GuardDuty detects → Detective investigates**.

## 49. AWS Security Hub

Centralizes and correlates security findings. Think: **Security Hub = central security findings/dashboard**.

## 50. Amazon Macie

Discovers and helps protect sensitive data in Amazon S3. Think: **Macie = sensitive data discovery in S3**.

## 51. AWS WAF

**Web Application Firewall** protects web applications from common web attacks. Works at the application/web layer. Think: **WAF = web traffic filtering**.

## 52. AWS Shield

Protection against DDoS attacks.

- **Shield Standard**: basic DDoS protection included automatically.
- **Shield Advanced**: enhanced DDoS protection and additional capabilities.

Think: **Shield = DDoS protection**.

## 53. AWS Firewall Manager

Central management of firewall/security policies across AWS accounts/resources. Think: **Firewall Manager = centrally manage security policies**.

## 54. AWS Certificate Manager (ACM)

Provision/manage SSL/TLS certificates. Think: **ACM = certificates**.

## 55. Amazon Cognito

Authentication/authorization for applications. Common use: user sign-up, login, application identities. Think: **Cognito = application user authentication**. Don't confuse with IAM: IAM → AWS resource access; Cognito → application end users.

## 56. AWS Directory Service

Managed directory capabilities. Can integrate AWS workloads with directory services such as Microsoft Active Directory.

## 57. AWS CloudTrail

Records AWS API activity. Useful for auditing, investigating actions, tracking who did what. Think: **CloudTrail = API activity/audit trail**.

## 58. Amazon CloudWatch

Monitoring and observability. Can collect/monitor metrics, logs, alarms, application/system information. Think: **CloudWatch = monitoring**.

## 59. AWS Config

Records/evaluates resource configurations and can help assess compliance against rules. Think: **Config = resource configuration/compliance**.

## 60. CloudWatch vs CloudTrail vs Config

Memorize — a classic CCP distinction.

| Service    | Main purpose                      |
| ---------- | --------------------------------- |
| CloudWatch | Monitoring/metrics/logs           |
| CloudTrail | API activity/auditing             |
| Config     | Resource configuration/compliance |

## 61. AWS Trusted Advisor

Recommendations related to cost optimization, performance, security, fault tolerance, service limits/quotas. Think: **Trusted Advisor = recommendations**.

## 62. AWS Health Dashboard

Shows AWS service/account health information relevant to your environment. Think: **AWS Health = AWS events affecting your resources/services**.

## 63. AWS Health API

Programmatic access to AWS Health information.

## 64. AWS Trust & Safety

Used for reporting abuse involving AWS resources.

# DOMAIN 3 — CLOUD TECHNOLOGY & SERVICES (34%)

The **largest domain**. Official sections: 1. Deployment/operations 2. Global infrastructure 3. Compute 4. Databases 5. Networking 6. Storage 7. AI/ML and analytics 8. Other AWS services

## 65. Ways to Access AWS

- **AWS Management Console**: web-based graphical interface. Best for human users, one-time operations, visual management.
- **AWS CLI**: command-line interface. Useful for automation, scripts, programmatic management.
- **AWS SDKs**: libraries for programming languages; allow applications to interact with AWS APIs.
- **APIs**: programmatic interaction with AWS services.
- **Infrastructure as Code**: infrastructure defined through code/templates. Main CCP example: **AWS CloudFormation**.

## 66. One-Time vs Repeatable Operations

If something needs to be done once, the Console may be appropriate. If it needs to happen repeatedly, use Automation / CLI / SDK / IaC. Exam concept: repeatable process → automate it.

## 67. Cloud Deployment Models

- **Cloud**: infrastructure primarily in cloud.
- **On-premises**: infrastructure owned/operated locally.
- **Hybrid**: combination of cloud + on-premises.

## 68. AWS Global Infrastructure

Core concepts: **Regions → Availability Zones → Edge Locations**

## 69. Region

A geographical area containing multiple Availability Zones. Choose a Region based on: latency, compliance/data sovereignty, service availability, cost, disaster recovery.

## 70. Availability Zone (AZ)

An isolated location within an AWS Region. A Region contains multiple AZs. AZs are designed to be isolated from failures in other AZs.

## 71. High Availability

Use multiple AZs so that failure of one AZ does not necessarily take down the application.

```
Load Balancer
      |
  ┌───┴───┐
 AZ-A    AZ-B
 EC2      EC2
```

If AZ-A fails, AZ-B can continue serving traffic.

## 72. Multiple Regions

Useful for disaster recovery, business continuity, global users, lower latency, data sovereignty, regional resilience.

## 73. Edge Locations

Locations used by AWS services such as CloudFront to bring content/services closer to end users. Think: **Edge = closer to users**.

## 74. AWS Wavelength
Provides AWS compute and storage services within telecommunications networks to support very low-latency 5G applications.
Think: **Wavelength = low-latency AWS services close to 5G users.**

## 75. Amazon CloudFront

Content Delivery Network (CDN). Caches content at edge locations. Benefits: lower latency, faster content delivery, reduced load on origin.

## 76. Amazon EC2

**Elastic Compute Cloud** — virtual servers in AWS. You choose: instance type, CPU/memory characteristics, storage, networking, operating system. Use EC2 when you need significant control over the server environment.

## 77. Amazon Machine Image (AMI)

A template containing the information needed to launch an EC2 instance, such as its operating system and software configuration. Think: **AMI = template for launching EC2 instances.**

## 78. EC2 Image Builder

Automates creating, customizing, testing, and maintaining machine images such as AMIs.
Think: **Image Builder = automate building and maintaining AMIs.**

## 79. EC2 Instance Types

Know the major families conceptually.

- **General purpose**: balanced CPU, memory, networking.
- **Compute optimized**: CPU-intensive workloads.
- **Memory optimized**: large-memory workloads.
- **Storage optimized**: high local storage / storage-intensive workloads.
- **Accelerated computing**: GPU/other accelerators.


## 80. EC2 Auto Scaling

Automatically adjusts compute capacity based on demand. Example: normal = 2 instances; high traffic = 10 instances; traffic drops = back to 2. Main benefit: **elasticity**.

## 81. Elastic Load Balancing (ELB)

Distributes incoming traffic across multiple targets. Benefits: high availability, scalability, traffic distribution. Think: **load balancer = distributes traffic**.

## 82. AWS Lambda

Serverless compute. You provide **code**; AWS manages servers, OS, infrastructure, scaling. You pay based largely on invocation/use. Best for event-driven workloads, short-running functions, APIs, automation.

## 83. Serverless

Serverless does **not** mean "there are no servers." It means AWS manages the underlying servers/infrastructure.

## 84. Containers

Containers package applications and dependencies together.

- **Amazon ECS (Elastic Container Service)**: managed container orchestration service.
- **Amazon EKS (Elastic Kubernetes Service)**: managed Kubernetes service.
- **Amazon ECR (Elastic Container Registry)** : container image registry.

Think: ECR = store container images; ECS = run/manage containers; EKS = Kubernetes.

## 85. AWS Fargate

Serverless compute for containers. You don't manage EC2 servers underneath the container workload. Think: **Fargate = run containers without managing servers**.

## 86. AWS Elastic Beanstalk

Platform as a service for deploying applications. AWS manages much of the underlying infrastructure while simplifying application deployment. Think: **deploy applications without manually managing all infrastructure**.

## 87. Amazon Lightsail

Simplified cloud service for smaller applications/workloads. Think: **easy/simple AWS hosting**.

## 88. AWS Batch

Runs batch computing jobs. Think: **batch workloads**.

## 89. AWS Outposts

AWS infrastructure deployed in your own/on-premises environment. Useful when workloads need AWS capabilities while remaining on-premises.

# DATABASES

## 90. Relational Database

Data organized into tables and relationships. SQL. AWS examples: RDS, Aurora.

## 91. Amazon RDS

Managed relational database service. Supports multiple database engines. AWS handles much of infrastructure, maintenance, backups, patching. Customer still manages database usage/configuration/data/access.

## 92. Amazon Aurora

AWS relational database designed for high performance/availability and compatibility with MySQL/PostgreSQL. Think: **AWS cloud-optimized relational database**.

## 93. DynamoDB

Fully managed NoSQL database. Characteristics: key-value/document, highly scalable, low latency, serverless. Think: **NoSQL at scale**.

## 94. Amazon ElastiCache

In-memory caching. Supports Redis and Memcached. Purpose: reduce database load and improve application performance.

## 95. Amazon DocumentDB

Managed document database compatible with MongoDB workloads/APIs. Think: **document database**.

## 96. Amazon Neptune

Managed graph database. Think: **relationships between entities → Neptune**.

## 97. AWS Database Migration Service (DMS)

Migrates databases. Can support homogeneous and heterogeneous migration.

## 98. AWS Schema Conversion Tool (SCT)

Converts schemas between different database engines. Example: Oracle → PostgreSQL.

## 99. Amazon Timestream

A managed time-series database for data that changes over time, such as IoT sensor readings and application metrics. Think: **Timestream = time-series data.**

# NETWORKING

## 100. Amazon VPC

**Virtual Private Cloud** — a logically isolated network in AWS. You control IP ranges, subnets, routing, gateways, network security.

## 101. Subnet

A subdivision of a VPC IP range. Can be public or private.

## 102. Public Subnet

Subnet whose routing allows access to/from the internet through appropriate components.

## 103. Private Subnet

No direct route to the public internet. Common for databases and internal applications.

## 104. Internet Gateway (IGW)

Provides internet connectivity for resources in a VPC when routing/security configuration permits it.

## 105. Elastic IP Address

A static public IPv4 address that can be allocated to your AWS account and associated with an EC2 instance or network interface. Think: **Elastic IP = persistent public IPv4 address.**

## 106. NAT Gateway

Allows resources in private subnets to initiate outbound internet connections without being directly reachable from the internet. Classic example: private EC2 needs to download updates → NAT Gateway provides outbound internet access.

## 107. Security Groups

Virtual firewall associated with resources such as EC2. Key characteristic: **stateful**. Controls inbound/outbound traffic.

## 108. Network ACL (NACL)

Network-level access control for subnets. Key characteristic: **stateless**. Supports allow and deny rules.

## 109. Security Group vs NACL

|           | Security Group             | NACL            |
| --------- | -------------------------- | --------------- |
| Level     | Resource                   | Subnet          |
| Stateful  | Yes                        | No              |
| Rules     | Allow                      | Allow + Deny    |
| Main idea | Instance/resource firewall | Subnet firewall |

## 110. Route 53

AWS DNS service. Domain name → IP/resource. Also provides DNS routing, health checks, domain registration. Think: **Route 53 = DNS**.

## 111. Amazon API Gateway

Create/manage APIs. Useful for REST APIs, HTTP APIs, WebSocket APIs. Common architecture:

```
Client
  ↓
API Gateway
  ↓
Lambda
  ↓
DynamoDB
```

## 112. AWS Direct Connect

Dedicated network connection from an organization to AWS. Benefits: more consistent/private connectivity, lower latency compared with internet-based connectivity in appropriate scenarios, hybrid environments. Think: **dedicated connection to AWS**.

## 113. AWS VPN

Encrypted connection over an existing network/internet path. Common use: on-premises network ↔ AWS VPC.

## 114. Site-to-Site VPN

Connects an on-premises network to a VPC.

## 115. Client VPN

Allows individual users/devices to connect to AWS resources through a VPN.

## 116. AWS PrivateLink

Private connectivity to supported services/resources without exposing traffic through the public internet. Think: **private access to services**.

## 117. AWS Transit Gateway

Connects multiple VPCs and networks through a central networking hub. Think: **hub-and-spoke networking**.

## 118. AWS Global Accelerator

Improves availability/performance for global applications using AWS global network infrastructure. Think: **global application traffic acceleration**. Don't confuse with CloudFront: CloudFront → CDN/cached content; Global Accelerator → network-level traffic acceleration.

# STORAGE

## 119. Amazon S3

Object storage. Used for files, images, videos, backups, logs, data lakes, static website content. S3 stores **objects inside buckets**.

## 120. S3 Characteristics

Object storage, highly durable, scalable, accessible through APIs, bucket/object permissions, versioning, lifecycle policies.

## 121. S3 Storage Classes

Know the purpose, not every obscure pricing detail.

- **S3 Standard**: frequently accessed data.
- **S3 Intelligent-Tiering**: automatically moves objects between access tiers based on changing access patterns.
- **S3 Standard-IA**: infrequently accessed data.
- **S3 One Zone-IA**: infrequently accessed data stored in a single AZ.
- **S3 Glacier Instant Retrieval**: archive data that still requires rapid retrieval.
- **S3 Glacier Flexible Retrieval**: archive data where retrieval can take longer.
- **S3 Glacier Deep Archive**: very long-term, rarely accessed archive.

General principle: lower-access/archive tiers → lower storage cost but potentially higher retrieval constraints/cost.

## 122. S3 Lifecycle Policies

Automatically transition/delete objects based on rules. Example:

```
Day 0 → S3 Standard
Day 30 → Standard-IA
Day 90 → Glacier
Day 365 → Delete
```

Purpose: automate storage cost optimization and retention.

## 123. S3 Versioning

Keeps multiple versions of objects. Useful for accidental deletion protection, recovery, version tracking.

## 124. Amazon EBS

Elastic Block Store — block storage for EC2. Think: **EBS = virtual hard drive attached to EC2**.

## 125. Instance Store

Temporary block storage physically associated with the host. Instance store data is **ephemeral**. If the underlying instance/host fails or is stopped/terminated depending on instance behavior, data may be lost.

## 126. Amazon EFS

Elastic File System — managed file storage. Multiple resources can access the same file system. Think: **EFS = shared Linux-style file system**.

## 127. Amazon FSx

Managed specialized file systems such as Windows File Server, Lustre, OpenZFS, NetApp ONTAP. Think: **FSx = managed specialized file systems**.

## 128. AWS Storage Gateway

Connects on-premises environments with AWS storage services. Useful in hybrid storage scenarios.

## 129. AWS Backup

Centralized backup service for supported AWS resources. Think: **AWS Backup = centralized backup management**.

## 130. AWS Elastic Disaster Recovery

Helps recover workloads into AWS for disaster recovery. Think: **DR migration/recovery**.

## 131. Disaster Recovery Strategies

- **Backup and Restore**: restore data and rebuild systems after a disaster; generally the lowest cost and longest recovery time.
- **Pilot Light**: keep core components ready; start and scale the remaining resources during recovery.
- **Warm Standby**: keep a smaller, fully functional environment running; scale it up during a disaster.
- **Multi-Site / Active-Active**: run multiple live environments simultaneously; generally the fastest recovery and highest cost.

Think: **Backup and Restore → Pilot Light → Warm Standby → Active-Active** means progressively faster recovery and higher cost.

## 132. EBS vs EFS vs S3

| Service        | Type            | Typical use             |
| -------------- | --------------- | ----------------------- |
| EBS            | Block           | EC2 disk                |
| EFS            | File            | Shared file system      |
| S3             | Object          | Files/objects           |
| Instance Store | Ephemeral block | Temporary local storage |

# ANALYTICS

## 133. Amazon Athena

Serverless interactive query service for data in S3. Think: **SQL/query S3 data**.

## 134. Amazon Redshift

Data warehouse. Think: **large-scale analytics/data warehousing**.

## 135. Amazon Kinesis

Real-time streaming data. Think: **streaming data**.

## 136. AWS Glue

Data integration/ETL service. Think: **prepare, transform, integrate data**.

## 137. Amazon EMR

Amazon Elastic MapReduce is a Managed big-data processing platform. Common technologies: Hadoop, Spark. Think: **big data processing**.

## 138. Amazon OpenSearch Service

Search, analytics, and log-analysis workloads. Think: **search + logs + analytics**.

## 139. Amazon QuickSight

Business intelligence and visualization. Think: **dashboards/BI**.

# AI / MACHINE LEARNING

## 140. Amazon SageMaker AI

Build/train/deploy machine-learning models. Think: **ML platform**.

## 141. Amazon Rekognition

Image/video analysis. Think: **computer vision**.

## 142. Amazon Textract

Extracts text/data from documents. Think: **document → structured information**.

## 143. Amazon Transcribe

Speech → text.

## 144. Amazon Translate

Language translation.

## 145. Amazon Polly

Text → speech.

## 146. Amazon Lex

Build conversational interfaces/chatbots.

## 147. Amazon Comprehend

Natural-language processing. Analyzes text for sentiment, entities, key phrases.

## 148. Amazon Kendra

An intelligent enterprise search service that helps users find information across connected data sources using natural-language questions.
Think: **Kendra = natural-language enterprise search.**

**Kendra vs Comprehend**
- **Kendra**: searches and finds information across content sources.
- **Comprehend**: analyzes text, such as sentiment, entities, and key phrases.

## 149. Amazon Q

Generative AI assistant/service family for work/developer/business use cases. For CCP: know it as an AWS generative AI assistant/service.

# APPLICATION INTEGRATION

## 150. Amazon Simple Queue Service SQS

Message queue. Allows applications to communicate asynchronously. Think: **SQS = queue**. Example: `Order Service → SQS → Worker`. If the worker is temporarily unavailable, messages can remain in the queue.

## 151. Amazon Simple Notification Service SNS

Publish/subscribe messaging and notifications. Can send messages/notifications to multiple subscribers/endpoints. Think: **SNS = notifications/pub-sub**.

## 152. SQS vs SNS

| SQS                         | SNS                            |
| --------------------------- | ------------------------------ |
| Queue                       | Pub/sub                        |
| Messages wait for consumers | Pushes messages to subscribers |
| Decouples producer/consumer | Fan-out/notifications          |

## 153. Amazon EventBridge

Event bus/service for connecting applications and reacting to events. Think: **event-driven architecture**.

## 154. AWS Step Functions

Orchestrates workflows. Think: **coordinate multiple steps/services**.

# BUSINESS APPLICATIONS

## 155. Amazon Connect

Cloud contact-center service.

## 156. Amazon SES

Simple Email Service. Used for sending/receiving email.

# DEVELOPER TOOLS

## 157. AWS CodeBuild

Build/compile/test source code.

## 158. AWS CodePipeline

CI/CD pipeline orchestration. Think: **automate software delivery pipeline**.

## 159. AWS X-Ray

Application tracing/observability. Helps identify performance bottlenecks, errors, request flow.

## 160. AWS CodeCommit

A managed source-control service for hosting private Git repositories. Think: **CodeCommit = Git repository hosting.**

## 161. AWS CodeArtifact

A managed repository for storing, publishing, and sharing software packages and dependencies. Think: **CodeArtifact = software package repository.**

## 162. AWS CodeGuru

Uses automated analysis and machine learning to help improve code quality and application performance.
- **Reviewer**: provides code-quality recommendations.
- **Profiler**: identifies application performance bottlenecks.
Think: **CodeGuru = code review + performance profiling.**

## 163. AWS Cloud9

A cloud-based IDE for writing, running, and debugging code. Think: **Cloud9 = cloud development environment.**

## 164. AWS Application Composer

A visual tool for designing serverless applications and generating infrastructure-as-code templates. Think: **Application Composer = visually design serverless applications.**

## 165. AWS Device Farm

Tests mobile and web applications on real devices hosted by AWS. Think: **Device Farm = test applications on real devices.**

# END USER COMPUTING

## 166. Amazon WorkSpaces

Managed virtual desktops. Think: **cloud desktop**.

## 167. Amazon AppStream 2.0

Streams desktop applications to users. Think: **stream applications**.

## 168. Amazon WorkSpaces Secure Browser

Managed browser environment for secure web access.

# FRONTEND WEB/MOBILE

## 169. AWS Amplify

Tools/services for building and deploying web/mobile applications. Think: **frontend + mobile application development**.

# IoT

## 170. AWS IoT Core

Connects/manages communication with IoT devices. Think: **devices → AWS**.

# MANAGEMENT & GOVERNANCE

## 171. AWS CloudFormation

Infrastructure as Code. Think: **define AWS infrastructure using templates**.

## 172. AWS CloudTrail

API audit trail. Already covered.

## 173. Amazon CloudWatch

Monitoring/logs/metrics/alarms.

## 174. AWS Config

Configuration/compliance.

## 175. AWS Compute Optimizer

Recommendations for right-sizing compute resources.

## 176. AWS License Manager

Helps manage software licenses.

## 177. AWS Service Catalog

Allows organizations to create/manage approved catalogs of IT products/services.

## 178. Service Quotas

Shows/manages service quotas/limits. Think: **how much of an AWS resource/service can I use?**

## 179. AWS Systems Manager

Operational management. Examples: patch management, Automation, Session Manager, Parameter Store.

## 180. AWS Well-Architected Tool

Helps review workloads against Well-Architected Framework best practices.

## 181. AWS Auto Scaling

Automatically scales supported AWS resources. Don't confuse: **Auto Scaling** → scaling capacity; **Elastic Load Balancing** → distributing traffic.

## 182. AWS Organizations

Multi-account management.

## 183. AWS Control Tower

Governance/setup of multi-account environments.

# MIGRATION

|Service|Purpose|
|---|---|
|Application Discovery|Discover on-prem infrastructure/apps|
|Application Migration Service|Migrate applications/servers|
|DMS|Database migration|
|SCT|Schema conversion|
|Migration Evaluator|Migration assessment/cost|
|Migration Hub|Track migration|

# NETWORKING QUICK TABLE

| Service            | Remember                         |
| ------------------ | -------------------------------- |
| VPC                | Virtual network                  |
| Subnet             | Network subdivision              |
| Internet Gateway   | Internet connectivity            |
| NAT Gateway        | Private subnet outbound internet |
| Route 53           | DNS                              |
| CloudFront         | CDN                              |
| Global Accelerator | Global traffic acceleration      |
| Direct Connect     | Dedicated connection             |
| VPN                | Encrypted network connection     |
| PrivateLink        | Private service connectivity     |
| Transit Gateway    | Connect many networks/VPCs       |
| API Gateway        | APIs                             |
| Security Group     | Stateful resource firewall       |
| NACL               | Stateless subnet firewall        |

# STORAGE QUICK TABLE

|Service|Remember|
|---|---|
|S3|Object storage|
|EBS|Block storage|
|EFS|File storage|
|FSx|Managed specialized file systems|
|S3 Glacier|Archive|
|Storage Gateway|Hybrid storage|
|AWS Backup|Backup|
|Elastic Disaster Recovery|Disaster recovery|

# DATABASE QUICK TABLE

|Service|Remember|
|---|---|
|RDS|Managed relational DB|
|Aurora|AWS cloud-optimized relational DB|
|DynamoDB|NoSQL|
|ElastiCache|In-memory cache|
|DocumentDB|Document DB|
|Neptune|Graph DB|
|DMS|Database migration|
|SCT|Schema conversion|

# DOMAIN 4 — BILLING, PRICING & SUPPORT (12%)

Officially divided into: 1. Pricing models 2. Billing/cost management 3. Technical resources/support

## 184. AWS Pricing Models

**On-Demand**: pay for compute capacity as you use it. Best for unpredictable workloads, short-term workloads, no long-term commitment.

## 185. Reserved Instances

Commit to a specific configuration/term to receive discounted pricing compared with On-Demand. Best for **predictable workloads**. AWS expects you to understand Reserved Instance flexibility and behavior in AWS Organizations.

## 186. Spot Instances

Use spare AWS compute capacity at potentially large discounts. But AWS can interrupt the instance when capacity is needed. Best for flexible, fault-tolerant workloads and batch jobs. Not ideal for critical workloads that cannot tolerate interruption.

## 187. Savings Plans

Commit to a consistent amount of compute usage/spend over a term in exchange for discounted pricing. Savings Plans are commitment-based discounts.

## 188. Dedicated Hosts

Physical server dedicated to a customer. Useful for licensing requirements, compliance, specific host-level requirements.

## 189. Dedicated Instances

Instances running on hardware dedicated to a single customer, without necessarily giving the same host-level control as Dedicated Hosts.

## 190. Capacity Reservations

Reserve capacity for EC2 in a specific Availability Zone. Capacity Reservation = capacity assurance. It is not primarily a discount mechanism.

## 191. Compute Pricing — Mental Model

| Option               | Main idea                           |
| -------------------- | ----------------------------------- |
| On-Demand            | Flexibility                         |
| Reserved             | Predictable long-term workload      |
| Spot                 | Cheapest/flexible but interruptible |
| Savings Plans        | Commitment for discounted compute   |
| Dedicated Host       | Dedicated physical host             |
| Dedicated Instance   | Dedicated hardware                  |
| Capacity Reservation | Reserve capacity                    |

## 192. Free Tier

AWS provides free usage for eligible services/accounts under applicable terms. "Free Tier" does not mean every AWS service is always free. Always understand usage limits, eligibility, duration, service-specific conditions.

## 193. AWS Pricing Calculator

Estimate expected AWS costs **before deployment**. Think: **planning/estimating future costs**.

## 194. AWS Cost Explorer

Analyze actual/current AWS spending and usage. Think: **analyze spending**.

## 195. AWS Budgets

Set budgets and receive alerts when actual/forecasted spending or usage reaches configured thresholds. Think: **budget + alerts**.

## 196. Cost Explorer vs Budgets vs Pricing Calculator

| Tool               | Purpose                    |
| ------------------ | -------------------------- |
| Pricing Calculator | Estimate before deployment |
| Cost Explorer      | Analyze existing spending  |
| Budgets            | Set limits/alerts          |

## 197. AWS Cost and Usage Report (CUR)

Detailed information about AWS usage and costs. Useful for detailed cost analysis, reporting, cost allocation.

## 198. Cost Allocation Tags

Tags help identify which resources/costs belong to teams, projects, departments, environments. Example:

```
Project = ECommerce
Environment = Production
Team = Security
```

Then use billing reports to analyze costs.

## 199. AWS Organizations + Consolidated Billing

Multiple AWS accounts can be centrally managed. Consolidated billing combines billing across accounts. Benefits: centralized billing, cost visibility, potential pricing benefits based on aggregated usage.

## 200. AWS Marketplace

Third-party software/products that can integrate with AWS. Examples: security products, software, business applications. Can also provide capabilities related to cost management, governance and entitlements.

## 201. AWS Support

Know the major support options. Current exam guide references: Basic Support, AWS Business Support+, AWS Enterprise Support, AWS Unified Operations. The exact benefits/response levels are worth checking immediately before your exam because support offerings can change.

## 202. AWS Support Plans

- **Basic**: included support; account and billing assistance, documentation, AWS Health, and basic Trusted Advisor checks.
- **Business Support+**: 24/7 technical support, unlimited support cases, and expanded Trusted Advisor checks.
- **Enterprise Support**: Business-level technical support plus a designated Technical Account Manager (TAM) and proactive guidance.
- **Unified Operations**: advanced proactive operational support for mission-critical workloads, including specialist guidance and operational reviews.

Think: **Basic = account/billing help; Business Support+ = technical support; Enterprise = TAM; Unified Operations = advanced proactive operations.**

## 203. AWS Knowledge Center

Articles answering common AWS questions/problems. Think: **troubleshooting/how-to knowledge**.

## 204. AWS re:Post

AWS community where customers and experts discuss AWS issues/questions. Think: **community Q&A**.

## 205. AWS Prescriptive Guidance

Recommendations and practical guidance for implementing AWS solutions. Think: **how should I approach this AWS problem?**

## 206. AWS Documentation

Official technical documentation. Think: detailed reference/how-to information.

## 207. AWS Whitepapers

In-depth AWS technical/business guidance.

## 208. AWS Security Blog

Security-focused AWS articles and guidance.

## 209. AWS Professional Services

AWS experts who help organizations plan/design/implement AWS solutions.

## 210. AWS Solutions Architects

Provide architectural guidance and help customers design AWS solutions.

## 211. AWS Partner Network (APN)

Network of AWS partners, including independent software vendors, system integrators, consulting/service partners.

## 212. AWS Partner Benefits

Potential benefits: training, certification, partner events, volume discounts.

## 213. Trusted Advisor vs Support vs Health

| Service               | Main idea                        |
| --------------------- | -------------------------------- |
| Trusted Advisor       | Recommendations                  |
| Health Dashboard      | AWS events affecting environment |
| Support               | Technical/customer assistance    |
| Knowledge Center      | AWS troubleshooting articles     |
| re:Post               | Community                        |
| Professional Services | Expert implementation/consulting |
| Solutions Architect   | Architecture guidance            |

# AWS SERVICE RECOGNITION MASTER LIST

The official current CLF-C02 in-scope list is broader than just the "core" services. AWS currently lists **19 service categories** and explicitly says the list is non-exhaustive and subject to change. You should at least recognize the following:

- **Analytics**: Athena, EMR, Glue, Kinesis, OpenSearch, QuickSight, Redshift, Timestream
- **Application Integration**: EventBridge, SNS, SQS, Step Functions
- **Business Applications**: Connect, SES
- **Cloud Financial Management**: Budgets, Cost and Usage Reports, Cost Explorer, Marketplace
- **Compute**: AWS Batch, EC2, Elastic Beanstalk, Lightsail, Outposts
- **Containers**: ECR, ECS, EKS
- **Customer Enablement**: AWS Support
- **Database**: Aurora, DocumentDB, DynamoDB, ElastiCache, Neptune, RDS
- **Developer Tools**: AWS CLI, Cloud9, CodeArtifact, CodeBuild, CodeCommit, CodeGuru, CodePipeline, Device Farm, X-Ray
- **End User Computing**: AppStream 2.0, WorkSpaces, WorkSpaces Secure Browser
- **Frontend Web/Mobile**: Amplify
- **IoT**: IoT Core
- **Machine Learning / Search**: Comprehend, Kendra, Lex, Polly, Amazon Q, Rekognition, SageMaker AI, Textract, Transcribe, Translate
- **Management/Governance**: Auto Scaling, CloudFormation, CloudTrail, CloudWatch, Compute Optimizer, Config, Control Tower, Health Dashboard, Image Builder, License Manager, Management Console, Organizations, Parameter Store, Service Catalog, Service Quotas, Systems Manager, Trusted Advisor, Well-Architected Tool
- **Migration**: Application Discovery Service, Application Migration Service, DataSync, Data Transfer Terminal, DMS, Migration Evaluator, Migration Hub, Snow Family, SCT
- **Networking**: API Gateway, CloudFront, Direct Connect, Elastic IP, Global Accelerator, PrivateLink, Route 53, Transit Gateway, VPC, VPN, Wavelength, Site-to-Site VPN, Client VPN
- **Security**: Artifact, ACM, CloudHSM, Cognito, Detective, Directory Service, Firewall Manager, GuardDuty, IAM, IAM Credential Report, IAM Identity Center, Inspector, KMS, Macie, RAM, Secrets Manager, Security Hub, Shield, STS, WAF
- **Serverless**: Fargate, Lambda
- **Storage**: Backup, EBS, EFS, Elastic Disaster Recovery, FSx, S3, S3 Glacier, Storage Gateway

This current service list is directly aligned with AWS's CLF-C02 documentation.

# THE MOST IMPORTANT SERVICE COMPARISONS

Be able to answer these **without hesitation**.

- **S3 vs EBS vs EFS**: Object vs Block vs File
- **RDS vs DynamoDB**: Relational vs NoSQL
- **RDS vs EC2 database**: Managed database vs database you manage on a server
- **CloudWatch vs CloudTrail vs Config**: Monitoring vs API auditing vs configuration/compliance
- **GuardDuty vs Inspector vs Detective vs Security Hub**: Threat detection vs vulnerability assessment vs investigation vs centralized findings
- **IAM vs Cognito**: AWS resource access vs application-user authentication
- **KMS vs CloudHSM**: Managed key management vs dedicated HSM
- **WAF vs Shield**: Web application protection vs DDoS protection
- **SQS vs SNS vs EventBridge**: Queue vs pub/sub notifications vs event bus
- **CloudFront vs Global Accelerator**: CDN/content caching vs global network traffic acceleration
- **Direct Connect vs VPN**: Dedicated connectivity vs encrypted connection over existing network
- **Security Group vs NACL**: Stateful resource firewall vs stateless subnet firewall
- **ECS vs EKS vs Fargate**: Container orchestration vs Kubernetes vs serverless container compute
- **EC2 vs Lambda**: Virtual server control vs serverless functions
- **Auto Scaling vs Load Balancer**: Adjust capacity vs distribute traffic
- **Cost Explorer vs Budgets vs Pricing Calculator**: Analyze vs alert/control vs estimate
- **Artifact vs Trusted Advisor**: Compliance documents vs recommendations
- **CloudFormation vs Console**: IaC/repeatability vs manual GUI management

- **Snow Family vs DataSync**: physical data transfer vs automated online transfer
- **AMI vs Image Builder**: instance template vs automated image creation
- **Parameter Store vs Secrets Manager**: configuration parameters vs secrets management
- **STS vs IAM**: temporary credentials vs identity and access management
- **Kendra vs Comprehend**: enterprise search vs text analysis
- **CodeCommit vs CodeArtifact**: Git repositories vs software packages
- **CodeGuru Reviewer vs Profiler**: code recommendations vs performance bottlenecks
- **Pilot Light vs Warm Standby**: core components ready vs smaller running environment
- **Warm Standby vs Active-Active**: scaled-up standby vs multiple live environments
