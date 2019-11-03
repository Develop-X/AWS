## Certification Questions

1. A company is storing an access key (access key ID and secret access key) in a text file on a custom AMI. The company uses the access key to access DynamoDB tables from instances created from the AMI. The security team has mandated a more secure solution. 
Which solution will meet the security team’s mandate? 

* IAM roles for EC2 instances allow applications running on the instance to access AWS resources without having to create and store any access keys. Any solution involving the creation of an access key then introduces the complexity of managing that secret
  
2.  A company is developing a highly available web application using stateless web servers. Which services are suitable for storing session state data? (Select TWO.) 
 
* Both **DynamoDB** and **ElastiCache** provide high performance storage of key-value pairs. CloudWatch and ELB are not storage services. Storage Gateway is a storage service, but it is a hybrid storage service that enables on-premises applications to use cloud storage.
 
3. Company salespeople upload their sales figures daily. A Solutions Architect needs a durable storage solution for these documents that also protects against users accidentally deleting important documents.  
   Which action will protect against unintended user actions?  

* Store data in an S3 bucket and enable versioning. If a versioned object is deleted, then it can still be recovered by retrieving the final version. Response A would lose any changes committed since the previous snapshot. Storing the data in 2 S3 buckets would provide slightly more protection, but a user could still delete the object from both buckets. EC2 instance storage is ephemeral and should never be used for data requiring durability. 
   
4. An application requires a highly available relational database with an initial storage capacity of 8 TB. The database will grow by 8 GB every day. To support expected traffic, at least eight read replicas will be required to handle database reads. 
   Which option will meet these requirements? 
   
* **Amazon Aurora** is a relational database that will automatically scale to accommodate data growth. Amazon Redshift does not support read replicas and will not automatically scale. DynamoDB is a NoSQL service, not a relational database. Amazon S3 is object storage, not a relational database.

5. A Solutions Architect is designing a critical business application with a relational database that runs on an EC2 instance. It requires a single EBS volume that can support up to 16,000 IOPS. Which Amazon EBS volume typecan meet the performance requirements of this application?

* EBS Provisioned IOPS SSD provides sustained performance for mission-critical low-latency workloads. EBS General Purpose SSD can provide bursts of performance up to 3,000 IOPS and have a maximum baseline performance of 10,000 IOPS for volume sizes greater than 3.3 TB. The 2 HDD options are lower cost, high throughput volumes.
