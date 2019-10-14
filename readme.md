<h1 align="center"></h1>

<div align="center">
  :stars::ship::ship::ship::ship::ship:
</div>
<div align="center">
  <strong>Everything AWS - idiosyncratic opinions of a bunch of AWS resources</strong>
</div>
<div align="center">
  A <code>4kb</code> framework for creating a AWS culture
</div>

<br />

<div align="center">
  <!-- Stability -->
  <a href="https://nodejs.org/api/documentation.html#documentation_stability_index">
    <img src="https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square"
      alt="API stability" />
  </a>  
  <!-- Build Status -->
  <a href="https://travis-ci.org/choojs/choo">
    <img src="https://img.shields.io/travis/choojs/choo/master.svg?style=flat-square"
      alt="Build Status" />
  </a>
  <!-- Test Coverage -->
  <a href="https://codecov.io/github/choojs/choo">
    <img src="https://img.shields.io/codecov/c/github/choojs/choo/master.svg?style=flat-square"
      alt="Test Coverage" />
  </a>
  <!-- Downloads -->
  <a href="https://npmjs.org/package/choo">
    <img src="https://img.shields.io/npm/dt/choo.svg?style=flat-square"
      alt="Download" />
  </a>
  <!-- Standard -->
  <a href="https://standardjs.com">
    <img src="https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square"
      alt="Standard" />
  </a>
</div>

<div align="center">
  <h3>
    <a href="https://github.com/Develop-X/AWS/tree/master/AWS%20Certified%20Solutions%20Architect">
      AWS Certified Solutions Architect
    </a>
    <span> | </span>
    <a href="https://github.com/Develop-X/AWS/blob/master/supporting-tools.md">
      Supporting Tools 
    </a>
    <span> | </span>
    <a href="https://github.com/Develop-X/AWS/blob/master/Which%20Services%20to%20Use.md">
      Which Services 
    </a>
    <span> | </span>
    <a href="https://github.com/Develop-X/AWS/blob/master/resources.md">
      Resources
    </a>
     <span> | </span>
    <a href="https://github.com/Develop-X/AWS/blob/master/AWS%20Certified%20Solutions%20Architect/000_Acronyms.md">
      Acronyms
    </a>
    </h3>
</div>

<div align="center">
  <sub>The little framework that could. Built with ❤︎ by
  Ady Kalra</a> and
    inspired by thoughtworks
  </a>
</div>

