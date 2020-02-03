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

  - **Users** – End users / people, employees of an organization.

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
