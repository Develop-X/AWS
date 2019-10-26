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


### Design Resilient Architecture

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



