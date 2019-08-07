# Object Storage & CDN – S3, Glacier and CloudFront

## S3 101

### S3 Simple Storage Service - Object Storage Classes

  - **S3-Standard** - Durability of 99.999999999% and availability of 99.99%.

  - **S3-IA** (Infrequently Accessed) - Durability of 99.999999999% and availability of 99.9%.

  - **S3-RRS** (Reduced Redundancy Storage) - Durability and availability of 99.99%. Use when you don’t care if data is occasionally lost and can easily be re-created.
  
  - **Glacier** - For archival only. Takes 3 - 5 hours to restore files. Durability of 99.999999999%.
  
  ??? Diff types?

### S3 Buckets

  - **S3 Namespace is global/universal** That means your bucket names must be unique. Region independent.

  - **A bucket name in any region should only contain lower case characters. It has to be DNS Compliant**

  - Object versioning - Different versions of the same object in a bucket.
  
  - Not suitable to install operating system or DB
  
  - Successful uploads will return a 200 status code

  - Only **Static website** can be hosted. Auto scaling, Load Balancing etc. all managed automatically.

  - You can **tag buckets (or any AWS resoruce) to track costs**. Tags consist of keys and (optional) value pairs.

  - **Lifecycle management of objects can be set**. e.g. move to Glacier after 30 days

  - **Every bucket created, object uploaded is private by default**.

  - Object Permissions – Access to Object ACLs

  - Prefix in bucket is a folder in the bucket.

  - Minimum file size that I can store on S3 bucket is 0 byte.

  - Max 100 S3 buckets per account by default.

  - Individual Amazon S3 objects can range in size from a minimum of **0 bytes** to a maximum of **5 terabytes**. The largest object that can be uploaded in a single PUT is **5 gigabytes**. For objects larger than **100 megabytes**, customers should consider using the Multipart Upload capability.

### S3 Versioning

  - **Once versioning is turned on it cannot be removed. It can only be suspended**. To remove versioning, you have to create a new bucket and transfer all files from old to new

  - **For newer version of an object, you still have to set permissions to allow access. It is disabled by default even if previous version is public.**

  - All versions of the file add up to the storage. Hence for larger objects, ensure that there is some lifecycle versioning in place.

  - **Version deleted cannot be restored.**

  - **Object deleted can be restored** – Delete the Delete marker.

  - Versioning is a good backup tool.

  - **For versioning. MFA can be setup for Delete capability for object / bucket – Complicated setup.**

## Cross Region Replication

  - To allow for cross region replication, the **both source and target buckets must have versioning enabled**.

  - When cross region replication is enabled, all existing objects in the bucket are not copied over to replica site. **Only Updates to existing objects and newer objects are replicated over**. All previous versions of the updated objects are replicated.

  - Permissions are also replicated from one bucket to another.

  - **Transitive replications do not work**. E.g. if you setup bucket C to replicate content from bucket B which replicates content from bucket A – Changes made to bucket A will not get propagated to C. You will need to manually upload content to bucket B to trigger replication to C.

  - **Delete markers** are replicated.
  - A delete marker is a placeholder (marker) for a versioned object that was named in a simple DELETE request. Because the object was in a versioning-enabled bucket, the object was not deleted. The delete marker, however, makes Amazon S3 behave as if it had been deleted.

  - **If you delete source replication bucket objects, they are deleted from replica target bucket too. When you delete a Delete marker or version from source, that action is not replicated.**

## Lifecycle Management

  - Objects stored in **Glacier incur minimum 90 day storage cost**.

  - Lifecycle management can be used in conjunction with versioning

  - **Objects can be transitioned to S3-IA after 30 days** and to Glacier class storage - 30 days IA.

  - You can also permanently delete objects.

## CloudFront CDN Overview

### Important terms

  - **CDN content delivery network** – collection of distributed servers where the content is served to users based on the user’s location and the location of content origin.

  - **Edge location** – location where content will be cached. Different from AWS Region / AZ

  - **Origin** – Can be S3 Bucket, an EC2 Instance, an Elastic Load Balancer or Route53

  - **Distribution** – is the name given to CDN collection which consists of Edge locations.

  - **Web Distribution** – Typically used for websites & web content only.

  - **RTMP Real-Time Messaging Protocol**– Used for Media Streaming. Adobe Flash media server’s protocol – video streaming.

  - First request is slow as it comes from source origin. Subsequent requests improve speed as they are cached in nearest edge location and routed there until TTL (Time To Live) expires.

  - CloudFront also works with non AWS origin which can be on premise as well. .

  - Edge locations are for read and write as well. Objects PUT on edge location are sent to origin

  - Objects are cached for life of TTL. **TTL can be set for 0 seconds to 365 days. Default TTL is 24 hours**. If objects change more frequently update the TTL

  - You can clear cached objects, with charges.

  - Origin domain name – either S3 bucket, ELB or on premise domain

### CloudFront Security.

  - **You can force them to use CDN URL instead of S3 DNS**

  - To restrict bucket access you need to create origin access identity. And allow this user read permission S3 bucket content –

  - Set video protocol policy – redirect http to https, http or https

  - **Allows various HTTP methods – GET, PUT, POST, PATCH, DELETE, and HEAD.**

  - **Restrict viewer access for S3 and CDN using pre-Signed URLs or Signed cookies. E.g. You can view video only using that URL**

  - Using Web Application Firewalls to prevent SQL injection, CSS attacks

  - **For https access, you can either use default CloudFront certificate or own certificate can be imported via ACM.(AWS Certificate Manager )**

  - **Provisioning / Updating CloudFront distribution takes up to 15-20 minutes.**

  - **Geo-restriction can be setup. Either whitelist or blacklist – countries from where content can be accessed.**

  - **Invalidating removes objects from CloudFront. It can be forced to remove from Cache – obviously costs.**

  - **You can force users to get content via CloudFront after removing read access to S3 bucket.**

  - You can also upload content to CloudFront.

