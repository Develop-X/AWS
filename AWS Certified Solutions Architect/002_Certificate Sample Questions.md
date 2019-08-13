## Certification Questions

1. A company is storing an access key (access key ID and secret access key) in a text file on a custom AMI. The company uses the access key to access DynamoDB tables from instances created from the AMI. The security team has mandated a more secure solution. 
Which solution will meet the security team’s mandate? 
  
   * A. Put the access key in an S3 bucket, and retrieve the access key on boot from the instance.  
   * B. Pass the access key to the instances through instance user data. 
   * C. Obtain the access key from a key server launched in a private subnet.  
   * D. Create an IAM role with permissions to access the table, and launch all instances with the new role. 
  
2.  A company is developing a highly available web application using stateless web servers. Which services are suitable for storing session state data? (Select TWO.) 
 
    * A. CloudWatch
    * B. DynamoDB  
    * C. Elastic Load Balancing  
    * D. ElastiCache 
    * E. Storage Gateway 
 
3) Company salespeople upload their sales figures daily. A Solutions Architect needs a durable storage solution for these documents that also protects against users accidentally deleting important documents.  
   Which action will protect against unintended user actions?  
   
   * A. Store data in an EBS volume and create snapshots once a week.  
   * B. Store data in an S3 bucket and enable versioning.  
   * C. Store data in two S3 buckets in different AWS regions.  
   * D. Store data on EC2 instance storage. 
   
4) An application requires a highly available relational database with an initial storage capacity of 8 TB. The database will grow by 8 GB every day. To support expected traffic, at least eight read replicas will be required to handle database reads. 
   Which option will meet these requirements? 
   
   * A. DynamoDB  
   * B. Amazon S3  
   * C. Amazon Aurora  
   * D. Amazon Redshift

## Answers 
* 1 - D – IAM roles for EC2 instances allow applications running on the instance to access AWS resources without having to create and store any access keys. Any solution involving the creation of an access key then introduces the complexity of managing that secret. 
