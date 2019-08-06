# AWS 10000 Feet Overview

## AWS history so far

  * **Andy Jesse** - CEO of Amazon Web Services and he said famously that invention requires two things one the ability to try a lot of experiments and two not having to live with the collateral damage of failed experiments.
  * In **2003 Chris Pinkman and Benjamin Black** presented a paper on what Amazon's own internal infrastructure should look like and they suggested selling it as a service and prepared a business case.
  * **SQS** launched in 2004 (first service)
  * **AWS launched in 2006 
  * 2007 - 180,000 developers on the platform
  * **2010 all of Amazon.com moved over to Amazon Web Services.
  * And by 2012 Amazon had their first reinvent conference.
  * 2013 - Certifications launched
  * 2014 - AWS was committed to achieve 100 per cent renewable energy usage for its global footprint.
  * 2015  - AWS broke out its revenue and they were making 6 billion US
  * 2016 - runrate of 13 billion US
  * 2017 - AWS re-invent releases a host of artifical intelligent services , runrate of 27 billion US
  * So these were services like Polly and lex.These are the things that power Alexa.They released sage maker which is a type of machine learning service.
  * 2018 - AWS launch Machine learning certificates and they had a heavy focus on automating and A.I. and AML.

## Global Infrastructure

|                        | AWS Global Infrastructure                    |                           | 
|------------------------|----------------------------------------------|---------------------------|
| Compute                | Storage                                      | Databases                 |
| Migration and Transfer | Network and Content Delivery | Developer tools | 
| Robotics | Blockchain | Satellite | 
| Management and Governance | Media Services | Machine Learning | 
| Analytics | Security Identity and Compliance | Mobile |
| AR & VR | Application Integration | AWS Cost Mgmt |
| Customer Engagement | Business Appln | Desktop & App Streaming |
| IOT |  | Game Development |

  - A **Region** is geographical area consisting of 2 or more availability zones.

  - **Availability zone** is logical data center. Availability Zones consist of one or more discrete data centers, each with redundant power, networking, and connectivity, housed in separate facilities.

  - **Edge Locations** are CDN End Points for CloudFront. Many more edge locations exist than regions.
  
  - An Amazon Web Services availability zone is part of an AWS region. This is best thought of as one of a set of data centers in the same city. ... Edge location is Content Delivery Network (CDN) endpoint for AWS to cache contents and reduce latency. Availability zone is logical (not physical!) data center of AWS.

