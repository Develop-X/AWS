## Important links to review
Review Exam [Blueprint](http://awstrainingandcertification.s3.amazonaws.com/production/AWS_certified_solutions_architect_associate_blueprint.pdf)

AWS [Cheat Sheets](https://tutorialsdojo.com/aws-cheat-sheets/)


## Tiers

 - Practitioner - Certified Cloud Practioner
 - Assosciate - Certified Solutions Architect Assosciate | Certified Developer Assosciate | Certified Sysops administrator assosciate
 - Professional - Certified Solutions Architect Professional | Devops Professional
 - Speciality - Big Data | Machine Learning | Security | Advanced Networking

## Exam Blueprint

The table below lists the domains measured by this examination and the extent to which they are represented

|Domain | % of Examination|
|------------- |:-------------:|
|1.0 Designing highly available, cost efficient, fault tolerant, scalable systems |60% |
|2.0 Implementation/Deployment |10% |
|3.0 Data Security| 20% |
|4.0 Troubleshooting |10% |
|**Total**|100%|

The exam is approximately 60 questions in 80 minutes. Pass marks not advertised but generally > 70%

**CROPS - Cost Optimized | Resilient | Operational Excellent | Performant | Secure |

```Domain 1```
## Design Resilient Architecture 34%
```Domain 2```
## Define Performant Architecture 24%
```Domain 3```
## Specify Secure applications and architecture 26%
```Domain 4```
## Design Cost Optimized architectures 10%
```Domain 5```
## Define Operational Excellent architectures 6%

- 65 questions 130 minutes


## Design Resilient Architecture

-  **Choose resilient/reliable storage** ```event of disaster you dont loose data or state```
- **Determine how to design decoupling mechanism using AWS services** ``` If one tier is failed others arent impacted because they are decoupled```
- **Determine how to design multi tier architecture** ```naturally decoupled, each tier scales independently```
- **Determine how to design high availability / fault tolerant systems.**

#### EC2 Instance Store
- **Ephemeral Volumes** ```( are lost when terminates/stops)```
- Only certain EC2 instances have instance stores
- Fixed Capacity (size is fixed)
- Disk type and capacity depends on EC2 instance type (SSD or HDD depends on instance type and so is capacity)
- Application level durability
- **Used for caching or storing other temporary data for fast access that can be replicated else where**

#### EBS (Elastic Block Storage)
- contrasts to EC2 instance store, this is attachable storage connects to 1 EC2 instance at a time.- 
- supports IOPS
- Indepndent lifecycle than EC2 instance (persist beyond lifetime of EC2 instance (advantage over EC2))
- attach mutiple EBS volumes to EC2 instance, however only one EC2 instance to EBS.
- multiple volumes attached can use RAID or striping to achieve higher throughput.
- Multiple volumes striped to create large volumes
- Encryption
- Snapshot

##### Types of EBS
- SSD (much better IOPS) (Good for random access)
- General purpose SSD (cheaper version)
- Provisioned IOPS SSD (better perf higher price)
- HDD (Better throughput , lower IOPS) (Good for sequential access) (cheaper)
- Throughput Optimized HDD (more expensive with better spes)
- Cold HDD 

#### EFS (Elastic File System)
- Mounting it as a disk similar to EBS
- EFS gives you shared storage, multiple EC2 instances can accsesss same storage
- Petabyte scale storage
- Capacity is elastics
- supports NFS4.0 and 4.1 , compatible with Linux based AMI, not supported by windows.

1. Create and EFS Volume
2. Create mount points in a particular VPC
3. The EFS volume can only attach a single VPC at a time.
4. Withing the VPC there are mount targets that EC2 connects to.

#### S3
- For object storage the primary option is S3
- S3 is implemented as distributed system
- Consistency Model - Strongly or Eventually?
- S3 gives you strong consistency for NO object, eventual consistency for updates.
- S3 gives you **storage classes**
- S3 Standard and S3 Standard IA(Infrequent access)
- S3 Standard is cheaper for access = uploads and downloads, S3 IA is expensive for access, cheaper for storage.
- Encryption for server side
- SSE-S3 is where s3 managed master key is used to encrypt files on server side.
- SSE-KMS is where KMS managed master keys are used to encrypt files on server side.
- SSE-C s where customer provided master keys are used to encrypt files on server side.
- S3 uses https
- Allows versioning on a bucket
- Control access through IAM, bucket policies, user policies, ACL (access control lists)
- S3 supports multi-part uploads
- Internet accessible API, unlimited capacity and reigon scoped

#### Amazon Glacier
- Solution for data backup and archive storage, eg financial statements for cold storage
- archives correspond to files and vaults which are collection of archives
- 3 Retrievals types - **Expedited, Standard and Bulk**
- Bulk is cheapest and can take upto 12 hours
- Expedited expensive, takes upto 5 mins
- Glacier encrypts data by default.
- Have lifecycle policies on s3 , which take auto backup after a period of time.
- Has reigonal availability.

#### De-coupling of services
- If server goes down other parts work properly
- e.g. Using an SQS you can decouple the services so they are queues
- Instead of using a queue we can also use a load balancer for decoupling
- Loadbalancer is useful when the backend service retuns a response, if there is no response required queue can be used instead.
- Elastic IP address is a way of decoupling servers , when a service goes down. (It is a static ip address that can be moved around)

#### High Availability v/s Fault Tolerant
- Fault Tolerance is a higher bar
- Fault Tolerance means user does not see any performance degradadtion.

#### AWS Cloudformation
- Create a large dployment with many s3, EC2, dynamodb, etc.. and make multiple copies
- Cloud formation that lets you describe your infra as JSON templates, and converts them to infrastructure and call them stack.
- Also promotes resilience, easily relaunch you application from nothing.
- Cloud Formation is like your system DNA
- AMI IDs differ across reigons
- Use mappings to specify base AMI since AMI ids are different in each riegon

#### AWS Lambda
- Provide stateless code , AWS spins up containers on demand whenever you invoke it. (responds to event or a time based interval)
- A great way to increase scalability and resilience is using Lambda
- Lambda does not allow SSH access
- Lambda logs are shown up in Cloudwatch logs
- RTO (Recovery Time Objective) - How long it takes for the sytem to recover
- RPO (Recovery Point in Object) - Loose data for that period of time. How much data was lost?

### Tips (Axioms)
- Single AZ will never be the right answer
- Using managed AWS services should always be preferred
- Fault Tolerant and High availability are not teh same thing
- Expect everything will fail at sometime and design systems accordingly

## Define Performant Architecture 

### Choose performant storage and databases
- EBS represents block storage , you cam mount EBS volumes as disks on your EC2 instance.
- SSD are more expensive , perform better for IOPS / random access
  - Provisioned IOPS is better from perf
- HDD are cheaper and perform better for sequential read/writes for database
  - Throughput Optimized are better from perf
- Offload all static content to S3 to dramatically improve your web server performance
  - Create a bucket in one of the reigons
  - Bucket name becomes the subdomain of the http url
  - Then you can upload any number of objects 
  - **Virtual hosted style url** bucket as part of the domain name
  - **Path url** bucket as the first style of the path
  - Buckets are always tied to a reigon, and are globally unique (noone else can have that name in any reigon)
  - full path after the bucket name is called the key
  - Pricing of bucket is based on 3 things - storage in gb/month, transfer out of reigon, API requests
  - Transfer into s3 and Transfer out of s3 to Cloudfront or the same reigon is free
  - Storage classes in s3 , s3 Standard and s3standardIA
  - cheaper storage for IA and has a 30 day storage minimum
  - s3 lifecycle policies delete or move your object based on age. cold data moved to IA
  - s3 does not replicate data across reigons, its a reigon scoped service. It replicats across AZs
  - Data from EBS is automatically replicated within an AZ
  
#### Design performant storage on databases  
 - Options 
   - Relational dabase using RDS
   - Managed nosql service using DynamoDB
   - Datawarehouse using Redshift, useful if you have analytical queries instead of transactional queries.
 - When to use RDS?
   - Managed relational database
   - You can choose from mysql, postgres, mariadb, aurora , sqlserver and oracle.
   - joins or other complex transactions or complex queries
   - a medium to hig query write/rate , lower than dynamodb
   - dont use for scaling/auto sharding
   - RDS master databse can be scaled by using bigger instance or using
   - Read replicas - offload your read request to read replicas. for  mysql, postgres, mariadb, aurora
 - DynamoDB
   - managed nosql db as a persistent datastore
   - auto scaling and automatically shard your data and split it across multiple servers
   - only specify throughput in rcu and wcu , read capacity unit is 1 read/sec for upto 4kb. write capacity unit for an item upto 1kb.
   - one strongly consistent read pe second.
   - you can get two eventually consistent read per second.
   - limitless storage by scaling horizontally, adding more servers
   - durability in both rds and dynamodb
   - customize the database us dynamodb

### Apply caching and improve performance
- low hanging fruit to improve performance
- Cache data at different levels
  - at a web level using a CDN such as cloudfront (will cache static content close to user) delvered from cloudfront edge location close to the user
  - If edge location does not have data gets it from cache
  - Caching at application and the databse level, you can elastic cache to cache what you would otherwise fetch from database.
- Elastic cache gives you two types pf services
  - memcached - is simpler and easier to setup, multithreading, easy horizontal scaling with auto discovery
  - redis - more sophesticated , more than a key value pair, support for specific data structures, persistence and atomic operations , cluster and sharded clusters
  
### Design solutions for elasticity and scalability
- **CloudFront** - speeding up content over the internet, is used for static and dynamic content. for ex serve content from web server with ttl as 0
- whats the benefit of using dynamic content on cloudfront ? not caching , request and response ride over AWS backbone instead of public internet.
- You can set up origins as S3 for static content.
- For dymanic content you can use EC2 , ELB or http server
- supports SSL
- Integrates with AWS shield , protects you from DDOS attacks. 
- Integrates with WAF (Web application firewall) which used for filtering requests based on type.
- **Vertical Scaling** when you replace a smaller instance with larger one,  also called scaling up and scaling down
- **Horizontal scaling** when you want to add more instances , also called scaling in and scaling out
- Use autoscaling for horizontal scaling , launch and terminate instances across AZs. 
- It can also automatically register instances with load balancers.
- Monitor instances using Cloudwatch, cpu utilization for example, we can set cloudwatch alarms. 
- Cloudwatch alarms are intercepted by auto scaling.
- The AS policy determines how many instances to launch and what kind of instenaces.
- Autoscaling needs uses launch configuration to launch a fully configured instance which has the AMI ID, Instance type, Key pair, user data etc..
- **Autoscaling** 
  - launch configuration specifies EC2 instance size, AMI name and other details
  - Auto scaling group specifies min and max instances, also desired instance (current setting), point it to a Load balancer and check health.
  - Auto scaling policy specifies how much to scale in and scale out.
  - attach multiple auto scaling policies to a auto scaling group.
- Auto scaling usescloudwatch to determine when to scale in and out.
- Cloudwatch can monitor metrics such as CPU utilization, netwrork metricsand queue size
- Cloudwatch has a feature called cloudwatch logs , which picks logs from EC2/Lambda or cloudtrail.
- You can use the logs for metrics.
- Provides default metrics for most services, also define custom metrics.
- Loadbalancer is used to distribute traffic across instances.
- Schedule to scale an instance so we can avoid the latency for scaling in or out.
- If an application optimally runs on 9 instances and must have 6 instances running instances minimally accepted performance, a desired capacity of 9 instances across 3 AZs is required. 

### Tips (Axioms)
- If data is unstructured use s3 as the storage solution.
- Use caching to strategically improve perrformance
- Know when and why to use ASG
- Choose the instance and the database type that make the most sense for workload and perf need.

## Specify Secure Applications and Architecture

### Best practices
- Determine how to secure application tiers
- Determine how to secure data
- Defining the networking infra for single VPC application 

#### Shared responsibility model
- Draws a line in your stack, below the line AWS is responsible and above the line the customer is 
- the principle of least privilige

#### AWS IAM
- Secure your resources using IAM
- lets you create users, groups and roles
- attach policies to these users , groups or roles.
- Integrate IAM with AD using Federation and AWS directory service using SAML federation.

#### Identities
- Exist in these forms: 
  - IAM users - within account
  - Roles - temporary identities assigned to users
  - Federation - use AD identities
  - Web Identity Federation - assign roles to users who have open id providers using (STS)Security Token Service
  
### Amazon VPC
- Virtual Private Cloud
- organize VPC into subnets , which are subnetworks of private IP addresses
- Within our VPC we use subnet groups and ACLs to decide who can talk to whom
- We create Internet gateways, NAT gateways , Virtual private gateways for data to flow in and out of our VPC
- We determine connectivity using Routes

#### How to use Subnets
- **Public Subnets** - to support inbound and outbound access to the public internet, route tables should include an entry to an internet gateway
- **Private Subnet** - donot have an entry to an internet gateway, not directly accessible to public internet, outbound access they use a NAT instance or a NAT gateway. For inbound access they use a jump box or a bastion host.
