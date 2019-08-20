**AWS – Concepts and Components**
-   AWS Global Infrastructure
    -   12 Regions & 33 AZs, 5 more Regions & 11 more AZs coming throughout the next year
    -   Region = 2 or more AZs
    -   AZ = DataCenter
    -   Edge Location = CDN End Points for CloudFront (there are currently more edge locations than regions)
-   Networking
    -   VPC = Virtual Private Cloud
    -   Direct Connect = connecting to AWS w/out using Internet connection
    -   Route53 = DNS service (port 53… duh)
-   Compute
    -   EC2 = virtual server
    -   EC2 Container Service = EC2 with Docker
    -   Elastic Beanstalk = Service for deploying web applications and services. “AWS for beginners”
    -   Lambda = “Most powerful/revolutionary service”. Run code w/out servers. Pay for execution time, only charged when code is executed.
-   Storage
    -   S3 = Object based storage, a place to store flat files in the cloud
    -   CloudFront = CDN (content delivery network), local caching of content
    -   Glacier = long term backup, 3-5 hours to retrieve data
    -   EFS = NAS in the cloud, block level storage (in preview)
    -   Snowball = Import/Export service. For moving large amounts of data in/out of AWS. They ship you a physical suitcase of disks
    -   Storage Gateway = VM that you run locally that replicates data from local datacenter to AWS
-   Databases
    -   RDS = SQL, Aurora, Oracle, PostgreSQL, MySQL, MariaDB
    -   DynamoDB = NoSQL
    -   Elasticache = Caching DB services in cloud to relieve stress on RDS for high I/O environments
    -   Redshift = Data warehousing service. Great performance
    -   DMS = Database Migration Services. How to migrate/convert local DBs into AWS
-   Analytics
    -   EMR = Elastic Map Reduce. A way of processing big data
        -   Managed web service Hadoop clusters
    -   Data Pipeline = moving data from one service to another
    -   Elastic Search = Managed service to deploy/operate a search engine in cloud
    -   Kinesis = managed service platform for real time streaming of big data.
        -   Web apps, mobile devices, wearables generate huge amounts of streaming data.
        -   Use kinesis to digest big data
    -   Machine Learning = for use by developers to work with machine learning…. (not in test)
    -   Quick Sight = Business Intelligence service (not in test)
-   Security & Identity
    -   IAM = control users, roles, groups, policies
    -   Directory Services
    -   Inspector = install agents on EC2 instances & check for vulnerabilities (not in test)
    -   WAF = Web Application Firewall condition sets:
        -   IP Match
        -   String Match
        -   SQL Injection Match
        -   Size Constraint
        -   Cross-site Scripting Match
    -   Cloud HSM = Hardware Security Module
    -   Certificate Manager
-   Management Tools
    -   CloudWatch = Monitor
    -   CloudFormation = Use templates to create infrastructure stacks
        -   Use “CloudFormer” to create a template of your existing infrastructure to capture and redeploy applications you already have running
    -   CloudTrail = track user & API activity
        -   By default, log files are stored indefinitely
    -   Config = Track resources & inventory changes (not in test)
    -   OpsWorks = automation
        -   Orchestration service that uses Chef
        -   Chef consists of recipes to maintain a consistent state
        -   Look for “chef”, “recipes”, “cookbook” in exam & think Opsworks
    -   Service Catalog = not in test
    -   Trusted Advisor = scans environment for ways to save money & increase security
-   Application Svcs
    -   API Gateway = not in test
    -   AppStream = AWS version of XenApp
    -   CloudSearch = Managed search solution
    -   Elastic Transcoder = Media transcoding service, change media files from source format to destination format
    -   SES = Simple Email Service = send/receive emails
    -   SQS = Simple Queue Service, a way of decoupling infrastructure
    -   SWF = Simple WorkFlow Service
-   Dev Tools (not in test)
    -   CodeCommit = “Github”
    -   CodeDeploy = automates code deployment
    -   CodePipeline = build, test, deploy code
-   Mobile Svcs (not in test, except for SNS)
    -   Mobile Hub = test mobile apps
    -   Cognito = save mobile user data in AWS cloud
    -   Device Farm = test against real smartphones & tablets in AWS cloud
    -   Mobile Analytics =
    -   SNS = big topic in exam, Simple Notification Service. Way to send notifications from cloud
-   Enterprise Applications
    -   WorkSpaces = VDI
        -   Replaces Windows PC in the cloud (PCoIP)
        -   Runs Windows 7, provided by Windows Server 2008 R2
        -   Are persistent (EBS)
        -   All data on D drive backed up every 12 hours
        -   Do not need an AWS account to login to workspaces
        -   Don’t need an existing AD domain, can use free client app
        -   Can integrate with existing AD domain
        -   By default:
            -   Users can personalize their WorkSpaces with wallpaper, icons, shortcuts, etc..
            -   Users have local admin access to install apps
    -   WorkDocs = DropBox for enterprise
    -   WorkMail = Exchange
-   IoT
    -   Internet of Things = not in test

**Identity Access Management (IAM)**
-   Central control of AWS account
-   Share access
-   Granular permissions of accounts/groups/roles/policies
-   Identity Federation (AD, Facebook, LinkedIn, etc…)
-   MFA = Multi Factor Authentication
-   Temp access for users/devices/services
-   Pwd rotation policy highly customizable
-   Policies = JSON key/value pairs
-   IAM is universal, applies to all regions consistently
-   New Users have no permissions when 1<sup>st</sup> created
-   New Users are assigned an access key ID & secret access key when first created, only viewable once so download it & secure!
-   Always setup MFA on root
-   Integrated with AWS marketplace

**S3**
-   Secure, durable, highly scalable object storage. “Unlimited storage”. A hard drive in the cloud.
-   Object based NOT block based storage (no OS or DBs -&gt; that’s Elastic Block Storage (EBS)). i.e. allows you to upload files
-   0 byte to 5Tb file size
-   Files are stored in buckets
-   S3 is a universal namespace, each one must be unique:
    -   <http://s3-aws-region.amazonaws.com/%3Cbucket>&gt;
-   EXAM Tips
    -   Read after Write consistency for PUTS of new Objects
    -   Eventual consistency for overwrite PUTS and DELETES as it can take time to propagate
-   S3 = Object based. Objects consist of the following:
    -   Key = name of the object
    -   Value = the data
    -   Version ID (for versioning)
    -   Metadata (tags)
    -   Subresources
    -   Access Control Lists (ACLs)
-   99.99% availability
-   99.999999999% durability
-   Tiered storage
-   Lifecycle mgmt.
    -   Can be used in conjunction with versioning
    -   Can be applied to both current & previous versions
    -   Actions:
        -   Transition to S3-IA (128Kb & 30 days after creation)
        -   Archive to Glacier (30 days after S3-IA, if relevant)
-   Encryption, ACLs & Bucket Policies
-   Storage Tiers
    -   S3
        -   99.99% availability
        -   99.999999999% durability
        -   Redundant, designed to sustain loss of 2 facilities concurrently
    -   S3-IA (infrequently accessed)
        -   99.9% availability
        -   99.999999999% durability
        -   Lower fee than S3, but charged a retrieval fee
    -   S3-RRS (Reduced Redundancy Storage)
        -   99.99% availability
        -   99.99% durability
    -   Glacier
        -   Very cheap (as little as $0.01 GB/mo.)
        -   Used for archive only
        -   Takes 3-5 hours to restore from Glacier
-   Versioning
    -   Stores all versions of an object (including all writes and deletes)
    -   Great backup tool
    -   Cannot disable versioning once enabled, but you can suspend
    -   Integrates with lifecycle rules
    -   Can use MFA delete capability, so that you can’t delete without MFA
    -   Cross Region Replication requires versioning – only applies to files manipulated \*after\* CRR is turned on
    -   Can take up a LOT of space on files that change a lot (because it stores each changed version)

**S3 – Security & Encryption**
-   By default, all new buckets are PRIVATE
-   2 types of access control for buckets
    -   Bucket policies
    -   ACLs
-   Buckets can be configured to log all requests
    -   Can be done to another bucket or to another AWS account
-   Encryption – 4 methods
    -   In transit – information to/from bucket
        -   Uses SSL/TLS
    -   At rest:
        -   Server Side Encryption (SSE)
            -   S3 Managed keys – **SSE-S3**
            -   AWS Key Management Service, Managed Keys – **SSE-KMS**
                -   Provides usage audit trail
            -   SSE w/ Customer Provided Keys – **SSE-C**
    -   Client Side Encryption – the customer encrypts data prior to uploading to bucket

**CloudFront – CDN (Content Delivery Network)**
-   Edge Location – Where the content will be cached (different from Region or AZ)
    -   Not just read only, can write to them too.
    -   Objects are cached for the life of the TTL (default 24 hours)
    -   Can clear cached objects, but you will be charged
-   Origin – Where the original server content is located (S3 Bucket, EC2 instance, Route53, or ELB for AWS)
-   Not faster for the 1<sup>st</sup> user, but faster for every other subsequent user
-   Can be used for static, dynamic, streaming & interactive content
-   Requests are automagically routed to nearest Edge Location
-   Optimized to work well with other AWS services (duh)
-   Also works with non-AWS origin servers (the “definitive version”)
-   2 types of Distributions:
    -   Web Distribution – Used for websites
    -   RTMP Distribution – used for media streaming
-   CloudFront options
    -   Restrict Viewer Access – restrict using signed URLs or signed cookies

**Storage Gateway**
-   Connects on-prem software appliance with AWS storage to provide seamless & secure between an org’s on-prem IT environment & AWS storage infrastructure.
-   Asynch replication backed up to S3 as EBS snapshots
-   Data is stored within a single region (user specified)
-   Software appliance is supported on VMware or Hyper-V
-   3 types of storage gateways:
    -   **Gateway Stored Volumes (cloud is backup)**
        -   Keep entire data set on-prem & asynch backed up to S3
        -   Create storage volumes up to 16TB in size & mount them as iSCSI devices
        -   Used for offsite backups
        -   Constantly replicating changes up to S3 in the form of Amazon EBS snapshots
    -   **Gateway Cached Volumes (cloud is primary)**
        -   Only most frequently accessed data is stored on-prem, entire data set is stored in S3
        -   Using S3 as your SAN array
        -   Create storage volumes up to 32TBs in size & mount them as iSCSI devices
        -   If you lose internet access, you lose access to all your data
    -   **Gateway Virtual Tape Library (VTL)**
        -   Limitless collection of virtual tapes
        -   Up to 10 virtual tape drives per gateway
        -   Exposes iSCSI interface so populat backup application (Netbackup , Backup Exec, Veeam, ect..) can point directly to VTL
-   Pricing:
    -   Only pay for what you use, 4 pricing components:
        -   Gateway usage (per gateway per month)
        -   Snapshot storage usage (per GB per month)
        -   Volume storage usage (per GB per month)
        -   Data xfer out (per GB per month)

**Snowball (Import/Export) 2 Types:
-   Import/Export Disk
    -   You ship your disks to AWS site of your choice
    -   Import into S3, Glacier, or EBS
    -   Export from S3 
-   Import/Export Snowball
    -   Available in US, EU(Ireland) & APAC(Sydney)
    -   50TB or 80TB models available
    -   256-bit encryption
    -   TPM ensures chain-of-custody
    -   Import into S3 only
    -   Export from S3

