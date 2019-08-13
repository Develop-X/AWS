# Identity & Access Management

## IAM 101

  - Configure **who uses AWS and their level of access** to the AWS Console.

  - Centralized control over AWS Account

  - Share access for AWS Account

  - Granular permissions for users / services

  - **Identity Federation** – Facebook, LinkedIn and Active Directory- You can login to AWS with your corporate credentials.

  - **Multi-factor authentication** – helps secure the account. Especially for root account

  - Temporary access to users and services

  - Setup **password rotation policy**

  - Integration with other AWS services.

  - Supports **PCI-DSS compliance** (Payment Card Industry Data Security Standard )

### Critical Terms

IAM consists of the following

  - **Users** – End users / people.

  - **Groups** – Users having one set of permissions.

  - **Roles** – Create roles and assign them to AWS resources.

  - **Policies** – Document (JSON format) that defines one or more permissions – assign to user or groups

### IAM Features

  - **IAM is a global service**. It is not region specific

  - **Root account** / god mode is the email address you use to sign up for AWS
    * Use google authenticator app and scan the QR code 
    * update the MFA code and assign MFA
    * Whenever you are doing anything inside IAM , the reigon is global and you are using the root account.

  - AWS recommends very limited usage of root account

  - Setup MFA on root account.

  - You can attach permissions to individual users and groups.

  - **Secret access key** can be retrieved only once during user creation. In case you lose it then you can re-generate it.

  - **IAM Password policy** can be set to access the admin console.

  - **New users have no permissions when first created**. Everything has to be explicitly added.

  - **Power User Access** allows Access to all AWS services except the management of groups and users within IAM.

Manage AWS resources via

1. **Management console** – Using username and password

2. **Rest APIs** – Using Access Key ID and Secret Access Key

3. **AWS CLI** - Command Line Interface - Using Access Key ID and Secret Access Key

4. **AWS SDK** – various programming languages supported.

Using Access Key ID and Secret Access Key – can be used only via accessing programmatically. Akin to username and password used while accessing the console

# Certification Questions
1. A company is storing an access key (access key ID and secret access key) in a text file on a custom AMI. The company uses the access key to access DynamoDB tables from instances created from the AMI. The security team has mandated a more secure solution. 
Which solution will meet the security team’s mandate? 

  * A. Put the access key in an S3 bucket, and retrieve the access key on boot from the instance.  
  * B. Pass the access key to the instances through instance user data. 
  * C. Obtain the access key from a key server launched in a private subnet.  
  * D. Create an IAM role with permissions to access the table, and launch all instances with the new role. 

## Answers 
* 1 - D – IAM roles for EC2 instances allow applications running on the instance to access AWS resources without having to create and store any access keys. Any solution involving the creation of an access key then introduces the complexity of managing that secret. 