## S3 Security & Encryption

### Security

  - By default all newly created buckets are Private

  - Control Access to buckets using

      - **Bucket Policies – bucket wide.**

      - **Access Control Lists (ACL) – up to individual objects.**

  - S3 buckets can log all access requests to another S3 bucket even another AWS account.

### Encryption

  - **In Transit**

**Secured using SSL/TLS** - For securing data in transit, S3 uses HTTPS by default. This means that SSL/TLS (Secure Sockets Layer/Transport Layer Security) encryption is used both for transferring data and also for sending S3 service management requests issued through the AWS Management Console or S3 APIs.

  - **Data at rest** two ways:

1. **Server Side**

    1. S3 Managed Keys – SSE – S3

    2. AWS KMS(Key Management Service) Managed Keys – SSE – KMS – Envelop Key. Provides audit trail
    CMK (AWS managed Customer Master Key)

    3. SSE using customer provided keys. Key Management is responsibility of user. SSE-C
    
Amazon S3 Server Side Encryption handles all encryption, decryption, and key management in a totally transparent fashion. When you PUT an object and request encryption (in an HTTP header supplied as part of the PUT), we generate a unique key, encrypt your data with the key, and then encrypt the key with a master key

2. **Client Side**

Encrypt data at client side and then upload to S3.

## Storage Gateway

  - It is a service which **connects an on-premises software appliance (virtual) with cloud based storage** to provide seamless and secure connectivity between the two. Either via internet or Direct connect.
  
  - Your gateway uploads data from the upload buffer over an encrypted Secure Sockets Layer (SSL) connection to the AWS Storage Gateway service running in the AWS Cloud. The service then stores the data encrypted in Amazon S3. You can take incremental backups, called snapshots, of your storage volumes.

  - It can also provide connectivity from EC2 instance in VPC to S3 via Storage Gateway in same VPC

  - **The virtual appliance will asynchronously replicate information up to S3 or Glacier**

  - **Can be downloaded as a VM – VMware ESXi / Hyper-V.**

  - 4 Types of Storage Gateways. / 5 types ( S3 / EFS / EBS / Glacier / Snowball)

 1.**File Gateway (NFS)** – Just store files in S3 – Word, Pictures, PDFs, and no OS. ( Saves a lot of money)
  -Files are stored as objects in S3 buckets and accessed over NFS (Network File System) mount point
  -File attributes as stored as S3 object metadata.
  -Once transferred to S3, standard S3 features apply to all files.

 2.**Volumes Gateway (iSCSI)** – (EYE-skuz-ee - Internet Small Computer Systems Interface) uses block based storage – virtual hard disk, operating system.
  - Stored Volumes – Store entire data set copy on-prem. Data async backed up to AWS S3.
  - Cached Volumes – Stored only recently accessed data on-prem. Rest on AWS S3

  Volume gateway interface presents applications with disk volumes using iSCSI protocol. They take virtual hard disks on premise and back them up to virtual hard disks on AWS. Data written to these volumes can be asynchronously backed up as point in time snapshots of volumes and stored in cloud as EBS snapshots.

 3.**Gateway Virtual Tape Library (VTL)** – Backup and Archiving solution. Create tapes and send to S3. You can use existing backup applications like NetBackup, Backup Exec, and Veam etc.

## Snowball

**Next version of Import / Export Gateway**

You could accelerate moving large amounts of data into and out of AWS using portable storage devices for transport. Ship the storage device – no need to transfer over the internet.  Problem arose with different types of disks

### Snowball Standard
  - Bigger than briefcase sized storage devices
  - **Petabyte scale data transport** solution used to transfer data in/out of AWS
  - **Cost is 1/5th as compared to transfer via high speed internet.**
  - **80TB snowball available.**
  - Multiple layers of security to protect data. Tamper resistant enclosure, 256-bit encryption
  - Once data is transferred, AWS performs software erasure of Snowball appliance.


### Snowball Edge
  - **100 TB data transfer device which has onboard storage and compute capabilities.**
  - Move large amounts of data in and out of AWS, as a temporary storage tier for large local datasets.
  - **You can run Lambda functions.**
  - Devices connect to existing applications and infrastructure using standard storage interfaces.
  - Snowball Edges can be clustered together to process your data on premise


### Snowmobile
  - Massive 45 foot long ruggedized shipping container, pulled by a truck.
  - **Petabyte or Exabyte of data that has to be transferred to AWS. 100 PB per snowmobile.**
  - You can use it for data center migration.

**Using snowball – Import / Export S3. If using Glacier first need to import into S3 and then into Snowball.**

## S3 Transfer Acceleration

It utilizes the CloudFront Edge Network to accelerate uploads to S3. Instead of uploading directly to S3, you can **use a distinct URL to upload directly to an edge location which will then transfer to S3 using Amazon’s backbone network.**

The farther you are from S3 bucket region the higher is the improvement you can observe using S3 Transfer Acceleration. High cost for usage than standard S3 transfer rates.
