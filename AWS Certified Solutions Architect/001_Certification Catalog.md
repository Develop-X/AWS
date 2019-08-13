## Important Links
- [Overview](https://aws.amazon.com/certification/certified-solutions-architect-associate/)
- [AWS_Cloud_Best_Practices](https://d1.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf)
- [Exam Blueprint latest](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS_Certified_Solutions_Architect_Associate-Exam_Guide_EN_1.8.pdf)
- [AWS Whitepapers](https://aws.amazon.com/whitepapers/?whitepapers-main.sort-by=item.additionalFields.sortDate&whitepapers-main.sort-order=desc)
- [Exam Blueprint](http://awstrainingandcertification.s3.amazonaws.com/production/AWS_certified_solutions_architect_associate_blueprint.pdf)
- [AWS Cheat Sheets](https://tutorialsdojo.com/aws-cheat-sheets/)
- [A History of Amazon Web Services](https://www.awsgeek.com/pages/AWS-History/)
- [EBS Volume Types](https://user-images.githubusercontent.com/8856857/62581104-803fc900-b8eb-11e9-9140-30ee4e6dc667.png)
- [EC2 Instance Types](https://user-images.githubusercontent.com/8856857/62579559-6dc39080-b8e7-11e9-98be-3b15e4ed1626.jpg)
- [EBS backed vs Instance store](https://user-images.githubusercontent.com/8856857/62652102-e6852400-b99d-11e9-93e3-b14ef207358f.jpg)
- [S3-EFS-EBS](https://user-images.githubusercontent.com/8856857/62652854-a6bf3c00-b99f-11e9-8214-67ddfa646545.png)
- [AWS_Database_Use_Cases](https://user-images.githubusercontent.com/8856857/62659707-6f588b80-b9af-11e9-826c-448ac6f8fd9b.png)
- [Database_Types](https://user-images.githubusercontent.com/8856857/62659991-366ce680-b9b0-11e9-98be-c36f0573ed2d.png)
- [VPC-Diagram](https://user-images.githubusercontent.com/8856857/62901631-a5778000-bda0-11e9-8563-305d02d0cf4d.jpg)
- [NAT Instance v/s NAT Gateway](https://user-images.githubusercontent.com/8856857/62902311-9396dc80-bda2-11e9-9934-b6fa181d378d.png)

## Blogs
- [AWS Certification Catalog](http://jayendrapatil.com/)

## Courses
- [Udemy](https://www.udemy.com/aws-certified-solutions-architect-associate/)

### Questions
- [AWS_Certified_Solutions_Architect_Associate_Sample_Questions](https://d1.awsstatic.com/training-and-certification/docs/AWS_Certified_Solutions_Architect_Associate_Sample_Questions.pdf)
- [FAQs](https://aws.amazon.com/faqs/)

<h2>Key Points to pass the Exam:</h2>
<h3>Demonstrate ability to architect the appropriate level of availability based on stakeholder requirements</h3>

1. Stakeholder requirements is key phrase here – look at what the requirements are first before deciding the best way to architect the solution
2. What is availability? Basically up time. Does the customer need 99.99% up time or less? Which products may need to be used to meet this requirement?
3. Look at products which are single AZ, multi AZ and multi region. It may be the case that a couple of instances in a single AZ will suffice if cost is a factor
4. CloudWatch can be used to perform EC2 or auto scaling actions when status checks fail or metrics are exceeded (alarms, etc)

<h3>Demonstrate ability to implement DR for systems based on RPO and RTO</h3>

1. What is DR? It is the recovery of systems, services and applications after an unplanned period of downtime.
2. What is RPO? Recovery Point Objective. At which point in time do we need to get back to when DR processes are invoked? 3. 3. This would come from a customer requirement – when systems are recovered, data is consistent from 30 minutes prior to the outage, or 1 hour, or 4 hours etc. What is acceptable to the stakeholder?
4. What is RTO? Recovery Time Objective. How quickly must systems and services be recovered after invoking DR processes? It may be that all critical systems must be back online within a maximum of four hours.
5. RTO and RPO are often paired together to provide an SLA to end users as to when services will be fully restored and how much data may be lost. For example, an RTO of 2 hours and an RPO of 15 minutes would mean all systems would be recovered in two hours or less and consistent to within 15 minutes of the failure.
6. How can low RTO be achieved? This can be done by using elastic scaling, for example or using monitoring scripts to power up new instances using the AWS API. You may also use multi AZ services such as EBS and RDS to provide additional resilience
7. How can low RPO be achieved? This can be done by using application aware and consistent backup tools, usually native ones such as VSS aware ones from Microsoft or RMAN for Oracle, for example. Databases and real time systems may need to be acquiesced to obtain a crash consistent backup. Standard snapshot tools may not provide this. RMAN can backup to S3 or use point in time snapshots using RDS. RMAN is supported on EC2. Use data dump to move large databases.
8. AWS has multi AZ, multi region and services like S3 which has 11 nines of durability with cross region replication
9. Glacier – long term archive storage. Cheap but not appropriate for fast recovery (several hours retrieval SLA)
19. Storage Gateway is a software appliance that sits on premises that can operate in three modes – gateway cached (hot data kept locally but most data stored in S3), gateway stored (all data kept locally but also replicated to S3) and VTL-Tape Library (virtual disk tapes stored in S3, virtual tape shelf stored in Glacier)
11. You should use gateway cached when the requirement is for low cost primary storage with hot data stored locally
12. Gateway stored keeps all data locally but takes asynchronous snapshots to S3
13. Gateway cached volumes can store 32TB of data, 32 volumes are supported (32 x 32, 1PB)
14. Gateway stored volumes are 16TB in size, 12 volumes are supported (16 x 12, 192TB)
15. Virtual tape library supports 1500 virtual tapes in S3 (150 TB total)
16. Virtual tape shelf is unlimited tapes (uses Glacier)
17. Storage Gateway can be on premises or EC2. Can also schedule snapshots, supports Direct Connect and also bandwidth throttling.
18. Storage Gateway supports ESXi or Hyper-V, 7.5GB RAM, 75GB storage, 4 or 8 vCPU for installation. To use the Marketplace appliance, you must choose xlarge instance or bigger and m3, i2, c3, c4, r3, d2, or m4 instance types
19. Gateway cached requires a separate volume as a buffer upload area and caching area
20. Gateway stored requires enough space to hold your full data set and also an upload buffer
VTL also requires an upload buffer and cache area
21. Ports required for Storage Gateway include 443 (HTTPS) to AWS, port 80 for initial activation only, port 3260 for iSCSI internally and port 53 for DNS (internal)
22. Gateway stored snapshots are stored in S3 and can be used to recover data quickly. EBS snapshots can also be used to create a volume to attach to new EC2 instances
23. Can also use gateway snapshots to create a new volume on the gateway itself
24. Snapshots can also be used to migrate cached volumes into stored volumes, stored volumes into cached volumes and also snapshot a volume to create a new EBS volume to attach to an instance
25. Use System Resource Check from the appliance menu to ensure the appliance has enough virtual resources to run (RAM, vCPU, etc.)
26. VTL virtual tape retrieval is instantaneous, whereas Tape Shelf (Glacier) can take up to 24 hours
27. VTL supports Backup Exec 2012-15, Veeam 7 and 8, NetBackup 7, System Center Data Protection 2012, Dell NetVault 10
28. Snapshots can either be scheduled or done ad hoc
29. Writes to S3 get throttled as the write buffer gets close to capacity – you can monitor this with CloudWatch
30. EBS – Elastic Block Store – block based storage replicated across hosts in a single AZ in a region
31. Direct Connect – connection directly into AWS’s data centre via a trusted third party. This can be backed up with standby Direct Connect links or even software VPN
32. Route53 also has 100% uptime SLA, Elastic Load Balancing and VPC can also provide a level of resilience if required
32. DynamoDB has three copies per region and also can perform multi-region replication
33. RDS also supports multi-AZ deployments and read only replicas of data. 5 read only replicas for MySQL, MariaDB and PostGres, 15 for Aurora
34. There are four DR models in the AWS white paper:
 * Backup and restore (cheap but slow RPO and RTO, use S3 for quick restores and AWS Import/Export for large datasets)
 * Pilot Light (minimal replication of the live environment, like the pilot light in a gas heater, it’s used to bring services up with the smallest footprint running in DR. AMIs ready but powered off, brought up manually or by autoscaling
 * Data must be replicated to DR from the primary site for failover)
 * Warm Standby (again a smaller replication of the live environment but with some services always running to facilitate a quicker failover. It can also be the full complement of servers but running on smaller instances than live. Horizontal scaling is preferred to add more instances to a load balancer)
 * Multi-site (active/active configuration where DNS sends traffic to both sites simultaneously. Auto scaling can also add instances for load where required. DNS weighting can be used to route traffic accordingly). DNS weighting is done as a percentage, so if two records have weightings of 10, then the overall is 20 and the percentage is 50% chance of either being used, this is round robin. Weights of 10 and 40 would mean a total of weight 50, with 1 in 5 chance of weight 10 DNS record being used
35. Import/Export can import data sets into S3, EBS or Glacier. You can only export from S3
36. Import/Export makes sense for large datasets that cannot be moved or copied into AWS over the internet in an efficient manner (time, cost, etc)
37. AWS will export data back to you encrypted with TrueCrypt
38. AWS will wipe devices after import if specified
39. If exporting from an S3 bucket with versioning enabled, only the most recent version is exported
40. Encryption for imports is optional, mandatory for exports
41. Some services have automated backup:
 * RDS
 * Redshift
 * Elasticache (Redis only)
42. EC2 does not have automated backup. You can use either EBS snapshots or create an AMI Image from a running or stopped instance. The latter option is especially useful if you have an instance storage on the host which is ephemeral and will get deleted when the instance is stopped (Bundle Instance). You can “copy” the host storage for the instance by creating an AMI, which can then be copied to another region
43. To restore a file on a server for example, take regular snapshots of the EBS volume, create a volume from the snapshot, mount the volume to the instance, browse and recover the files as necessary
44. MySQL requires InnoDB for automated backups, if you delete an instance then all automated backups are deleted, manual DB snapshots stored in S3 are not deleted
45. All backups are stored in S3
When you do an RDS restore, you can change the engine type (SQL Standard to Enterprise, for example), assuming you have enough storage space.
46. Elasticache automated backups snapshot the whole cluster, so there will be performance degradation whilst this takes place. Backups are stored on S3.
46. Redshift backups are stored on S3 and have a 1 day retention period by default and only backs up delta changes to keep storage consumption to a minimum
47. EC2 snapshots are stored in S3 and are incremental and each snapshot still contains the base snapshot data. You are only charged for the incremental snapshot storage

<h3>Determine appropriate use of multi-Availability Zones vs. multi-Region architectures</h3>

1. Multi-AZ services examples are S3, RDS, DynamoDB. Using multi-AZ can mitigate against the loss of up to two AZs (data centres, assuming there are three. Some regions only have two). This can provide a good balance between cost, complexity and reliability
2. Multi-region services can mitigate failures in AZs or individual regions, but may cost more and introduce more infrastructure and complexity. Use ELB for multi-region failover and resilience, CloudFront
3. DynamoDB offers cross region replication, RDS offers the ability to snapshot from one region to another to have read only replicas. Code Pipeline has a built in template for replicating DynamoDB elsewhere for DR
4. Redshift can snapshot within the same region and also replicate to another region

<h3>Demonstrate ability to implement self-healing capabilities</h3>

1. HA available already for most popular databases:-
2. SQL Server Availability Groups, SQL Mirroring, log shipping. Read replicas in other AZs not supported
3. MySQL – Asynchronous mirroring
4. Oracle – Data Guard, RAC (RAC not supported on AWS but can run on EC2 by using VPN and Placement Groups as multicast is not supported)
5. RDS has multi-AZ automatic failover to protect against
6. Loss of availability in primary AZ
7. Loss of connectivity to primary DB
8. Storage or host failure of primary DB
9. Software patching (done by AWS, remember)
10. Rebooting of primary DB
11. Uses master and slave model
12. MySQL, Oracle and Postgres use physical layer replication to keep data consistent on the standby instance
13. SQL Server uses application layer mirroring but achieves the same result
14. Multi-AZ uses synchronous replication (consistent read/write), asynchronous (potential data loss) is only used for read replicas
15. DB backups are taken from the secondary to reduce I/O load on the primary
16. DB restores are taken from the secondary to avoid I/O suspension on the primary
17. AZ failover can be forced by rebooting your instance either via the console or via the RebootDBInstance API call
18. Multi-AZ databases are used for DR, not as a scaling solution. Scale can be achieved by using read replicas, this can be done via the AWS console or by using the CreateDBInstanceReadReplica API call
19. Amazon Aurora employs a highly durable, SSD-backed virtualized storage layer purpose-built for database workloads. 
20. Amazon Aurora automatically replicates your volume six ways, across three Availability Zones. Amazon Aurora storage is fault-tolerant, transparently handling the loss of up to two copies of data without affecting database write availability and up to three copies without affecting read availability. Amazon Aurora storage is also self-healing. Data blocks and disks are continuously scanned for errors and replaced automatically.
21. Creating a read replica means a snapshot of your primary DB instance, this may result in a pause of about a minute in non multi-AZ deployments
22. Multi-AZ deployments will use a secondary for a snapshot
23. A new DNS endpoint address is given for the read only replica, you need to update the app
24. You can promote a read only replica to be a standalone, but this breaks replication
25. MySQL and Postgres can have up to 5 replicas
26. Read replicas in different regions for MySQL only
26. Replication is asynchronous only
27. Read replicas can be built off Multi-AZ databases
28. Read replicas are not multi-AZ
29. MySQL can have read replicas of read replicas, but this increases latency
30. DB Snapshots and automated backups cannot be taken of read replicas
31. Consider using DynamoDB instead of RDS if your database does not require:-
32. Transaction support
33. Atomicity
34. Consistency
35. Isolation
36. Durability
37. ACID (durability) compliance
38. Joins
39. SQL