**S3 Transfer Acceleration (probably not in exam yet)**
-   Use Edge Network to accelerate uploads to your S3 bucket
-   Better performance the further you are away from your bucket
-   Incurs an additional fee

**EC2 (Elastic Compute Cloud) – “**A web service that provides resizable
compute capacity in the cloud. Reduces time required to obtain & boot
new server instances to minutes allowing the ability to quickly scale
capacity both up and down.”

Pricing models:
-   On Demand – pay fixed rate by the hour with no commitment
    -   Best for burst need servers & unpredictable workloads that cannot be interrupted
    -   For users that want flexibility of EC2 w/out up-front payments or long-term commitment
    -   Test/Dev for apps running on EC2 for the 1<sup>st</sup> time.
    -   Supplement reserved instance servers (for extra temporary server load)
-   Reserved – 1 or 3 year term. Discount compared to On Demand, the longer your contract, the more you save.
    -   Best for “steady state” systems that you’ll always have running
    -   Apps that need reserved capacity, steady state or predictable usage
        -   Domain Controllers
        -   1<sup>st</sup> web server
-   Spot – Allows you to bid for whatever price you want to pay for instance capacity (by hour).
    -   When your bid = spot price, you get a server
    -   When spot price exceeds your bid, you lose server with 1 hour warning
    -   Best used for grid computing where instances are disposable & applications have flexible start/stop times
    -   If spot instance is terminated by EC2, you don’t get charged for partial hour of usage. If \*you\* terminate, you’ll get charged for the full hour.

**EC2 Instance Types:
(Reminder is mrmcgiftpx = Docter MC Gift Pics)

| **Family** | **Speciality**                | **Use Case**                     |
|------------|-------------------------------|----------------------------------|
| T2         | Lowest Cost, Gen Purpose      | Web Svr, small DB                |
| M4         | Gen Purpose (**M**ain)        | App                              |
| M3         | Gen Purpose (**M**ain)        | App                              |
| C4         | **C**ompute Optimized         | High CPU App/DB                  |
| C3         | **C**ompute Optimized         | High CPU App/DB                  |
| R3         | Mem Optimized (**R**AM)       | High Mem App/DB                  |
| G2         | **G**raphics                  | Vid Encoding, 3D Apps, Streaming |
| I2         | High Speed Storage (**I**OPS) | NoSQL DBs, Data Warehousing      |
| D2         | **D**ense Storage             | File srv, Hadoop                 |

**EBS (Elastic Block Storage) – **Storage volumes that are attached to EC2 instances (think VMDKs)
-   EBS versus EFS versus S3 https://stackoverflow.com/questions/29575877/aws-efs-vs-ebs-vs-s3-differences-when-to-use
-   Can’t attach 1 EBS instance to 2 EC2 instances (use EFS for that)
-   Can attach multiple EBS instances to 1 EC2 instance
    -   How to “grow” an EBS volume:
        -   Detach the original Amazon EBS volume.
        -   Create a snapshot of the original Amazon EBS volume’s data in Amazon S3.
        -   Create a new Amazon EBS volume from the snapshot, but specify a larger size than the original volume.
        -   Attach the new, larger volume to your Amazon EC2 instance in place of the original. (In many cases, an OS-level utility must also be used to expand the file system.)
        -   Delete the original Amazon EBS volume.
-   Placed in specific AZs & automatically replicated
-   EBS 3 Volume Types
    -   General Purpose SSD (GP2)
        -   99.999% availability
        -   Ratio of 3 IOPs per GB & ability to burst up to 3k IOPS for short periods for volumes under 1Gb.
        -   Use if you need up to 10k IOPS
    -   Provisioned IOPS SSD (I01)
        -   For I/O intensive apps (large DBs).
        -   Use if you need more than 10k IOPS
    -   Magnetic (standard)
        -   Cheapest
        -   Good for infrequently accessed data (fileservers)

**\*Know how to create a VPC from memory for exam!\***
-   When creating an AMI, on Step 4(Add storage) “Delete on Termination” is checked and not encrypted by default (i.e. Termination protection is turned off by default):

![Image01](/images/060116_1515_AWSCertifie1.png?raw=true)

-   On an EBS-backed instance, the default action is for the root EBS vol to be deleted when the instance is terminated.
-   Root volumes cannot be encrypted by default, you’ll need a 3<sup>rd</sup> party tool (bit locker, etc) to encrypt root vols.

**Security Group Basics:**
-   All inbound traffic is blocked by default (except for ssh for listros and rdp for windows)
-   All outbound traffic is allowed by default
-   Can edit security groups on the fly. **Edits take effect immediately**.
-   To install Apache on AWS AMI:
    -   *yum install httpd –y*
    -   *service httpd status*
    -   *service httpd start*
    -   *chkconfig httpd on*
-   Can’t add a rule to deny a specific protocol inbound or outbound
-   Security groups are stateful:
    -   If you allow a protocol inbound, automatically it’s added to outbound
-   Can have any \# of instances in a security group

**Volumes vs Snapshots**
-   Volume
    -   A volume is a virtual hard disk (think VMDK)
    -   Volumes exist on EBS
    -   If you take a snapshot of a volume, this will store that volume on S3
-   Snapshot
    -   Point in time copy of a volume
    -   Exists on S3
    -   Are incremental, only the blocks that have changed since the last snap are moved to S3
    -   1<sup>st</sup> snap takes some time to create
    -   Can use snap to create a new volume & change the disk type (magnetic -&gt; GP2 or IO1 or any other combination)
    -   If you want to snap a root volume, you should stop the instance before taking snap
        -   If you don’t, AWS will stop it prior to taking snap.
Go into EC2 -&gt; Volumes -&gt; create volume (make sure it’s in the
same AZ as your server!) -&gt; Actions -&gt; attach to server.
Use *lsblk *to view disks to confirm new volume attached.
Use *file –s /dev/xvdf *to make sure it’s clean
Use *mkfs –t ext4 /dev/xvdf *to make file system, then *mkdir
/fileserver *to create directory*, & mount /dev/xvdf/fileserver *to
mount

**Volumes vs Snapshots – Security**
-   Snapshots of encrypted vols are encrypted automatically
-   Vols restored from encrypted snaps are also automatically encrypted
-   You can share snaps, but only if they are unencrypted
    -   They can be shared to other AWS accounts or made public

**RAID, Volumes & Snapshots**
-   RAID = Redundant Array of Independent Disks
    -   RAID 0 – Striped, no redundancy, good performance
    -   RAID 1 – mirrored, redundancy
    -   RAID 5 – good for reads, bad for writes, **AWS does not recommend ever putting RAID 5’s on EBS**
    -   RAID 10 – Striped & Mirrored, good redundancy, good performance
-   Why create a RAID in AWS?
    -   Not getting Disk I/O that you require from GP2 or IO1 on a single volume.
-   How do you snap a RAID array?
    -   Stop the app from writing to disk… how?
    -   Take application consistent snap using one of these 3 methods:
        -   Freeze file system
        -   Unmount RAID array
        -   Shut down EC2 instance

**Create an AMI (Amazon Machine Image)**
-   AMI = template VM
-   Are regional. You can only launch an AMI from the region where it’s stored. You CAN copy AMI’s to other regions using the command line/console/API.
-   Contains:
    -   Template for root volume for the instance (OS, application servers, apps, etc)
    -   Launch permissions that control with AWS accounts can use the AMI to launch instances
    -   Block device mapping that specifies which volumes to attach when launching instance
-   By default, any AMI you create is private. You can modify image permission to make it public.
-   ![Image02](/images/060116_1515_AWSCertifie2.png?raw=true)
-   **Read these articles on how to harden & clean up an AMI before making public!**
    -   <https://aws.amazon.com/articles/9001172542712674>
    -   <http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/building-shared-amis.html>

**AMI Types (EBS vs Instance Store)**
-   You can select your AMI based on:
    -   Region
    -   OS
    -   Architecture (32 or 64 bit)
    -   Launch Permissions
    -   Storage for the Root Device (root vol), 2 types:
        -   Instance Store (ephemeral storage)
            -   Can’t “stop” an instance of this type, only reboot or terminate. If the underlying host fails, you will lose data.
            -   You can reboot without losing data, if you stop the instance, the data will be wiped.
            -   “Ephemeral storage” means exactly that, not persistent
            -   The root device for an instance launched from the AMI is an instance store volume created from a template stored in S3
            -   Cannot be detached and reattached to other EC2 instances
        -   EBS backed volumes
            -   Are persistent
            -   The root device for an instance launched from the AMI is an EBS volume created from an EBS snapshot
            -   Can be stopped, you will not lose data if the underlying host fails.
            -   Can be detached and reattached to other EC2 instances
            -   By default, both root vols will be deleted on termination, but you can choose to keep an EBS vol on termination, not for ephemeral.

**Elastic Load Balancers (ELB)**
-   ELB is never given a static IP address, just DNS name.
-   ELBs can be “In Service” or “Out of Service”
-   Thresholds
    -   Unhealthy Threshold = how many intervals with no response before flagging as Out of Service
    -   Healthy Threshold = how many intervals with response before flagging as In Service
-   Support the following X-Forwarder headers:
    -   X-Forwarded-For
    -   X-Forwarded-Proto
    -   X-Forwarded-Port

**CloudWatch – Performance Monitoring Service**
-   Standard monitoring = 5 minutes
    -   Turned on by default
-   Detailed monitoring = 1 minute
-   Monitors the hypervisor, NOT the guest OS
    -   Does not monitor memory
-   Dashboards – create/configure widgets to monitor your environment
-   Alarms – notify when a given threshold is hit
-   Events – automatically respond to state changes in your AWS resources
-   Logs – aggregate, monitor & store logs. Agent installed onto EC2 instances

**AWS Command Line
– **[**http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html**](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)
-   You can only assign a role to an EC2 instance during its creation!
-   AWS command line preinstalled on the AWS AMI
-   Commands:
    -   *Aws configure*
        -   Input access key, Secret Access key, default region name (in doc above) & output format (I just hit enter)
    -   *Aws s3 help*
        -   Make Bucket = mb
        -   Remove Bucket = rb
![Image01](/images/060116_1515_AWSCertifie3.png?raw=true)
-   If you use roles, you don’t have to store your credentials on your EC2 instance (which is a security risk)

**IAM – Roles**
-   Roles can only be assigned to an EC2 instance when you are launching it.
-   Roles are more secure than storing access keys on individual EC2 instances
-   Roles are easier to manage
-   They are universal, can be used in any region/AZ
-   Useful for:
    -   Federated (non-AWS) user access
        -   Microsoft AD, LDAP, Kerberos
        -   Can create trust if org supports SAML 2.0
    -   Cross-Account Access
        -   Multiple AWS accounts
    -   Applications running on EC2 instances that need access to other AWS resources
        -   EC2 instance hitting an S3 bucket or DynamoDB table

**Bash Scripting**
-   Write a script that EC2 instance will run when 1<sup>st</sup> being provisioned
    -   Install apache
    -   Run updates
    -   Move file from S3 to apache dir to create website
-   How to write the bash script
    -   *\#!/bin/bash*
    -   *Yum install httpd –y*
    -   *Yum update –y*
    -   *Aws s3 cp s3://&lt;BUCKETNAME&gt;t/index.html /var/www/html*
    -   *Service httpd start*
    -   *Chkconfig httpd on*
