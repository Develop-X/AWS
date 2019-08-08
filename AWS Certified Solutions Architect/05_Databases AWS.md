# Databases on AWS

![Database_Types](https://user-images.githubusercontent.com/8856857/62659991-366ce680-b9b0-11e9-98be-c36f0573ed2d.png)
![AWS_Database_Use_Cases](https://user-images.githubusercontent.com/8856857/62659707-6f588b80-b9af-11e9-826c-448ac6f8fd9b.png)

## Databases 101

### RDBMS

RDBMS Types - **MOMMAP**

  - MS-SQL Server

  - Oracle

  - MySQL

  - PostgreSQL

  - Aurora

  - MariaDB

### NoSQL DBs

Document Oriented

  - CouchDB,

  - MongoDB

  - Dynamo DB

Collection = Table, Document = Row, Keys-Value Pairs = Fields

### Data Warehousing

OLTP(Online transaction processing) (pulls out specific / narrow record set) vs OLAP( Online Analytical Processing) – (pulls in large number of records). It uses different architecture and infrastructure layer.  Differ in terms of queries run on top of data. OLAP is more about aggregation.

### ElastiCache

In memory cache in cloud.

  - Memcached

  - Redis

Exam – Improve database performance – e.g. top 10 deals of the day.

### Database Migration Service

Migrate production database to AWS. AWS manages all complexities of migration process. **Source database remains fully operational**. Both **homogenous (Oracle to Oracle)** as well as **heterogeneous migrations are supported (Oracle to Aurora or Microsoft SQL)**. Can also be used for continuous data replication with high availability

**AWS Schema migration tool makes heterogeneous database**  - migrations  - easy by automatically converting the source database schema and a majority of the custom code, including views, stored procedures, and functions, to a format compatible with the target database. Any code that cannot be automatically converted is clearly marked so that it can be manually converted.

## RDS – Back Ups, Multi AZs & Read Replicas

**OLTP systems**

### Backups

  - **Automated Backups** – full daily snapshot & will also store transaction logs.  

  - Enabled by default. Stored in S3. **Free backup storage in S3 upto the RDS Instance size.**  

  - You can define backup window. Choose wisely.

  - **Backups are deleted when the RDS Instance is deleted.**

### Snapshots

  - **Done manually. They are stored even after you delete the instance.**

  - You can copy snapshots across regions.

  - You can publish the snapshot to make it publically available.

  - **Restoring Backups/ Snapshots – The restored version will be a new RDS instance with new end point.**

  - You can check the instance size to restore.

  - You cannot restore to existing instance

### Encryption

  - **Encryption at rest is supported for MySQL, SQL Server, Oracle and PostgreSQL & MariaDB.** relational databases

  - Managed by AWS KMS.

  - **Cannot encrypt an already present instance.** To encrypt, create new instance with encryption enabled and then migrate your data to it.

### Multi-AZ Deployment

  - A standby copy is created in another AZ. AWS handles replication and auto-failover

  - AWS can automatically failover RDS instance to another instance.

  - In case of failover, No need to change connection string.

  - This can be used for DR purpose only. This option has to be selected at instance creation time. This option is not useful for improving performance / scaling.

### Read Replica Databases.

  - Read-replica – async data transfer to another RDS instance. You can actually read from these instances, unlike Multi-AZ deployments. You can also have read replicas of read-replicas up to 5 copies. (Watch out as async causes latency)-

  - Read-replicas can be used for Dev/Test environments, run certain workloads only against them and not against direct production deployment – Intensive workloads.

  - *MySQL , MariaDB, PostgreSQL only for read-replicas , no Oracle & SQL Server*

  - You cannot have read-replicas that have multi-AZ. However, you can create read replicas of Multi AZ source databases.

  - Read replicas can be of a different size than source DB.

  - Each read-replica will have its own DNS end point

  - Automatic backups must be turned on in order to deploy a read replica

  - Read Replicas can be promoted to be their own databases. This breaks replication. E.g. Dev/Test can be connected to the replica by first promoting it as DB itself.

  - Read Replicas can be done in a second region for MySQL and MariaDB – no PostgreSQL.

  - Application re-architecture is required to make use of Read replicas

  - Read replicas are not used for DR. they are used for performance scaling only.

## DynamoDB

  - Fast and flexible NoSQL database

  - Consistent, single digit millisecond latency.

  - Fully managed DB – supports both document based & Key-value data models.

  - Great fit for mobile, IoT, web, gaming etc. applications.

  - Stored on SSDs

  - Stored on 3 geographically distinct DCs (not AZs). Built in redundancy

  - Consistency

1. Eventual consistent reads - Consistency reached up to 1 second (default)

2. Strongly Consistent reads - Consistency reached after writes to all copies are completed. <1 second

Select type based on application needs

  - Pricing – Write Capacity Units and Read Capacity Units ($/hr.). Also Storage cost per month. You provision capacity in units/second. It can scale on the fly. Provisioned capacity.

  - Dynamo DB – Expensive for Writes. Cheap for Reads. Important point v/s RDS.

  - You can dynamically add columns – without the need to update other rows with the column data. As this is no RDBMS.

  - Reserved capacity is available for DynamoDB as well.

### RDS v/s DynamoDB

  - Use DynamoDB for Push button scaling. With RDS – to scale horizontally a new instance has to be created.

  - DynamoDB is cheap for reads and expensive for writes.

  - Observe workload characteristics and decide

  - Use RDS if data requires joins and relationships.

  - In RDBMS database structure cannot be dynamically altered. With DynamoDB you can.

## Redshift

Petabyte scale DW solution in cloud.  Used for OLAP – sum of various columns and joining the data.

### Configurations

  - Single Node – 160 GB. Used by Small and Medium Size businesses.

  - Multi-Node – Leader Node (handles all incoming connections & receives queries) & compute Node (store data and perform queries and computations – up to 128 Compute Nodes)

### Performance

  - Redshift is 10 times faster than usual OLAP systems.

  - It uses Columnar Data Store.  Columnar data is stored sequentially on storage system. Hence low I/O required – improving performance.

  - Advanced Compression (easier to do it via Columns instead of via Rows – which have different data types). Columns have similar type of data. Doesn’t use indexes and views – hence less storage required.

  - Based on data, appropriate data compression scheme is used.

  - Allows for massive parallel processing

### Pricing  

  - Based on Compute Node hours (compute node only – no leader node).

  - Backup and Data Transfer (only within VPC)

### Security

  - Transit encrypted via SSL,

  - At rest using AES-256 encryption

  - Can use your own HSM or default AWSK Key management.

### Availability

Not Multi-AZs. Can restore snapshots

Exam Tips – Database warehousing service, cheap, faster. Best seller AWS Service. Speed achieved due to columnar storage. And Data stored sequentially on disk – hence faster.

## ElastiCache

  - Easy to deploy, operate and scale an in-memory cache in the cloud.

  - Improve performance by avoiding repeated calls to DB.

  - Improve latency and throughput for read-heavy applications.

  - Can be used for compute intensive data

### Memcached

  - All Memcached tooling can be easily ported over.

### Redis

  - Supports Master / Slave replication and multi-AZ deployment to get redundancy.

Exam Tips

  - ElastiCache is used if DB is primarily read-heavy and not frequently changing

  - Use Redshift – if application is slow due to constant OLAP transactions on top of OLTP focused DB.

## Aurora

  - Bespoke Database Engine.

  - It is MySQL compatible.

  - However you can’t download and install on your workstation.

### Performance

5 times better performance than MySQL. At a fraction of cost as compared to Oracle.

### Scaling

  - Outset 10 GB Storage, auto increment of storage up to 64 TB

  - No Push button scaling – unlike DynamoDB

### Fault Tolerance

  - Maintains 2 copies of your data in at least 3 availability zones. This is for the Data only not for the instances that runs the Database.

  - 2 copies lost – no impact on write availability.

  - 3 copies lost – no impact on read availability.

  - Storage is self-healing.

### Replicas

  - MySQL Read Replica can be created from the Aurora source DB.(up to 5 of them)

  - Aurora Replicas – up to 15 of them. If leader crashes, the replica with the highest tiers becomes the leader. While creating replicas, remember to assign different tier levels.

  - Cluster Endpoint vs Individual Endpoint

No Free Tier usage available. Also available only in select regions. Takes slightly longer to provision

## Exam Tips

  - Why you can’t connect to DB Server from DMZ. Check the security group – if it is removed or added

  - Have separate groups for EC2 Instance and RDS Instance.

  - Multi-AZ for Disaster Recovery only. Not for performance improvement. For performance improvement use, multiple read-replicas

  - Dynamo DB v/s RDS

If you want push button scaling, without any downtown, you will always want to use DynamoDB.

With RDS scaling is not so easy, you have to use a bigger instance or add read replicas (manual process).

  - If you are using Amazon RDS Provisioned IOPS storage with a MySQL or Oracle database engine, what is the maximum size RDS volume you can have by default? – **6TB**

  - What data transfer charge is incurred when replicating data from your primary RDS instance to your secondary RDS instance? - **There is no charge associated with this action**.

  - When you have deployed an RDS database into multiple availability zones, can you use the secondary database as an independent read node? – **No**

  - RDS automatically creates RDS Security Group w/ TCP port # 3306 enabled. 

  - In VPC Security Group, the answer would be YES because you will have manually specify access to port & protocol.