## Table of Contents
- [AWS Management & Governance](#AWS-Management-&-Governance)
  - [CloudFormation](#CloudFormation)
  - [CloudWatch](#CloudWatch)
- [AWS Storage](#AWS-Storage)
  - [S3](#S3)
- [AWS Application Integration](#AWS-Application-Integration)
  - [SNS](#SNS)

## AWS Management & Governance

## CloudFormation
[AWS CloudFormation](https://aws.amazon.com/cloudformation/) ```allows you to model your entire infrastructure with either a text file or programming languages. This provides a``` **single source of truth** ```for your AWS resources and helps you to standardize infrastructure components used across your organization, enabling configuration compliance and faster troubleshooting.```

```It provisions your resources in a``` **safe, repeatable manner, allowing you to build and rebuild your infrastructure** ```and applications, without having to perform manual actions or write custom scripts.```

```When you use AWS CloudFormation, you work with``` [templates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html#w2ab1b5c15b7) ```and``` [stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html#w2ab1b5c15b9)

```If you need to make changes to the running resources in a stack, you update the stack. Before making changes to your resources, you can generate a``` [change set](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html#w2ab1b5c15c11) ```, which is a summary of your proposed changes.```

[How It works](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-howdoesitwork.html) ``` Code Infrastructure - Code your infra from scratch using cloud formation template language , in either YAML or JSON format or start from any available templates.``` **Check out your template code or upload into s3** ``` Use AWS cloud formation via browser console, command line or APIs to``` **create a stack based on your template code.** ``` Output - AWS provisons and configures the stacks and resources you specified on your template.``` 

```A collection of useful``` [CloudFormation templates](https://github.com/awslabs/aws-cloudformation-templates)
[Advance Cloud Formation Acloudguru](https://github.com/ACloudGuru/AdvancedCloudFormation)

```AWS CloudFormation```[Best Practices](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html) 
* Organize Your Stacks By Lifecycle and Ownership
* Use Cross-Stack References to Export Shared Resources
* Use IAM to Control Access
* Reuse Templates to Replicate Stacks in Multiple Environments
* Verify Quotas for All Resource Types
* Use Nested Stacks to Reuse Common Template Patterns
* Do Not Embed Credentials in Your Templates
* Use AWS::CloudFormation::Init to Deploy Software Applications on Amazon EC2 Instances
* Validate Templates Before Using Them
* Manage All Stack Resources Through AWS CloudFormation
* Create Change Sets Before Updating Your Stacks
* Use Stack Policies
* Use AWS CloudTrail to Log AWS CloudFormation Calls
* Use Code Reviews and Revision Controls to Manage Your Templates
* Update Your Amazon EC2 Linux Instances Regularly

## CloudWatch
[Amazon Cloudwatch](https://docs.aws.amazon.com/cloudwatch/?id=docs_gateway) ```Amazon CloudWatch monitors your Amazon Web Services (AWS) resources and the applications you run on AWS in real time. You can use CloudWatch to collect and track metrics, which are variables you can measure for your resources and applications.``` 
```You can create alarms which watch metrics and send notifications or automatically make changes to the resources you are monitoring when a threshold is breached. For example, you can monitor the CPU usage and disk reads and writes of your Amazon EC2 instances and then use this data to determine whether you should launch additional instances to handle increased load. ```
* [Amazon CloudWatch console](https://console.aws.amazon.com/cloudwatch/)
Use the following links to get started using the CloudWatch Query API:
* Actions: [An alphabetical list of all CloudWatch actions.](https://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_Operations.html)
* Data Types: [An alphabetical list of all CloudWatch data types.](https://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_Types.html)
* Common Parameters: [Parameters that all Query actions can use.](https://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/CommonParameters.html)
* Common Errors: [Client and server errors that all actions can return.](https://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/CommonErrors.html)
* Regions and Endpoints: [Supported regions and endpoints for all AWS products.](https://docs.aws.amazon.com/general/latest/gr/rande.html#cw_region)

## AWS Storage

## S3
[Amazon s3](https://docs.aws.amazon.com/s3/) ```Amazon Simple Storage Service (Amazon S3) is storage for the internet. You can use Amazon S3 to store and retrieve any amount of data at any time, from anywhere on the web.  Amazon S3 stores ```**data as objects within buckets.** ```An object consists of a file and optionally any metadata that describes that file. You can have one or more buckets. For each bucket, you can control access to it (who can create, delete, and list objects in the bucket), view access logs for it and its objects, and choose the geographical region where Amazon S3 will store the bucket and its contents.```

```Amazon S3 is a``` **REST service.** ```You can send requests to Amazon S3 using the REST API or the``` **AWS SDK** ```wrapper libraries that wrap the underlying Amazon S3 REST API, simplifying your programming tasks.```
* [Making Requests to Amazon S3 over IPv6](https://docs.aws.amazon.com/AmazonS3/latest/dev/ipv6-access.html)
* [Making Requests Using the AWS SDKs](https://docs.aws.amazon.com/AmazonS3/latest/dev/MakingAuthenticatedRequests.html)
* [Making Requests Using the REST API](https://docs.aws.amazon.com/AmazonS3/latest/dev/RESTAPI.html)

## AWS Application Integration

## SNS
[Amazon Simple Notification Service](https://docs.aws.amazon.com/sns/?id=docs_gateway) ```is a web service that enables applications, end-users, and devices to instantly send and receive notifications from the cloud / is a web service that coordinates and manages the delivery or sending of messages to subscribing endpoints or clients. ```
```In Amazon SNS, there are two types of clients``` **publishers and subscribers** ```also referred to as``` **producers and consumers.** ```Publishers communicate``` [asynchronously](https://www.taskus.com/glossary/asynchronous-messaging/) ```with subscribers by producing and sending a message to a ``` [SNS topic](https://docs.aws.amazon.com/sns/latest/dg/sns-tutorial-create-topic.html)``` which is a logical access point and communication channel. Subscribers (that is, web servers, email addresses, Amazon SQS queues, AWS Lambda functions) consume or receive the message or notification over one of the supported protocols (that is, Amazon SQS, HTTP/S, email, SMS, Lambda) when they are subscribed to the topic.```

```When using Amazon SNS, you (as the owner)``` **create a topic** ```and control access to it by defining policies that determine which publishers and subscribers can communicate with the topic. A publisher sends messages to topics that they have created or to topics they have permission to publish to. Instead of including a specific destination address in each message, a publisher sends a message to the topic. Amazon SNS matches the topic to a list of subscribers who have subscribed to that topic, and delivers the message to each of those subscribers.``` **Each topic has a unique name that identifies the Amazon SNS endpoint** ```for publishers to post messages and subscribers to register for notifications. Subscribers receive all messages published to the topics to which they subscribe, and all subscribers to a topic receive the same messages.```
* Step 1: Create a Topic
* Step 2: Create a Subscription for an Endpoint to the Topic
* Step 3: Publish a Message to the Topic
* Step 4: Delete the Subscription and Topic
[Common Amazon SNS Scenarios](https://docs.aws.amazon.com/sns/latest/dg/sns-common-scenarios.html)

* **Fanout** ```The "fanout" scenario is when an Amazon SNS message is sent to a topic and then``` **replicated and pushed to multiple Amazon SQS queues, HTTP endpoints, or email addresses.** ```This allows for``` **parallel asynchronous processing.** ```For example, you could develop an application that sends an Amazon SNS message to a topic whenever an order is placed for a product. Then, the Amazon SQS queues that are subscribed to that topic would receive identical notifications for the new order. The Amazon EC2 server instance attached to one of the queues could handle the processing or fulfillment of the order while the other server instance could be attached to a data warehouse for analysis of all orders received.```
```Another way to use "fanout" is to replicate data sent to your production environment with your development environment. Expanding upon the previous example, you could subscribe yet another queue to the same topic for new incoming orders. Then, by attaching this new queue to your development environment, you could continue to improve and test your application using data received from your production environment.```
* **Application and System Alerts**
```Application and system alerts are notifications, triggered by predefined thresholds, sent to specified users by SMS and/or email. For example, since many AWS services use Amazon SNS, you can receive immediate notification when an event occurs, such as a specific change to your Amazon EC2 Auto Scaling group.```
* **Push Email and Text Messaging**
```Push email and text messaging are two ways to transmit messages to individuals or groups via email and/or SMS. For example, you could use Amazon SNS to push targeted news headlines to subscribers by email or SMS. Upon receiving the email or SMS text, interested readers could then choose to learn more by visiting a website or launching an application.```
* **Mobile Push Notifications**
```Mobile push notifications enable you to send messages directly to mobile apps. For example, you could use Amazon SNS for sending notifications to an app, indicating that an update is available. The notification message can include a link to download and install the update.```