-   Provision an AWS AMI instance per usual, but in the advanced section put in the above script

![Image04](/images/060116_1515_AWSCertifie4.png?raw=true)

**Instance Metadata –**
-   How to access instance metadata from within an EC2 instance. From CLI:
    -   Sudo su
    -   Curl <http://169.254.169.254/latest/meta-data>
        -   This could be triggered from a bash script & returns a bunch of different variables, which can then be used to perform various functions:
            -   Write data to an html page
            -   Trigger a lambda function to update DNS
            -   Whatever else you can think of 

![Image05](/images/060116_1515_AWSCertifie5.png?raw=true)

**Auto scaling Groups**
-   Have to have a launch configuration to have an auto scaling group
-   Can create rules to spin-up and/or shut down instances based on monitor triggers
-   Deleting an auto scaling group will automatically delete any instances it created

**EC2 Placement Groups**
-   A logical grouping of instances within a single AZ.
    -   Can’t span AZs (duh)
-   Enables applications to participate in low-latency, 10 GBps network
-   Recommended for apps that benefit from low latency networks, high network throughput, or both
    -   Grid computing
    -   Hadoop clusters
-   Name must be unique within your AWS account
-   Only certain types of instances can be launched in a placement group
    -   Compute Optimized
    -   GPU
    -   Memory Optimized
    -   Storage Optimized
-   AWS recommends homogenous instances within a placement group (size & family)
-   Can’t merge placement groups
-   Can’t move an existing instances into a placement group. You \*can\* create an AMI from your existing instance THEN launch a new instance from that AMI into a placement group… if you really wanted to.

**Elastic File System (not in exam yet)**
-   File storage for EC2 instances
-   Elastic capacity
-   Can mount multiple EC2 instances to 1 EFS “volume”
-   Supports NFSv4 & thousands of connections
-   Only pay for the storage you use (don’t need to pre-provision)
-   Scales up to PBs
-   Data is stored across multiple AZs within a region
-   Read after write consistency
-   File based storage

**Lambda concepts**

-   Compute service that runs your code in response to events and it automatically manages the underlying compute resources for you
-   Can automatically run code in response to events
    -   Modifications to objects in S3 buckets
    -   Messages arriving in Kinesis stream
    -   Table updates in DynamoDB
    -   API call logs created by CloudTrail
    -   Etc…
-   A new abstraction layer – run code without worrying about infrastructure at all
-   Javascript is the supported programming language
-   99.99% availability for the service and the functions it operates
-   1<sup>st</sup> 1 million requests are free, $0.20 per 1 million requests afterwards

**Route53 (DNS)**
-   IPv6 not fully supported yet.
-   Alias records work like CNAME records
    -   Used to map resource record sets in your hosted zone to ELB, CloudFront distributions, or S3 buckets that are configured as websites.
    -   Difference – a CNAME can’t be used for naked domain names (i.e. w/out “www”), you can with A record or Alias.
    -   Automatically recognizes changes in the record sets
-   ELBs don’t have a pre-defined IPv4 address, resolved using DNS
    -   This can be an issue because naked domain names need an IP address.
    -   Hence the need for Alias records
-   Given a choice, always choose an Alias record because you won’t incur additional charges (as you would with a CNAME)

**DNS Routing Policies:**
-   Simple
    -   Default when you create a new record set
    -   Most commonly used when you have a single resource that performs a given function (i.e. 1 webserver)
    -   No built-in intelligence
-   Weighted
    -   Split traffic based on weighted assignments (10% to X, 90% to Y)
    -   Different regions, ELBs, AZs, etc.
    -   Commonly used when testing a new website & you only want a small subset to see the new site
-   Latency
    -   Route traffic based on lowest network latency for your end user
    -   Need to create a latency resource record set for the EC2 or ELB resource in each region you want participating.
    -   Great for improving global page load times
-   Failover
    -   Used when you want to create an active/passive set up.
    -   Route53 will monitor health of primary site using a health check (which monitors your end points)
-   Geolocation
    -   You choose were traffic will be sent based on location of users
    -   Ex. All EU users get routed to servers w/ local language and prices in Euros

**Databases**
-   RDS – Been around since the 70s. Database: tables, rows, fields (columns) -&gt; think spreadsheet
    -   Read this FAQ: <https://aws.amazon.com/rds/faqs/>
    -   For OLTP
    -   SQL Server
    -   Oracle
    -   MySQL
    -   PostgreSQL
    -   Aurora
    -   MariaDB
-   DynamoDB – non-relational databases (No SQL)
    -   Database:
        -   Collection     = Table
        -   Document     = Row
        -   Key/Value pairs    = Fields
-   ElastiCache
    -   web service that deploys, operates & scales an in-memory cache. Improves performance of web apps by retrieving info from RAM instead of disk.
    -   Supports 2 open source in-mem caching engines
        -   Memcached
        -   Redis
    -   Caches most consistently queried data
-   Redshift (data warehousing)
    -   OLAP
    -   Used for BI. Cognos, Jaspersoft, SAP Netweaver
    -   Used to pull in large & complex data sets. Usually used to do queries on data.
-   DMS (database migration services)
    -   Migrate your prod DB into AWS
    -   AWS manages all the complexities of migration like data type transformation, compression & parallel xfer
    -   Schema conversion tool:
        -   Convert source DB to a different target DB (Oracle -&gt; Aurora, etc…)
-   Backups, Multi-AZ & Read Replicas
    -   Backups (2 types):
        -   Automated
            -   Recover DB to any point in time within retention period (between 1 – 35 days)
            -   Point in time recovery down to a second, up to the last 5 minutes
            -   Enabled by default
            -   Backup data is stored in S3
            -   Free backup storage equal to size of DB
            -   Backups are taken within a defined window, retention period up to 35 days
            -   During backup, I/O suspended (typically a few minutes)
                -   This can be avoided if you go Multi-AZ as the backup is taken of the standby
        -   DB Snapshots
            -   Done manually (user initiated), full backup
            -   Stored even after you delete the original RDS instance, until you explicitly delete them
            -   When you restore either automated or snap, the restored version will be a new RDS instance with a new endpoint
    -   Encryption
        -   At rest is supported for MySQL, Oracle, SQL, PostgreSQL & MariaDB
        -   Done using AWS KMS
        -   Once your RDS instance is encrypted at rest – underlying storage, backups, read replicas and snaps are also encrypted
        -   Turning on encryption for an existing instance isn’t supported… create a new encrypted instance & migrate data to it
    -   Multi-AZ
        -   Primary RDS instance uses synchronous replication to an RDS in a diff AZ.
        -   Automatic failover, same DNS point, AWS handles replication
        -   Disaster Recovery only, not performance improvement
        -   Only in:
            -   SQL Server
            -   Oracle
            -   MySQL Server
            -   PostgreSQL
            -   MariaDB
    -   Read Replica
        -   Uses asynchronous replication to create up to 5 read-only DB copies
        -   Used for performance improvement & Scaling, not DR:
            -   Write to prod, read from read replicas
        -   Must have automatic backups turned on
        -   You can have read replicas OF read replicas, but watch out for latency if you do this.
        -   Each read replica will have it’s own DNS end point.
        -   Cannot have read replicas that have Multi-AZ but you CAN create read replicas of Multi-AZ source DBs
        -   Can break replication & turn a read replica to it’s own source DB
        -   Only in:
            -   MySQL Server
            -   PostgreSQL
            -   MariaDB
    -   DynamoDB vs RDS
        -   DynamoDB offers “push button” scaling -&gt; scale DB on the fly with no downtime
        -   RDS isn’t as easy -&gt; usually need to create bigger instance size manually or add a read replica
-   DynamoDB
    -   Fast, flexible NoSQL DB service.
    -   Used for apps that need consistent, single-digit millisecond latency at any scale
    -   Fully managed & supports document and key/value data models
    -   Stored on SSD storage
    -   Spread across 3 “geographically distinct” data centers
    -   Multiple consistency models:
        -   Eventually consistent reads (default)
            -   Consistency usually reached within 1 second (best read performance)
        -   Strongly consistent reads
            -   Returns a result that reflects all writes that got a successful response prior to the read
            -   Use this if your app needs data back immediately & in less than 1 second.
    -   Pricing (not in exam):
        -   Write throughput $0.0065 per hour every 10 units
        -   Read throughput $0.0065 per hour every 50 units
        -   Storage = $0.25 per GB per month
        -   Expensive for writes, cheap for reads
-   Redshift
    -   Fast (10 times faster), fully managed petabyte-scale data warehouse service
    -   Can start small for $0.25 per hour with no commitments & scale up to PB or more for $1,000 per TB per year.
    -   OLAP transactions
    -   Data warehousing DBs us diff type of architecture from both a DB perspective & infrastructure layer.
    -   2 Configurations:
        -   Single node (160Gb)
        -   Multi-node
            -   Leader Node (manages client connections and receives queries)
            -   Compute Node (store data & perform queries and computations). Up to 128 Compute Nodes
    -   Columnar Data Storage – instead of rows, redshift organizes data by column
        -   Only columns involved in the queries are processed
        -   Columnar data is stored sequentially on the storage media
        -   Block size of 1MB for columnar storage
        -   Therefore requires far fewer I/Os, greatly improving performance
    -   Advanced Compression
        -   Columnar data can be compressed much better than row based data
        -   Redshift automatically samples data & chooses the best compression scheme
    -   Massively Parallel Processing (MPP):
        -   Automatically distributes data & query load across all nodes & newly added nodes
    -   Pricing:
        -   Compute Node Hours
            -   1 unit per node per hour
        -   Backup
        -   Data Transfer
    -   Security
        -   Encrypted in transit using SSL
        -   At rest using AES-256
        -   By default RedShift does it’s own key mgmt.
            -   Can manage keys through HSM (hardware security modules) or KMS if you want
    -   Only available in 1 AZ
        -   Can restore snaps to new AZs in the event of an outage
    -   Good choice if mgmt. runs lots of OLAP transactions & it’s stressing the DB
    -   Think Business Intelligence (BI)

-   Elasticache

    -   Caches things – if your app is constantly going to a DB to pull the same data over and over, you can cache it for faster performance
    -   Used to improve latency and throughput for **read-heavy app** workloads (social networks, gaming, media sharing) or **compute heavy** workloads (recommendation engine)
    -   Improves application performance by storing critical pieces of data in mem for low-latency access.
    -   Types of elasticache
        -   Memcached
            -   Widely adopted mem object caching system.
        -   Redis
            -   Open source in-mem key/value store.
        -   Supports master/slave replication & multi-AZ to achieve cross AZ redundancy
    -   Good choice if your DB is read heavy & not prone to frequent changing

-   Aurora
    -   MySQL compatible RDS DB engine
    -   Speed & availability of commercial DBs
    -   Simplicity & cost-effectiveness of open source DBs
    -   5x better performance than MySQL @ 1/10<sup>th</sup> the price of commercial DB w/ similar performance & availability
    -   Big challenge to Oracle
    -   Scaling capabilities:
        -   Start w/ 10Gb, scales in 10Gb increments up to 64Tb
        -   Compute scales up to 32vCPUs & 244Gb of mem
        -   2 copies of DB in each AZ w/ a min of 3 AZs (6 copies of data)
        -   Can handle loss of 2 copies w/out affecting write availability
        -   Can handle loss of 3 copies w/out affecting read availability
        -   Storage is self-healing. Blocks & disks are constantly scanned & repaired
    -   Replica features:
        -   Aurora Replicas (currently 15)
        -   MySQL read replicas (currently 5)

