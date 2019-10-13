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
- [AWS Storage](#AWS-Storage)
  - [S3](#S3)

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

## AWS Storage

## S3
[Amazon s3](https://docs.aws.amazon.com/s3/) ```Amazon Simple Storage Service (Amazon S3) is storage for the internet. You can use Amazon S3 to store and retrieve any amount of data at any time, from anywhere on the web.  Amazon S3 stores ```**data as objects within buckets.** ```An object consists of a file and optionally any metadata that describes that file. You can have one or more buckets. For each bucket, you can control access to it (who can create, delete, and list objects in the bucket), view access logs for it and its objects, and choose the geographical region where Amazon S3 will store the bucket and its contents.```

```Amazon S3 is a``` **REST service.** ```You can send requests to Amazon S3 using the REST API or the``` **AWS SDK** ```wrapper libraries that wrap the underlying Amazon S3 REST API, simplifying your programming tasks.```
* [Making Requests to Amazon S3 over IPv6](https://docs.aws.amazon.com/AmazonS3/latest/dev/ipv6-access.html)
* [Making Requests Using the AWS SDKs](https://docs.aws.amazon.com/AmazonS3/latest/dev/MakingAuthenticatedRequests.html)
* [Making Requests Using the REST API](https://docs.aws.amazon.com/AmazonS3/latest/dev/RESTAPI.html)
