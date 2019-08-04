## AWS Certified Solutions Architect - Associate 2019
### Section 1: Introduction 2019

* **AWS partner certs** - 20 standard and 8 professional certs required by a org to have the partnership status
* **Tiers**
  * Practitioner - Certified Cloud Practioner 
  * Assosciate - Certified Solutions Architect Assosciate | Certified Developer Assosciate | Certified Sysops administrator assosciate
  * Professional - Certified Solutions Architect Professional | Devops Professional 
  * Speciality - Big Data | Machine Learning | Security | Advanced Networking

* **The Exam Blue Print**
  * 130 minutes
  * 60 questions 
  * Multiple choice
  * Creating an AWS account 

### Section 2: AWS - 10,000 Foot Overview

* **AWS history so far**
  * Andy Jesse - CEO of Amazon Web Services and he said famously that invention requires two things one the ability to try a lot of experiments and two not having to live with the collateral damage of failed experiments.
  * In 2003 Chris Pinkman and Benjamin Black presented a paper on what Amazon's own internal infrastructure should look like and they suggested selling it as a service and prepared a business case.
  * SQS launched in 2004 (first service)
  * AWS launched in 2006 
  * 2007 - 180,000 developers on the platform
  * 2010 all of Amazon.com moved over to Amazon Web Services.
  * And by 2012 Amazon had their first reinvent conference.
  * 2013 - Certifications launched
  * 2014 - AWS was committed to achieve 100 per cent renewable energy usage for its global footprint.
  * 2015  - AWS broke out its revenue and they were making 6 billion US
  * 2016 - runrate of 13 billion US
  * 2017 - AWS re-invent releases a host of artifical intelligent services , runrate of 27 billion US
  * So these were services like Polly and lex.These are the things that power Alexa.They released sage maker which is a type of machine learning service.
  * 2018 - AWS launch Machine learning certificates and they had a heavy focus on automating and A.I. and AML.
  
 * **AWS - 10,000 Foot Overview**

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

## AWS Global Infrastructure
* Reigons , **Avalability Zones** - Think of zones as the Data centers, 1 AVZ could be 2 or 3 data centers
* Each **Reigon** consists of two or more AVZs
* **Edge locations** - you're always going to have more edge locations than you will have regions
  * These are endpoints for AWS which are used for caching content so typically this consists of CloudFront which is Amazon's content delivery network 
    
##  Section 3: Identity Access Management & S3

### IAM 101

* **IAM** - allows you to set up users groups permissions and roles and basically allows you to grant access to different parts of
the AWS platform. IAM offers the following features 
  * It gives you centralized control of your AWS account 
  * It gives you shared access to your AWS account 
  * granular permissions
  * Identity Federation ( Active directory / Facebook / LinkedIn)
  * multi factor authentication (username + password + special code)
  * Provide temp access for users/devices and services where necessary
  * allows you to set up your own password rotation policy 
  * supports PCI DSS compliance (Payments Card)
  
#### 4 key terminologies - 
  * **Users** - End users such as people, employees of an org
  * **Groups** - A collection of users. Each user in the group will inherit the group properties
  * **Policies** - Policies are made up of documents called policy documents. JSON format used to give permissions to users/ groups.
  * **Roles** - create roles and assign to groups.
  
 ### IAM LAB
 
 * Services -> Identity Access and Compliance -> IAM
 * IAM users sign-in link: - https://accountname.signin.aws.amazon.com/console
   * Can customize and choose a global name
 * Root account / god mode - account that you first sign-in with 
 * **Activate MFA on your root account**
   * Use google authenticator app and scan the QR code 
   * update the MFA code and assign MFA
 * Whenever you are doing anything inside IAM , the reigon is global and you are using the root account.
 
 * **Create individual IAM users**
   * Add user -> Access type -> 
   * **Programmatic access** - Enables an access key ID and secret access key for the AWS API, CLI, SDK, and other development tools
   * **AWS Management Console access** - Enables a password that allows users to sign-in to the AWS Management Console.
   * Create a group and assign AWS managed policies
   * Apply IAM policy
 * **Use groups to assign permissions**
 * **Apply an IAM password policy**

![IAM Dashboard](https://user-images.githubusercontent.com/8856857/61251611-538e0b00-a79e-11e9-8eef-ffd406943de9.PNG)

 * **Create Role**
   * 1. Choose Services
   * 2. Attach Permission Policies
   
![Choose Services](https://user-images.githubusercontent.com/8856857/61251943-4e7d8b80-a79f-11e9-86a8-eedd9c6f5b99.png)

![What have we learnt?](https://user-images.githubusercontent.com/8856857/61252484-095a5900-a7a1-11e9-96bc-06800ef2a54a.png)
![What have we learnt?](https://user-images.githubusercontent.com/8856857/61252643-8980be80-a7a1-11e9-8cfe-5a5f5ba823df.png)

### Create a Billing Alarm
* Billing Dashboard -> Billing Preferences 
* Find the CloudWatch Service

## Summary
IAM consists of the following:
* Users
* Groups
* Roles
* Policies - JSON object

* **IAM is Universal** it does not apply to reigons at this time
* The **root account** is simply the account you create when you setup AWS forthe first time, it has all admin privilidges
* No users have **no permission** when thier accounts are first created.
* New users are assigned **Access Key ID and Secret Key Access** when first created
* **These are not the same as password** and cannot be used to login to the console, you can use Access Key ID and Secret Key Access to access AWS via API / commandline.
* **You onle get to view these once**, if you loose them you need to regenerate them.