**VPC (Virtual Private Cloud)**
-   **For the exam know how to build a custom VPC from memory**
    -   Create VPC
        -   Define IP range (automatically creates default route table)
        -   Create subnets (automatically creates route table & nACL)
            -   Largest = /16, Smallest = /28
            -   AWS reserves the 1<sup>st</sup> 4 and last 1 IP address of any subnet, so /28 = 11 useable IPs
        -   Create IGW
            -   By default it’s detached, need to manually attach it to VPC
        -   Create custom route table & attach IGW to it
        -   Associate public subnet(s) to use new route
        -   Launch 1 instance per subnet
        -   Provision EC2 NAT instance
            -   Create security group for NAT instance

-   VPC = Think of it as a Virtual Datacenter
    -   By default you are allowed 5 VPCs per region
    -   Logically isolated section of AWS where you can launch AWS resources in a virtual network of your own definition
    -   You control the network environment: IP address range, subnets, routing tables, gateways, etc

-   Default VPC vs Custom VPC
    -   Default is user friendly, can deploy instances right away
    -   All subnets in default VPC have an internet gateway attached
    -   Each EC2 instance has both a public & private IP address
    -   If you delete default VPC, you have to call AWS to get it back

-   VPC Peering
    -   Connect 1 VPC to another VPC via direct network route using private IP addresses
    -   Instances behave as if they were on the same private network
    -   You can peer VPC’s with other AWS accounts & with other VPC’s in the same account **within a single region**
    -   AWS uses the existing infrastructure of a VPC to create a VPC peering connection. 
    -   It is not a gateway or a VPN connection.
    -   It does not rely on a separate piece of hardware
    -   No SPoF for communication or bandwidth bottleneck
    -   Peering is done in a star configuration. VPC A  VPC B  VPC C = A cannot talk to C unless you connect directly (**no transitive peering**)
    -   **Peers cannot have matching or overlapping CIDR blocks**
-   By default when you create a VPC it will automatically create a route table
-   If you choose dedicated tenancy for your VPC, any instances you create in that VPC will also be dedicated
-   1 subnet = 1 AZ, you cannot have subnets cross AZ
-   Don’t forget to add internet gateway
    -   1 IGW per VPC
    -   Need to attach IGW after you create it
-   Need to create InternetRouteTable if you want VPC to communicate in/out 

![Image06](/images/060116_1515_AWSCertifie6.png?raw=true)

-   Once you’ve created your IGW, any subnet associations you make to it will be internet accessible:

![Image06](/images/060116_1515_AWSCertifie6.png?raw=true)

-   A security group can stretch across multiple Regions/AZs where a subnet cannot

<!-- -->

-   VPC Flow Logs:

    -   Enables you to capture information about the IP traffic going to and from network interfaces in your VPC
    -   Data is stored using Amazon CloudWatch Logs, you can view and retrieve its data in Amazon CloudWatch Logs.
    -   Help with a number of tasks:
        -   Troubleshoot why specific traffic is not reaching an instance
        -   Diagnose overly restrictive security group rules
        -   Security tool to monitor the traffic that is reaching your instance.

**Network Address Translation (NAT)**
-   Allows your instances that do not have internet access the ability to access the internet via a NAT server instance
-   create security group
-   allow inbound & outbound on HTTP and HTTPS
-   provision NAT inside public subnet
-   **On a NAT instance, you need to change source/destination check to disabled**
-   Set up route on private subnet to route through NAT instance

**Access Control Lists (ACLs)**
-   A numbered list of rules (in order, lowest applies first)
-   Put down network access lists across the entire subnet
-   Over rules security groups
-   Acts as a basic firewall
-   VPC automatically comes with an ACL
-   When you create a new ACL, by default everything is DENY
-   Only one ACL per subnet, but many subnets can have the same ACL

**Application Services**

**SQS – most important service going into exam**
-   Read FAQ for SQS for exam: <https://aws.amazon.com/sqs/faqs/>
-   A distributed message queueing service that sits between a “producer” and “consumer” to quickly and reliably cache that message.
-   Allows you to decouple the components of an app so that they can run independently.
-   Eases message management between components
-   Any component can later retrieve the queued message using SQS API
-   Queue resolves issues if:
    -   The producer is producing work faster than consumer is processing
    -   Producer or consumer are only intermittently connected to network
-   Ensures delivery of each message at least once
-   Supports multiple writers and readers on the same queue
-   Can apply autoscaling to SQS 
-   A single queue can be used by many app components with no need for those components to coordinate amongst themselves to share the queue
-   SQS does NOT guarantee first in, first out (FIFO) delivery of message
    -   If you want this, you need to place sequencing information in each message so that you can reorder the messages after they come out of queue, or consider different queues when setting different priorities
-   SQS is a pull based system
-   30 seconds visibility time out by default
-   12 hour maximum visibilty time (can be changed with ChangeMessageVisibiity method)
-   Supports long polling (default is 20 seconds). Long poll waits and answers when messages arrive.
-   Engineered to provide “at least once” delivery of mgs, but you should design your app so that processing a message more than once won’t create an error
-   Messages can contain up to 256KB of text in any format
-   Billed at 64KB “chunk” – a 25kKB msg will be 4 x 64KB “chunks”
-   1<sup>st</sup> 1 million SQS requests per month are free
-   $0.50 per 1 million requests per month thereafter
-   A single request can have from 1 to 10 messages, up to a max total payload of 256KB
-   Each 64KB ‘chunk’ of payload is billed as 1 request.
    -   Ex: 1 API call with a 256KB payload is billed as 4 requests

**SWF – Simple Workflow Service**
-   Makes it easy to coordinate work across distributed app components
-   Enables apps to be designed as a coordination of tasks
-   Tasks represent invocations of various processing steps in a app which can be performed by:
    -   Executable code
    -   Web service calls
    -   Human actions
    -   Scripts

-   Amazon uses SWF to process orders on the amazon website to get you your stuffs
-   SWF vs SQS
    -   SQS has a retention period of 14 days, SWF up to 1 year for workflow executions
    -   SWF presents task-oriented API, SQS = message-oriented API
    -   SWF ensures a task is assigned only once and never duplicated, with SQS you need to handle the potential for duplicate messages
    -   SWF keeps track of all the tasks & events in an application. With SQS you need to implement application-level tracking, especially if you have multiple queues.

-   SWF Actors (3 types):
    -   Workflow Starters – an app that can initiate a workflow (amazon.com front end when placing an order)
    -   Deciders – control the flow of activity tasks (if cc declined – decide to send to alternative payments page)
    -   Activity workers – carry out tasks (payment now successful, go pull widget off shelf & mail it)

**SNS – Simple Notification Service**
-   Web service to setup, operate & send notifications from AWS.
-   Scalable, flexible, cost-effective way to publish messages from an app & deliver them to subscribers or other apps
-   Push notification to Apple, Google, Fire OS, Windows devices, etc..
-   Can deliver via SMS text messages, email, SQS queues, any HTTP endpoint
-   Can also trigger Lambda functions

-   SNS Subscribers:
    -   HTTP/S
    -   Email/Email-JSON
    -   SQS
    -   Application
    -   Lambda

-   Allows you to group multiple recipients using topics
-   One topic can support delivery to multiple endpoints types
    -   “Autoscale change” to my phone, my email etc… all properly formatted for the endpoint

-   All messages published to SNS are stored redundantly across multiple AZs

-   Instantaneous, push-based deliver (no polling)
-   Simple APIs & easy integration with apps
-   Flexible message delivery over multiple transport protocols
-   Pay as you go model with no up-front costs
-   Mgmt console offers simple point/click interface

-   SNS vs SQS
    -   Both messaging services in AWS
    -   SNS – Push
    -   SQS – Polls (pulls)

-   Pricing:
    -   $0.50 per 1 million SNS requests
    -   $0.06 per 100,000 notification deliveries over HTTP
    -   $0.75 per 100 notification deliveries over SMS
    -   $2.00 per 100,000 notification deliveries over email

**Elastic Transcoder**
-   Media transcoder in the cloud
-   Converts media file from original source format into different formats that will play on different endpoint devices
-   Provides transcoding presets for popular output formats
    -   Don’t need to guess about which settings work best on particular devices