## The AWS Platform

  - **Networking & Content Delivery

      - **VPC** [know VPC in and out] – Virtual Data Center. You can have multiple VPCs per region. VPCs can also be connected to each other.

      - **Route53** – Amazon’s DNS Service

      - **CloudFront** – Content delivery network. Edge locations cache assets.

      - **Direct Connect** – Connect your physical DCs to AWS using dedicated telephone lines

  - **Compute 

      - **EC2** – Elastic Compute Cloud.

      - **EC2 Container Services** – supports Docker.

      - **Elastic Beanstalk** - Just upload your code here. Elastic Bean stalk will provision all infrastructure required.

      - **Lambda** Alexa, Echo devices rely on Lambda

      - **Lightsail** – Out of the box cloud – WordPress, Drupal

  - **Storage

      - **S3** - Object Store

      - **Glacier** – Archive files from S3 into Glacier – use when you don’t need immediate access to files

      - **EFS** (Elastic File Service) - Block Store - can be used for storing databases. It can be attached to multiple EC2 instances.

      - **Storage Gateway** (VM) - communicates between your data center and S3 storage.

  - **Databases

      - **RDS** ( MySQL, PostgreSQL, SQL Server, MariaDB, Aurora)

      - **DynamoDB** - Non relational DB (important for developer exam)

      - **Redshift**  - Data warehousing system  

      - **ElastiCache** - Cloud in-memory DB (important for developer / architect exam)

  - **Migration

      - **Snowball** - Transfer Data - next step over Export Import gateway. Store all your data from enterprise into Snowball and then ship to AWS. Also released Snowball edge – add compute capacity to storage device – so that you can run analytics on top of the huge dataset collected, without having to transfer to cloud. AWS Lambda is supported on Snowball edge.

      - **DMS** - Database migration services - migrate existing DBs to Cloud, also migrate existing Cloud DBs to other regions. Can migrate from Oracle/MySQL/PostgreSQL/ to Aurora.  

      - **SMS** - Server migration services - migrate existing VMs on premise to the Cloud -up to 50 concurrent ones.

  - **Analytics

      - **Athena** - allow SQL queries on S3. Run queries on csv files in S3 buckets.

      - **EMR** -Elastic Map Reduce - process large amounts of data. Based on Hadoop, Apache Spark. Log Analytics etc.

      - **Cloud Search** - Managed services provided by AWS

      - **Elastic Search** – Search service which uses the Elastic product

      - **Kinesis** - streaming and analysis real time data (important for architect exam). used for collating large amounts of data streamed from multiple sources

      - **Data Pipeline** - move data from one place to another. e.g. S3 into DynamoDB and vice versa

      - **Quick Sight**- BA tools for rich visualizations and dashboards.

  - **Security & Identity

      - **IAM** – How you setup and assign users / groups etc.

      - **Inspector** - Agent which inspects your VMs and does security reporting

      - **Certificate Manager** – free SSL certs for your domain names.

      - **Directory Service** - (important for architect exam)

      - **WAF** - Web Application Firewall. Allows application level protection. Different from traditional network level firewalls. You can inspect headers / content

      - **Artifacts** - All Documentation - under compliance and reports.

  - **Management Tools** (important for architect exam)

      - **Cloud Watch** - monitor performance of AWS environment – standard infrastructure metrics.

      - **Cloud Formation** - Infrastructure into Code - document which describes the infrastructure which uses AWS resources.

      - **Cloud Trail** - audit usage of AWS Resources. Important for security exam.

      - **OpsWorks** - automate deployments using Chef. Important for sysops exam

      - **Config manager** - monitors environments and **provides alerts for events**. E.g. someone creates a security group which is against policy

      - **Trusted Advisor** - automated tips for cost & performance optimization, security tips, architecture and design

  - **Application Services

      - **Step functions** – visualize application internals – which micro services is your application using.

      - **SWF** - Simple Workflow Service. Used in Amazon fulfillment center.

      - **API Gateway** - Create, Publish & monitor API services. Access back-end services. 

      - **AppStream** - Stream desktop services via browser

      - **Elastic Transcoder** - convert video into multiple formats to suit all devices.

  - **Developer Tools

      - **Code Commit** - GitHub

      - **Code Build** - pay by minute of build & compilation

      - **Code Deploy** – deploy code to EC2 instances.

      - **Code Pipeline** – Track code versions in different environments.

  - **Mobile Service**

      - **Mobile Hub** - for mobile apps - separate console.

      - **Cognito** - identity provider for mobile applications. Social identity providers – Gmail, Facebook OAuth providers.  

      - **Device Farm** - testing your apps across multitude of devices

      - **Mobile Analytics** – Collect application usage data in a cost-effective way.

      - **Pinpoint** - GA for mobile apps

  - **Business Productivity

      - **Work Docs** – Store work documents on cloud

      - **Work Mail** – Exchange on AWS

  - **IoT

      - IoT Gateway

  - **Desktop and App Streaming

      - **WorkSpaces - aka VDI**. Desktop on cloud. Citrix Receiver

      - **App Stream 2.0** - stream desktop apps to users.

  - **Artificial Intelligence

      - **Alexa** (which uses Lambda) + Lex. Echo isn’t required anymore to use Alexa. It can be accessed via software.

      - **Polly** - Text to Speech

      - **Machine Learning** – based on dataset, AWS will predict outcomes for future decisions – based on demographics etc.

      - **Rekognition** – Image recognition, Facial recognition based on Databases.

  - **Messaging**  (important for associate exam)

      - **SNS** Simple Notifcation Service– Notify by email / text messages/ http-end points

      - **SQS** Simple Queue Service - Post messages to Queue. De-couple your applications.

      - **SES** Simple Email Service – send email via AWS