-   Pay based on the minutes that you transcode & the resolution at which you transcode
-   [https://read.acloud.guru/easy-video-transcoding-in-aws-7a0abaaab7b8\#.eepluawzo](https://read.acloud.guru/easy-video-transcoding-in-aws-7a0abaaab7b8)

**White Paper Breakdown:**

**Overview of
AWS: **[**http://d0.awsstatic.com/whitepapers/aws-overview.pdf**](http://d0.awsstatic.com/whitepapers/aws-overview.pdf)

What is cloud computing? On demand delivery of IT resources and apps via the Internet w/ pay-as-you-go pricing. Cloud providers maintain the network-connected hardware while the consumer provisions and use what you need via web applications.

6 Advantages of Cloud:

1.  Trade capex for “variable expense”
2.  Benefit from economies of scale
3.  Stop guessing about capacity
4.  Increase speed & agility
5.  Stop spending money running & maintaining datacenters
6.  Go global in minutes

**Overview of Security
Processes: **[**http://d0.awsstatic.com/whitepapers/Security/AWS%20Security%20Whitepaper.pdf**](http://d0.awsstatic.com/whitepapers/Security/AWS%20Security%20Whitepaper.pdf)

-   State of the art electronic surveillance and multi factor accesscontrol systems
-   Staffed 24×7 by security guards
-   Access is least privilege based

Shared Security Model – AWS is responsible for securing the underlying infrastructure. YOU are responsible for anything you put on or connects to the cloud

AWS responsibilities:

-   Infrastructure (hardware, virtual infrastructure, software, networking, facilities, infra security)
-   Security configuration of it’s managed services (DynamoDB, RDS, Redshift, Elastic MapReduce, WorkSpaces)

Customer responsibilities:

-   IAAS – EC2, VPC, S3
-   Managed services – Amazon is responsible for patching, AV etc… but YOU are responsible for account mgmt. and user access. Recommended that MFA is implemented, SSL/TLS is used for communication, & API/user activity is logged using CloudTrail

Storage Decommissioning:

-   AWS uses NIST 800-88 to destroy data. All decommed magnetic storage devices are degaussed and physically destroyed.

Network Security:

-   Transmission Protection – Use HTTPS using SSL
-   For customers who need additional layers of network security, AWS provides VPCs & the ability to use an IPSec VPN between their datacenter & the VPC
-   Amazon Corporate Segregation – AWS production network is segregated from the Amazon corporate network by a means of a complex set of network security/segregation devices
-   DDoS mitigation
-   Prevent Man in the middle attacks (MITM)
-   Prevent IP Spoofing – the AWS controlled, host-based firewall will not permit an instance to send traffic with a source IP or MAC other than its own.
-   Prevent Port Scanning – Unauthorized port scans are a violation of T&Es. You must request a vulnerability scan in advance
-   Prevent Packet Sniffing by other tenants

AWS Credentials

-   Passwords
-   MFA
-   Access Keys
-   Key Pairs
-   X.509 certs

AWS Trusted Advisor

-   Inspects your AWS environment & makes recommendations to save money, improve performance & close security gaps:
-   Provides alerts for several of the most common security misconfigs:
    -   Leaving certain ports open
    -   Not creating IAM accounts for internal users
    -   Allowing public access to S3 buckets
    -   Not turning on user activity logging (AWS CloudTrail)
    -   Not using MFA on your root AWS account

Instance Isolation

-   Instances on same physical machine are isolated from each other via the Xen hypervisor.
-   The AWS firewall resides within the hypervisor layer, between the physical network interface & the instances virtual interface.
    -   All packets must pass through this firewall
-   Physical RAM is separated using similar mechanisms
-   Customer instances have no access to raw disk devices, only virtual disks
-   AWS proprietary disk virtualization layer resets every block of storage used by the customer
    -   Ensures customer X data isn’t exposed to customer Y
-   Mem allocated to guest is scrubbed (zeroed out) by hypervisor when it becomes unprovisioned
    -   Mem not returned to pool of free mem until scrubbing is complete
-   Guest OS
    -   Instances are completely controlled by customer. AWS does not have any access rights or back doors to guest OSes
    -   AWS provides the ability to encrypt EBS volumes & their snapshots with AES-256
-   Firewall:
    -   EC2 provides a complete firewall solution. By default inbound is DENY-ALL
-   ELB – SSL Termination on the load balancer is supported
    -   Allows you to ID the originating IP address of a client connecting to your servers, whether you are using HTTPS or TCP load balancing

-   Direct Connect:
    -   Slower to provision than a VPN because it’s a physical connection
    -   Bypass ISPs in your network path (if you don’t want traffic to traverse Internet)
    -   Procure rack space within the facility housing the AWS Direct Connect location & deploy your equipment nearby.
    -   Connect this equipment to AWS Direct Connect using a cross-connect
    -   Use VLANs (802.1q) to use 1 connection to access both public (S3) and private (EC2 in a VPC) AWS resources
    -   Available in
        -   10Gbps
        -   1Gbps
        -   Sub 1Gbps groups purchased through AWS Direct Connect Partners

**Risk and
Compliance**: <http://d0.awsstatic.com/whitepapers/compliance/AWS_Risk_and_Compliance_Whitepaper.pdf>
-   AWS mgmt. has a strategic business plan which includes risk identification & mitigation plans. This is re-evaluated at least bi-annually. 
-   AWS security regularly scans all Internet facing service endpoint IP addresses for vulnerabilities (these scans do not include customer instances)
-   Independent external vulnerability threat assessments are performed regularly by 3<sup>rd</sup> party security firms.
    -   Not meant to replace a customer’s own vulnerability scans

<!-- -->

-   SOC 1/SSAE 16/ISAE 3402
-   SOC2
-   SOC3
-   FISMA, DIACAP, & FedRAMP
-   PCI DSS Level 1 **can take credit card information with PCI compliance (software needs to be compliant too)**
-   ISO 27001
-   ISO 9001
-   ITAR
-   FIPS 140-2
-   HIPAA
-   Cloud Security Alliance (CSA)
-   Motion Picture Association of America (MPAA)

AWS Platform:

![Image08](/images/060116_1515_AWSCertifie8.png?raw=true)

**Storage Options in the Cloud: (2 docs?)**

[**http://media.amazonwebservices.com/AWS\_Storage\_Options.pdf**](http://media.amazonwebservices.com/AWS_Storage_Options.pdf)

[**http://d0.awsstatic.com/whitepapers/AWS%20Storage%20Services%20Whitepaper-v9.pdf**](http://d0.awsstatic.com/whitepapers/AWS%20Storage%20Services%20Whitepaper-v9.pdf)

**Architecting for the Cloud – Best
Practices: **[**http://d0.awsstatic.com/whitepapers/AWS\_Cloud\_Best\_Practices.pdf**](http://d0.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf)

Business Benefits:
-   Almost 0 upfront infrastructure investment
-   JIT infrastructure
-   More efficient resource utilization
-   Usage-based pricing
-   Reduced time to market

Technical Benefits:
-   Automation – “Scriptable infrastructure”
-   Auto-scaling
-   Proactive scaling
-   More efficient dev lifecycle
-   Improved testability
-   DR/BC baked in
-   “Overflow” traffic to the cloud

Design for Failure:
-   Assume that hardware will fail & outages will occur
-   Assume that you will be overloaded with requests
-   By being a pessimist, you think about recovery strategies during design time, which helps you design an overall better system

Decouple your components:
-   Build components that do not have tight dependencies so that if 1 component dies/sleeps/is busy, the other components are built so as to continue work as if no failure is happening.
-   If you see decoupling in exam, think SQS
-   WebServer – SQS – AppServer – SQS – DBServer

Implement Elasticity:
-   Proactive Cyclic Scaling – periodic scaling that occurs @ fixed intervals (daily, weekly, monthly, quarterly) i.e. “Payroll Monday”
-   Proactive Event Scaling – when you are expecting a big surge of traffic (Black Friday, new product launch, marketing campaign)
-   Auto-scaling based on demand – Create triggers in monitoring to scale up/down resources

Secure Your Application:
-   Only have the ports open to/from your various stacks to allow communication, no more (duh)

Consolidated Billing
-   1 paying account for all linked accounts in an org
-   Paying account gets 1 monthly bill
-   Paying account cannot access resources of the linked accounts
-   All linked accounts are independent of each other
-   20 linked accounts for consolidated billing (soft limit)
-   Easy to track charges & allocate costs
-   Volume pricing discount, resources of all your linked accounts are added up for discounts

Resource Groups & Tagging
-   Tags = Key/Value pairs attached to AWS resources
-   Metadata
-   Tags can be inherited sometimes:
    -   Autoscaling, CloudFormation, Elastic Beanstalk can create other resources
-   Resource Groups
    -   Make it easy to group resources using the tags that are assigned to them
    -   Contain info like:
        -   Region
        -   Name
        -   Health checks
        -   For EC2 – Public & Private IP addresses
        -   For ELB – Port configs
        -   For RDS – Database engine, etc.
    -   Use tag editor to find/modify resources in large volumes

Active Directory Integration:
-   User browses to ADFS URL
-   User authenticates against AD
-   User receives a SAML assertion
-   User’s browser posts the SAML assertion to the AWS sign-in endpoint for SAML
-   User’s browser receives the sign-in URL and is redirected to the console






# Additional Exam Tips

Side Note - Difference between Object Store (Files) and Block Store (DB). Dropbox uses S3 to store the actual data and metadata is stored in their own data centers.

## AWS Exam Tips

1. Kinesis - process large streams of data. To process data - Amazon Redshift and Elastic Map Reduce

2. EBS Instance Store vs EC2 instance store - EBS - Block store, long term storage can be attached/detached to different EC2 instances. However, attached to only 1 instance at a time. Data on the EBS volume will persist even after the instance is stopped. EC2 instance store is ephemeral – can’t be attached to multiple EC2 instances.

3. OpsWorks - Orchestration service that uses Chef - keywords *Chef, Recipes, Cook Books*. Infrastructure as Code

4. Elastic Transcoder - Convert media files into formats for various formats optimized for devices on the cloud. Don’t need to guess settings for various devices. Pay for minutes you transcode and minutes you transcode.  

5. SWF Actors - workflow starters, deciders and activity workers.

6. EC2 - get public ip - it’s in instance meta-data and not user data. Access link [http://169.254.169.254/latest/meta-data](http://169.254.169.254/latest/meta-data/local-ipv4)[/local-ipv4](http://169.254.169.254/latest/meta-data/local-ipv4)  - wget or curl.  User data is the shell script provided to the EC2 instance at startup. The user data is executed only once at boot time.

## Consolidated billing

  - Separate Paying Account and independent department / environment accounts.

  - Get granular control on expenditure per account.

  - Get volume discounts based on aggregate usage.

  - Current soft limit of 20 accounts to consolidate

## Cross Account Access.

  - Improve productivity for a multi account / multi role accounts on the AWS console, without the need to sign in again.

  - Grant access to different accounts for users

  - Need to explicitly set policies, roles accordingly.

## Resource Groups / Tagging

  - It is a collection of resources that share one or more tags.

  - Key value pairs attached to AWS resources. Tags can be inherited from other services that create them.

  - Once single dashboard for groups fulfilling a certain criterion on tags.

  - Can help track all the resources that you have spawned. And also learn about hidden resources – ones which you forgot that you created earlier.

  - Use tag editor to find resources that are not tagged.

## VPC Peering

  - Connection between 2 VPCs that allows you to route traffic between two VPCs using private addresses, without the need to traverse the internet or any gateway.

  - You can create VPC peering between own VPC or between another account *in the same region*

  - Ensure that the address space does not overlap.

  - Daisy chaining of VPC connections not possible. You need to setup individual connections between each VPC.

## Direct Connect

  - Establish dedicated network connection from your data center to AWS.

  - You can avoid using regular internet route. This is a dedicated, private network connection.

  - VPN connections are routed over internet. Can be setup in minutes.

  - AWS Direct Connect lets you establish a dedicated network connection between your network and one of the AWS Direct Connect locations. 

  - Direct Connect takes weeks/ months to setup

  - Helps reduce bandwidth cost. Consistent network performance and private connectivity to AWS VPC.

## Active Directory Integration

  - AD Connector – interface to your internal AD implementation on premise

  - You can authenticate to AWS console using AD credentials via SAML

  - After you authenticate to AD, then temporary token credentials are generated to allow you to login to the console.

## Workspaces.

  - VDI on the cloud. Replacement for physical desktop.

  - Access the desktop by workspace clients or browsers

  - Don’t need an AWS account to access workspaces. Administrators can setup authentication via existing AD domain.

  - Runs Windows 7 experience

  - Provides local administrator access.

  - Workspaces are persistent

  - All D: / data is backed up every 12 hours.

Q&A which I got incorrect.

1. What does an AWS Region consist of? - A distinct location within a geographic area designed to provide high availability to a specific geography.

2. Which AWS service is effectively a NAS in the cloud, allowing you to connect it to multiple EC2 instances at once? - EFS (Elastic File System). Note difference from EBS which is directly attached to an EC2 Instance. 

3. You need a service that will aggregate your data from multiple data sources (S3, DynamoDB, RDS, etc.) and provide business intelligence based on this data. Which AWS service should you use? - Quick Sight

# AWS Free Tier Usage

## Free Services Options –

[https://aws.amazon.com/free/](https://aws.amazon.com/free/)

Only t2.micro instance is free tier eligible.

[http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-free-tier.html](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-free-tier.html)

## Hourly Usage in the Free Tier

Some services, such as Amazon EC2, Amazon RDS, and Elastic Load Balancing, charge for usage on an hourly basis. The free tier for these services provides you with a monthly allotment of hours for the first 12 months. For example, the free tier for Amazon EC2 provides you with 750 hours usage of Linux (any combination of t2.micro and t1.micro instances), plus 750 hours usage of Windows (any combination of t2.micro and t1.micro instances). How you divide this allotment is up to you. For example, you can use one Linux instance continuously for a month, or 10 Linux instances for 75 hours a month.

In some cases, leaving your resources running maximizes your free tier benefits. For example, if you run an Amazon EC2 instance for only a portion of an hour, AWS counts that as an entire hour. Therefore, if you stop and start an Amazon EC2 instance three times in a single hour, you use up three hours of your monthly allotment.

## Free Tier Eligible Amazon Machine Images

When you start an Amazon EC2 instance, you must select an Amazon Machine Image (AMI) that is eligible for the free tier. Because of licensing restrictions, some AMIs are not eligible for the free tier.

AMIs that are eligible for the free tier are marked in the Amazon EC2 Launch Wizard as **Free tier eligible**. The free tier allotment for Linux and Microsoft Windows instances is counted separately; you can run 750 hours of a Linux t2.micro or t1.micro instance plus 750 hours of a Windows t2.micro or t1.micro instance each month for the first 12 months.

Third-party applications or services from AWS Marketplace are not eligible for the free tier.

# FAQs of Services

US Standard Region is renamed to US East (Northern Virginia) to keep consistency with other AWS regional naming conventions.

## RDS

  - Amazon RDS can automatically back up your database and keep your database software up to date with the latest version.

  - With optional [Multi-AZ deployments](https://aws.amazon.com/rds/faqs/#36), Amazon RDS also manages synchronous data replication across Availability Zones with automatic failover.

  - You are still responsible for managing the database settings that are specific to your application. You'll need to build the relational schema that best fits your use case and are responsible for any performance tuning to optimize your database for your application’s workflow – **RDS does not do performance tuning**.

  - Amazon RDS enables you to run a fully featured relational database while offloading database administration. Using one of our many relational database AMIs on [Amazon EC2](https://aws.amazon.com/ec2/) allows you to manage your own relational database in the cloud

  - By default, customers are allowed to have up to a total of 40 Amazon RDS DB instances. Of those 40, up to 10 can be Oracle or SQL Server DB instances under the "License Included" model.

  - The Amazon RDS maintenance window is your opportunity to control when DB instance modifications (such as scaling DB instance class) and software patching occur, in the event they are requested or required.

  - The only maintenance events that require Amazon RDS to take your DB instance offline are scale compute operations (which generally take only a few minutes from start-to-finish) or required software patching

  - If you are using RDS for MySQL or MariaDB, you can access the slow query logs for your database to determine if there are slow-running SQL queries and, if so, the performance characteristics of each

  - Q: Can I test my DB instance with a new version before upgrading?

Yes. You can do so by creating a DB snapshot of your existing DB instance, restoring from the DB snapshot to create a new DB instance, and then initiating a version upgrade for the new DB instance.

  - Functionally, reserved instances and on-demand DB instances are exactly the same. The only difference is how your DB instance(s) are billed: With Reserved Instances, you purchase a one or three year reservation and in return receive a lower effective hourly usage rate 

  - Reserved instances are purchased for the Region rather than for the Availability Zone. RI pricing is not applicable when changing region or any of the instance attributes.

  - Amazon RDS uses EBS volumes for database and log storage. Depending on the size of storage requested, Amazon RDS automatically stripes across multiple EBS volumes to enhance IOPS performance. For MySQL and Oracle, for an existing DB instance, you may observe some I/O capacity improvement if you scale up your storage. 

  - When increasing storage, no availability issues for DB. When scaling compute, temporary unavailability is experienced – set maintenance windows accordingly.

  - RDS SSD – fast and high I/O performance, Magnetic / Standard Store – small workloads with less frequently accessed data.

  - Q: What is the difference between automated backups and DB Snapshots?

The automated backup feature of Amazon RDS enables point-in-time recovery of your DB instance. When automated backups are turned on for your DB Instance, Amazon RDS automatically performs a full daily snapshot of your data (during your preferred backup window) and captures transaction logs (as updates to your DB Instance are made). 

DB Snapshots are user-initiated and enable you to back up your DB instance in a known state as frequently as you wish, and then restore to that specific state at any time

  - Amazon RDS DB snapshots and automated backups are stored in S3.

  - Automated backups are deleted when the DB Instance is deleted. Only manually created DB Snapshots are retained after the DB Instance is deleted.

  - Amazon RDS manages backups, software patching, automatic failure detection, read replicas and recovery whether your DB Instances are deployed inside or outside a VPC

  - Amazon RDS supports encryption at rest for all database engines, using keys you manage using AWS Key Management Service (KMS). 

  - Yes. AWS CloudTrail is a web service that records AWS API calls for your account and delivers log files to you.

  - A database parameter group (DB Parameter Group) acts as a "container" for engine configuration values that can be applied to one or more DB Instances. 

|If You Need|Consider Using|Product Type|
|---|----|----|
|A managed relational database in the cloud that you can launch in minutes with a just a few clicks.| Amazon RDS| Relational Database|
|A fully managed MySQL compatible relational database with 5X performance and enterprise level features.| Amazon Aurora | Relational Database|
|A managed NoSQL database that offers extremely fast performance, seamless scalability and reliability| Amazon DynamoDB| NoSQL Database|
|A fast, fully managed, petabyte-scale data warehouse at less than a tenth the cost of traditional solutions.|Amazon Redshift| Data Warehouse|
|To deploy, operate, and scale in-memory cache based on Memcached or Redis in the cloud.| Amazon ElastiCache| In-Memory Cache|
|Help migrating your databases to AWS easily and inexpensively with zero downtime.| AWS Database Migration Service| Database Migration|
|To build flexible cloud-native directories for organizing hierarchies of data along multiple dimensions |Amazon Cloud Directory | Directory|


## EC2

  - After early December 2016, all newly created instances, reservations, volumes, and snapshots will be required to use the longer ID format. Need to upgrade certain SDKs and CLIs. If you interact with AWS resources via APIs, SDKs, or the AWS CLI, you might be impacted, depending on whether your software makes assumptions about the ID format when validating or persisting resource IDs

  - Reservation IDs apply to all instances, and are different from Reserved Instances.  A reservation ID has a one-to-one relationship with an instance launch request, but can be associated with more than one instance if you launch multiple instances using the same launch request

  - On windows instances, don’t use EC2 instance ID as part of computer name.

  - Instances store type root volume mostly use paravirtualization. Data lost post restart of instance.

  - EBS backed root volume instances mostly use HVM. By using Amazon EBS, data on the root device will persist independently from the lifetime of the instance. This enables you to stop and restart the instance at a subsequent time

  - Custom AMIs are stored in using EBS and S3.

  - EC2 instances used ECC Memory – error correcting code.

  - Pricing is per instance-hour consumed for each instance type. Partial instance-hours consumed are billed as full hours. Charged for "running" state only.

  - Also, charged for data transfer in and data transfer out.

  - No charge for data transfer in from internet or AWS resources in same region / availability zone/ private IP for communication etc.

  - Charge for data transfer out to internet.

  - EC2 instances are built on commodity hardware. EC2 Compute unit provides consistent computation capacity irrespective of underlying EC2 hardware.

  - Use CloudTrail to log any information about the number of API calls. It has to be enabled.

  - By default all accounts are limited to 5 Elastic IP addresses per region.

  - Elastic IP is charged when not associated with any region

  - In EC2-Classic - If you stop an instance, its Elastic IP address is disassociated, and you must re-associate the Elastic IP address when you restart the instance. In EC2-VPC - If you stop an instance, its Elastic IP address remains associated.

  - EC2 Classic – older EC2 format. EC2-VPC – newer format which has default VPC created.

  - If you created your account after 2013-12-04, it supports EC2-VPC only. If your accounts supports EC2-VPC only, AWS creates a *default VPC* for you.

  - You can create reverse DNS records for Elastic IP address by requesting AWS. Forward DNS record must exist as a pre-requisite.

  - One Availability Zone name (for example, us-east-1a) in two AWS customer accounts may relate to different physical Availability Zones.

  - Enhanced EC2 Networking - For supported Amazon EC2 instances, this feature provides higher packet per second (PPS) performance, lower inter-instance latencies, and very low network jitter.

  - If you are using an Amazon EBS volume as a root partition, you will need to set the Delete on Terminate flag to "N" if you want your Amazon EBS volume to persist outside the life of the instance.

  - While you are able to attach multiple volumes to a single instance, attaching multiple instances to one volume is not supported at this time.

  - EBS snapshots are only available through the Amazon EC2 APIs

  - Users who have permission to create volumes based on your shared snapshots will first make a copy of the snapshot into their account. Users can modify their own copies of the data, but the data on your original snapshot and any other volumes created by other users from your original snapshot will remain unmodified.

  - Amazon CloudWatch stores metrics for terminated Amazon EC2 instances or deleted Elastic Load Balancers for 2 weeks.

  - CloudWatch charge consistent for all EC2 instance types

  - If you have an Auto Scaling group with running instances and you choose to delete the Auto Scaling group, the instances will be terminated and the Auto Scaling group will be deleted.

  - The Classic Load Balancer that routes traffic based on either application or network level information, and the Application Load Balancer that routes traffic based on advanced application level information that includes the content of the request.

  - The Classic Load Balancer is ideal for simple load balancing of traffic across multiple EC2 instances, while the Application Load Balancer is ideal for applications needing advanced routing capabilities, microservices, and container-based architectures

  - Reserved instances are for a particular family type only. Use convertible instances to change the instance type during mid-term.

  - The Convertible Reserved Instance is useful for customers who can commit to using EC2 instances for a three-year term in exchange for a significant discount on their EC2 usage, are uncertain about their instance needs in the future, or want to benefit from changes in price.

  - All reservations are region specific

  - The Reserved Instance Marketplace is an online marketplace that provides AWS customers the flexibility to sell their Amazon Elastic Compute Cloud (Amazon EC2) Reserved Instances to other businesses and organizations.

  - Spot instances provide the ability for customers to purchase compute capacity with no upfront commitment, at hourly rates usually lower than the On-Demand rate.

  - Not all instance types are available on Spot

  - CloudWatch reporting 100% CPU utilization is your signal that you should consider scaling – manually or via Auto Scaling – up to a larger instance type or scale out to multiple Micro instances.

  - Compute-optimized instances are designed for applications that benefit from high compute power. These applications include high performance front-end fleets, web-servers, batch processing, distributed analytics, high performance science and engineering applications, ad serving, MMO gaming, video-encoding, and distributed analytics.

  - GPU instances work best for applications with massive parallelism, for example workloads using thousands of threads. Graphics processing is an example with huge computational requirements

  - High performance computing instances require special type of drivers – NVIDIA

  - Cluster Compute Instances combine high compute resources with a high performance networking for High Performance Compute (HPC) applications and other demanding network-bound applications. Amazon EC2 cluster placement group functionality allows users to group Cluster Compute Instances in clusters.

  - Only HVM based AMIs can be used for Cluster Compute or Cluster GPU instances

  - Amazon EC2 allows you to choose between Fixed Performance Instances (e.g. M3, C3, and R3) and Burstable Performance Instances (e.g. T2). 

  - T2 instances’ baseline performance and ability to burst are governed by CPU Credits.

  - Dense-storage instances are designed for workloads that require high sequential read and write access to very large data sets, such as Hadoop distributed computing, massively parallel processing data warehousing, and log processing applications. 

  - VM Import/Export enables customers to import Virtual Machine (VM) images in order to create Amazon EC2 instances. Customers can also export previously imported EC2 instances to create VMs

  - Standard S3 storage fees apply for VM Import and Export. OS licenses can’t be exported / imported along with the images.

  - VM Import/Export commands only available via CLI and API

  - EC2 SLA guarantees a Monthly Uptime Percentage of at least 99.95% for Amazon EC2 and Amazon EBS within a Region.

  - ( skipped info around specialized instance types)

## S3

  - S3 is Object Store, EBS is block store

  - Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 5 terabytes. The largest object that can be uploaded in a single PUT is 5 gigabytes.

  - S3 supports multipart upload for heavier objects - > 100 MB

  - S3 supports multi-Object delete to delete many objects simultaneously.

  - S3 Storage Classes - S3 Standard for general-purpose storage of frequently accessed data, Amazon S3 Standard - Infrequent Access for long-lived, but less frequently accessed data, and Amazon Glacier for long-term archive.

  - Reduced Redundancy Storage (RRS) – lower levels of Redundancy than S3. It is an Amazon S3 storage option that enables customers to **store noncritical, reproducible data*  - at lower levels of redundancy than Amazon S3’s standard storage. *[Non-critical, reproducible data – think of RRS]*

  - Amazon S3 buckets in all Regions provide read-after-write consistency for PUTS of new objects and eventual consistency for overwrite PUTS and DELETES

  - Any publicly available data in Amazon S3 can be downloaded via the BitTorrent protocol. It allows users download from Amazon and other users simultaneously.

  - By default, customers can provision up to 100 buckets per AWS account.

  - There is no Data Transfer charge for data transferred within an Amazon S3 Region via a COPY request. For inter-region transfer fees apply

  - The volume of storage billed in a month is based on the average storage used throughout the month. Usage calculated as Byte-Hours and then converted to GB-Month for final pricing.

  - Normal Amazon S3 pricing applies when accessing the service through the AWS Management Console.

  - Amazon S3 is secure by default. Only the bucket and object owners originally have access to Amazon S3 resources they create. You can use access control mechanisms such as bucket policies and Access Control Lists (ACLs) to selectively grant permissions to users and groups of users

  - S3 Access Control Mechanisms – IAM policies, bucket policies, ACLs, query string authentication [customers can create a URL to an Amazon S3 object which is only valid for a limited time]

  - You can optionally configure Amazon S3 buckets to create access log records for all requests made against it

  - You should choose **SSE-S3*  - if you prefer to have Amazon manage your keys. **SSE-C*  - enables you to leverage Amazon S3 to perform the encryption and decryption of your objects while retaining control of the keys used to encrypt objects

  - An encryption client library, such as the Amazon S3 Encryption Client, you retain control of the keys and complete the encryption.

  - Compliance with privacy laws is end user responsibility.

  - An Amazon VPC Endpoint for Amazon S3 is a logical entity within a VPC that allows connectivity only to S3.

  - For S3 data, that best practice for durability includes **secure access permissions**, **Cross-Region Replication**, **versioning*  - and a functioning, **regularly tested backup**.

  - Amazon S3 Standard and Standard - IA redundantly stores your objects on multiple devices across multiple facilities in an Amazon S3 Region

  - By default, GET requests will retrieve the most recently written version. Older versions of an overwritten or deleted object can be retrieved by specifying a version in the request.

  - Versioning offers an additional level of protection by providing a means of recovery when customers accidentally overwrite or delete objects. Only the owner of an Amazon S3 bucket can permanently delete a version

  - Versioning’s MFA Delete capability, which uses multi-factor authentication, can be used to provide an additional layer of security

  - The Standard - IA storage class is set at the object level and can exist in the same bucket as Standard, allowing you to use lifecycle policies to automatically transition objects between storage classes without any application changes.

  - You can directly PUT into Standard – IA by specifying STANDARD_IA in the x-amz-storage-class header. You can also set lifecycle policies to transition objects from Standard to Standard - IA.

  - Standard - IA is designed for larger objects and has a minimum object size of 128KB. Objects smaller than 128KB in size will incur storage charges as if the object were 128KB

  - Amazon Glacier provides **three options for access to archives, from a few minutes to several hours**.  Expedited (1-5 minutes), Standard (3-5 hours), or Bulk retrievals (5-12 hours). File size limit < 250 mb

  - Because Amazon S3 maintains the mapping between your user-defined object name and Amazon Glacier’s system-defined identifier, Amazon S3 objects that are stored using the Amazon Glacier option are only accessible through the Amazon S3 APIs or the Amazon S3 Management Console (**Objects cant be directly access via Glacier API**).

  - To retrieve Amazon S3 data stored in Amazon Glacier, **initiate a retrieval request using the Amazon S3 APIs or the Amazon S3 Management Console.*  - The retrieval request creates a temporary copy of your data in RRS while leaving the archived data intact in Amazon Glacier. You can specify the amount of time in days for which the temporary copy is stored in RRS. You can then access your temporary copy from RRS through an Amazon S3 GET request on the archived object.

  - For Amazon Glacier - Amazon S3 calculates the object size as the amount of data you stored plus an additional 32 kilobytes of Glacier data(metadata and index) plus an additional 8 KB (user-defined name and metadata)of S3 standard storage data

  - If an object archived in Amazon Glacier is deleted or overwritten within three months of being archived then there will be an early deletion fee

  - Amazon S3 event notifications can be sent in response to actions in Amazon S3 like PUTs, POSTs, COPYs, or DELETEs. Notification messages can be sent through either Amazon SNS, Amazon SQS, or directly to AWS Lambda.

  - There are no additional charges from Amazon S3 for event notifications. You pay only for use of Amazon SNS or Amazon SQS to deliver event notifications, or for the cost of running the AWS Lambda function.

  - Amazon S3 provides multiple ways to enable redirection of web content for your static websites

  - No additional cost for S3 static website hosting

  - S3 Object Tags are key-value pairs applied to S3 objects which can be created, updated or deleted at any time during the lifetime of the object.

  - Object Tags can be replicated across regions using Cross-Region Replication.

  - S3 Analytics, with storage class analysis, you can analyze storage access patterns and transition the right data to the right storage class. This new S3 Analytics feature automatically identifies infrequent access patterns to help you transition storage to Standard-IA

  - S3 Inventory provides a CSV (Comma Separated Values) flat-file output of your objects and their corresponding metadata on a daily or weekly basis for an S3 bucket or a shared prefix.

  - S3 CloudWatch Metrics are priced as custom metrics for Amazon CloudWatch

  - There is no additional cost to set up and apply lifecycle policies. A transition request is charged per object when an object becomes eligible for transition according to the lifecycle rule.

  - Cross Region Replication is an Amazon S3 feature that automatically replicates data across AWS regions. With CRR, every object uploaded to an S3 bucket is automatically replicated to a destination bucket in a different AWS region that you choose. CRR is a bucket-level configuration.

  - You pay the Amazon S3 charges for storage, requests, and inter-region data transfer for the replicated copy of data. If the source object is uploaded using the multipart upload feature, then it is replicated using the same number of parts and part size

  - Transfer Acceleration leverages Amazon CloudFront’s globally distributed AWS Edge Locations. As data arrives at an AWS Edge Location, data is routed to your Amazon S3 bucket over an optimized network path. You have to enable TA on an S3 bucket

  - Transfer Acceleration v/s Amazon CloudFront’s PUT/POST – Use TA for higher throughput. If you have objects that are smaller than 1GB or if the data set is less than 1GB in size, you should consider using Amazon CloudFront's PUT/POST

  - AWS Direct Connect is a good choice for customers with a private networking requirement or have access to AWS Direct Connect exchanges. Transfer Acceleration is best for submitting data from distributed client locations over the public Internet, or where variable network conditions make throughput poor

  - Amazon S3 dual-stack endpoints support requests to S3 buckets over IPv6 and IPv4. When you make a request to a dual-stack endpoint, the bucket URL resolves to an IPv6 or an IPv4 address.

## VPC

  - You have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways.

  - Hardware Virtual Private Network (VPN) connection between your corporate datacenter and your VPC and thus extend your own data center.

  - **Internet Gateway*  - – connect to internet for public subnet. **NAT Gateway **– connect to internet for private subnet

  - **Virtual Private Gateway**: The Amazon VPC side of a VPN connection. **Customer Gateway**: The customer side of a VPN connection.

  - **Peering Connection**: A peering connection enables you to route traffic via private IP addresses between two peered VPCs.

  - **VPC Endpoint**: Enables Amazon S3 access from within your VPC without using an Internet gateway or NAT.

  - AWS resources are automatically provisioned in a ready-to-use default VPC.

  - There are no additional charges for creating and using the VPC itself.

  - For A VPC, connectivity can be established to Both the Internet and your corporate data center (utilizing both an Internet gateway and a virtual private gateway)

  - An Internet gateway is horizontally-scaled, redundant, and highly available. It imposes no bandwidth constraints

  - Instances in Public subnet can have Public IPs or Elastic IPs and connect to the internet and receive inbound unsolicited connections too.

  - How do I connect a VPC to my corporate datacenter? – By establishing a hardware VPN connection between your existing network and Amazon VPC.

  - It is recommended using non-overlapping IP address ranges. 

  - Default VPCs are assigned a CIDR range of 172.31.0.0/16. Default subnets within a default VPC are assigned /20 netblocks within the VPC CIDR range. 

  - Amazon VPC supports VPCs between /28 (in CIDR notation) and /16 in size for IPv4

  - To change the size of a VPC you must terminate your existing VPC and create a new one.

  - Amazon reserves the first four (4) IP addresses and the last one (1) IP address of every subnet for IP networking purposes.

  - Primary private IP addresses are retained for the instance's or interface's lifetime. Secondary private IP addresses can be assigned, unassigned, or moved between interfaces or instances at any time.

  - An IP address assigned to a running instance can only be used again by another instance once that original running instance is in a "terminated" state. 

  - The number of secondary private IP addresses you can assign depends on the instance type.

  - AWS VPC does not support multicast or broadcast

  - Secure VPC via security groups (stateful) and ACLs (stateless)

  - Security groups in a VPC specify which traffic is allowed to or from an Amazon EC2 instance. Network ACLs operate at the subnet level and evaluate traffic entering and exiting a subnet. **Network ACLs can be used to set both Allow and Deny rules.*  - Network ACLs do not filter traffic between instances in the same subnet. In addition, network ACLs perform stateless filtering while security groups perform stateful filtering. 

  - Can Amazon EC2 instances within a VPC in one region communicate with Amazon EC2 instances within a VPC in another region? Yes, they can communicate using public IP addresses, NAT gateway, NAT instances, VPN connections, or Direct Connect connections.

  - Amazon EC2 instances within a VPC communicate with Amazon S3 by – VPC Endpoint for S3 and internet gateway

  - Ping (ICMP Echo Request and Echo Reply) requests to the router in your VPC is not supported. Ping between Amazon EC2 instances within VPC is supported as long as your operating system's firewalls, VPC security groups, and network ACLs permit such traffic.

  - You can use the Amazon VPC Flow Logs feature to monitor the network traffic in your VPC.

  - VPC can span Availability Zones, subnet cannot span AZs.

  - You can use AMIs in Amazon VPC that are registered within the same region as your VPC

  - An instance launched in a VPC using an Amazon EBS-backed AMI maintains the same IP address when stopped and restarted.

  - Can I have more than two network interfaces attached to my EC2 instance? – Yes, The total number of network interfaces that can be attached to an EC2 instance depends on the instance type

  - Network interfaces can only be attached to instances residing in the same Availability Zone

  - VPC Peering connections are only available between VPCs in the same region

  - You can peer VPCs belonging to different AWS accounts.

  - Peered VPCs must have non-overlapping IP ranges.

  - VPC peering connections do not require an Internet Gateway.

  - VPC peering traffic within a region is not encrypted.

  - Amazon Virtual Private Cloud (VPC) ClassicLink allows EC2 instances in the EC2-Classic platform to communicate with instances in a VPC using private IP addresses.

## SQS

  - Amazon SQS can help you build a distributed application with decoupled components, 

  - Using SQS you can build a microservice architecture and use message queues to connect your microservices.

  - **FIFO (first-in-first-out) queues*  - **preserve*  - the exact order in which messages are sent and received. If you use a FIFO queue, you don't have to place sequencing information in your messages. **Standard queues*  - provide a **loose-FIFO capability*  - that attempts to preserve the order of messages. However, because standard queues are designed to be massively scalable using a highly distributed architecture, receiving messages in the exact **order they are sent is not guaranteed**.

  - Standard queues provide at-least-once delivery, which means that each message is delivered at least once.

FIFO queues provide exactly-once processing, which means that each message is delivered once and remains available until a consumer processes it and deletes it. Duplicates are not introduced into the FIFO queue.

  - Standard queues – unlimited TPS. FIFO Queues – 300 TPS.

  - Standard queues – available in all regions. FIFO queues – US East (Ohio) and US West (Oregon)

  - Amazon SWF API actions are task-oriented. Amazon SQS API actions are message-oriented.

  - With SWF – it is a robust platform for development, message passing between tasks. With SQS this feature has to be enabled separately.

  - Use  SQS for  - Decoupling the components of an application , Configuring individual message delay, Dynamically increasing concurrency or throughput at read time, Scaling transparently

  - Amazon Kinesis Streams allows real-time processing of streaming big data and the ability to read and replay records to multiple Amazon Kinesis Applications

  - Use Kinesis streams - Routing related records to the same record processor, Allowing multiple applications to consume the same stream concurrently

  - The cost of Amazon SQS is calculated per request, plus data transfer charges for data transferred out of Amazon SQS (unless data is transferred to Amazon EC2 instances or to AWS Lambda functions within the same region).

  - Batch operations (SendMessageBatch, DeleteMessageBatch, and ChangeMessageVisibilityBatch) all cost the same as other Amazon SQS requests. By grouping messages into batches, you can reduce your Amazon SQS costs.

  - Some AWS or external services that send notifications to Amazon SQS might not be compatible with FIFO queues

  - One or more producers can send messages to a FIFO queue. Messages are stored in the order that they were successfully received by Amazon SQS.

  - Amazon SQS FIFO queues don't serve messages from the same message group to more than one consumer at a time. However, if your FIFO queue has **multiple message groups**, you can take advantage of parallel consumers, allowing Amazon SQS to **serve messages from different message groups to different consumers**.

  - Must use a FIFO dead letter queue with a FIFO queue. (Similarly, you can use only a standard dead letter queue with a standard queue.)

  - The name of a FIFO queue must end with the .fifo suffix. To determine whether a queue is FIFO, you can check whether the queue name ends with the suffix.

  - SQS common use case is a distributed, decoupled application whose multiple components and modules need to communicate with each other, but can’t do the same amount of work simultaneously.

  - You can interact with SQS with API, Console and SDK

  - Only an AWS account owner (or an AWS account that the account owner has delegated rights to) can perform operations on an Amazon SQS message queue

  - Message Identifier:	4514bcb7-9935-42ca-b2e4-47549b42c84c

MD5 of Body:	a305cfffacad586f5a30573687e93b7b

MD5 of Message Attributes:	caeec55758b361f94b3626437df44a32

  - The visibility timeout is a period of time during which Amazon SQS prevents other consuming components from receiving and processing a message. Messages are hidden from other consumers for this duration. Assuming a reader has picked up a message and is unable to process and delete it within the same visibility timeout, the message is then visible again in the queue and can be picked up by other processors.

  - The maximum visibility timeout for an Amazon SQS message is 12 hours.

  - An Amazon SQS message can contain up to 10 metadata attributes. 

  - **SQS Long Polling*  - - While the regular short polling returns immediately, even if the message queue being polled is empty, long polling doesn’t return a response until a message arrives in the message queue, or the long poll times out. No additional charge for long polling calls.

  - In almost all cases, Amazon SQS long polling is preferable to short polling. Use short polling if a single application thread is polling multiple – queues.

  - SQS message queues can receive notifications from Amazon SNS topics.

  - Deliver same message to multiple SQS Queues – by creating a SNS Topic. And then have multiple SQS queues subscribe to the topic. A message published to a SNS Topic will be delivered to all SQS queues by SNS

  - You can delete all messages in an Amazon SQS message queue using the PurgeQueue action, while retaining the queue and its attributes.

  - For security, encrypt messages before they are placed in Queue

  - Messages deleted from FIFO queues are never seen / introduced again. On rare occasions, this might happen in standard queues.

  - When you issue a DeleteMessage request on a previously-deleted message, Amazon SQS returns a success response.

  - SQS is not HIPAA compliant. Send messages to SQS via S3 which is HIPAA compliant.

  - SQS messages retained upto 14 days

  - Maximum SQS message size is 256KB. Larger messages via SDK client

  - Queue can store unlimited messages. Limit on number of inflight messages

  - Queue names have 80 character limit.

  - You cannot share SQS messages between regions

## Route 53

Q. What is the difference between a Domain and a Hosted Zone?

A domain is a general DNS concept. Domain names are easily recognizable names for numerically addressed Internet resources. For example, *amazon.com *is a domain. A hosted zone is an Amazon Route 53 concept. A hosted zone is analogous to a traditional DNS zone file; it represents a collection of records that can be managed together, belonging to a single parent domain name. All resource record sets within a hosted zone must have the hosted zone’s domain name as a suffix. For example, the *amazon.com *hosted zone may contain records named *www.amazon.com*, and *www.aws.amazon.com*, but not a record named *www.amazon.ca*. 

Q. Does Amazon Route 53 use an anycast network?

Yes. Anycast is a networking and routing technology that helps your end users’ DNS queries get answered from the optimal Route 53 location given network conditions.

Each Amazon Route 53 account is limited to a maximum of 500 hosted zones and 10,000 resource record sets per hosted zone. 

R53 supports all the well-known DNS types.  

Amazon Route 53 offers ‘Alias’ records (an Amazon Route 53-specific virtual record). Alias records are used to map resource record sets in your hosted zone to Amazon Elastic Load Balancing load balancers, Amazon CloudFront distributions, AWS Elastic Beanstalk environments, or Amazon S3 buckets that are configured as websites. Alias records work like a CNAME record in that you can map one DNS name (example.com) to another ‘target’ DNS name (elb1234.elb.amazonaws.com). They differ from a CNAME record in that they are not visible to resolvers. Resolvers only see the A record and the resulting IP address of the target record.

 Queries to Alias records that are mapped to ELB load balancers are free. These queries are listed as "Intra-AWS-DNS-Queries" on the Amazon Route 53 usage report

Amazon Route 53 Traffic Flow is an easy-to-use and cost-effective global traffic management service.

Private DNS is a Route 53 feature that lets you have authoritative DNS within your VPCs without exposing your DNS records (including the name of the resource and its IP address (es) to the Internet.

Q. Does Amazon Route 53 support wildcard entries? If so, what record types support them?

A. Yes. To make it even easier for you to configure DNS settings for your domain

Q. Will Private DNS work across AWS regions?

Yes. DNS answers will be available within every VPC that you associate with the private hosted zone. Note that you will need to ensure that the VPCs in each region have connectivity with each other in order for resources in one region to be able to reach resources in another region. 

Q. What happens if all of my endpoints are unhealthy?

Route 53 can only fail over to an endpoint that is healthy. If there are no healthy endpoints remaining in a resource record set, Route 53 will behave as if all health checks are passing.

You will be charged for the hosted zone that Route 53 creates for your domain name, as well as for the DNS queries against this hosted zone that Route 53 serves on your behalf.

Q. Can I configure DNS Failover based on internal health metrics, such as CPU load, network, or memory?

Yes. Amazon Route 53’s metric based health checks let you perform DNS failover based on any metric that is available within Amazon CloudWatch, including AWS-provided metrics and custom metrics from your own application.

Q. How can I use health checks to verify that my web server is returning the correct content?

You can use Route 53 health checks to check for the presence of a designated string in a server response by selecting the "Enable String Matching" option

# Quiz Questions – Tricky ones.

  - You can force failover of RDS Instances in Multi-AZ deployments.

  - For Microsoft SQL Server, there are two different limits -- that of the DB (10GB), and that of the DB instance server storage (300GB). A DB server instance could quite easily host several DBs, or a DB and support files such as logs, dumps, and flat file backups. Please see the AWS documentation for full details.

  - Maximum response time for a Business Level Premium Support Case is 1 hour

  - RDS Aurora stores 6 copies of data

  - Maximum backup retention policy in RDS is 35 days.

  - Amazon RDS does not currently support increasing storage on an active SQL Server Db instance.

  - A policy is a document that provides a formal statement of one or more permissions.

  - 4 levels of AWS Premium support - Basic, Developer, Business, and Enterprise

  - When creating an RDS instance, you can select the Availability Zone into which you deploy it.

  - It is possible to transfer a reserved instance from one Availability Zone to another

  - US STANDARD is a redundant term. The AWS exams still use the term so you need to be familiar with it. The questions is still valid just ignore the reference to US STANDARD and any past discrepancies that may have existed.

  - New subnets in a custom VPC can communicate with each other across Availability Zones.

  - You should reduce the input split size in the MapReduce job configuration, then adjust the number of simultaneous mapper tasks so that more tasks can be processed at once

  - For all new AWS accounts, there is a soft limit of 20 EC2 instances per region

  - Memory usage is a custom metric in CloudWatch. CPU, Disk read operations and network in are default

  - By definition, a public subnet within a VPC is one that has at least one route in its routing table that uses an Internet Gateway (IGW).

# Technical Concepts

1. Anycast v/s Multicast v/s Broadcast v/s Unicast

[http://serverfault.com/questions/279482/what-is-the-difference-between-unicast-anycast-broadcast-and-multicast-traffic](http://serverfault.com/questions/279482/what-is-the-difference-between-unicast-anycast-broadcast-and-multicast-traffic)

**Multicast** is like a broadcast that can cross subnets, but unlike broadcast does not touch all nodes. Nodes have to subscribe to a multicast group to receive information.

To use **Anycast** you advertise the same network in multiple spots of the Internet, and rely on shortest-path calculations to funnel clients to your multiple locations. As far the network nodes themselves are concerned, they're using a **unicast** connection to talk to your anycasted nodes. Anycast is announcing the same network in different *parts* of the network, in order to decrease the network hops needed to get to that network.

2. Shards

A **database shard** is a horizontal partition of data in a database or search engine. Each individual partition is referred to as a **shard** or **database shard**. Each shard is held on a separate database server instance, to spread load.

3. **PV v/s HVM**

HVM AMIs are presented with a fully virtualized set of hardware and boot by executing the master boot record of the root block device of your image. This virtualization type provides the ability to run an operating system directly on top of a virtual machine without any modification, as if it were run on the bare-metal hardware. The Amazon EC2 host system emulates some or all of the underlying hardware that is presented to the guest

Paravirtual guests can run on host hardware that does not have explicit support for virtualization, but they cannot take advantage of special hardware extensions such as enhanced networking or GPU processing. 

For the best performance, we recommend that you use current generation instance types and HVM AMIs when you launch your instances
