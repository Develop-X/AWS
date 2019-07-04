
|     |     |     |     |     |     |     |     |     |
|:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |
| [#](#-names) 	| [EBS](#EBS) 	| [Route53](#Route53) 	| [ALB](#ALB) 	| [Database](#Database) 	| [S3](#s3) 	| [AMI ](#AMI) 	| [EC2](#EC2) 	| [H](#h-names) 	|
| [I](#i-names) 	| [J](#j-names) 	| [K](#k-names) 	| [L](#l-names) 	| [M](#m-names) 	| [N](#n-names) 	| [O](#o-names) 	| [P](#p-names) 	| [Q](#q-names) 	|
| [R](#r-names) 	| [s](#s-names) 	| [T](#t-names) 	| [U](#u-names) 	| [V](#v-names) 	| [W](#w-names) 	| [X](#x-names) 	| [Y](#y-names) 	| [Z](#z-names)  	|

#### EC2
* **difference between ec2 and ecs** ```AWS ECS is just a logical grouping (cluster) of EC2 instances, and all the EC2 instances part of an ECS act as Docker host i.e. ECS can send command to launch a container on them ( EC2 ). ... An Amazon ECS without any EC2 registered (added to the cluster) is good for nothing.```

#### AMI
*  **What is AMI?** ```AMI stands for Amazon Machine Image.  It’s a template that provides the information (an operating system, an application server, and applications) required to launch an instance, which is a copy of the AMI running as a virtual server in the cloud.  You can launch instances from as many different AMIs as you need.```

#### S3
* **Explain what S3 is?** ```S3 stands for Simple Storage Service. You can use S3 interface to store and retrieve any amount of data, at any time and from anywhere on the web.  For S3, the payment model is “pay as you go.”```

#### EBS

* **What type of performance can you expect from Elastic Block Storage? How do you back it up and enhance the performance ?**
```Performance of an elastic block storage varies i.e. it can go above the SLA performance level and after that drop below it. SLA provides an average disk I/O rate  which can at times frustrate performance experts who yearn for reliable and consistent disk throughput on a server. Virtual AWS instances do not behave this way. One can backup EBS volumes through a graphical user interface like elasticfox or use the snapshot facility through an API call. Also, the performance can be improved by using Linux software raid and striping across four volumes.```

* **Imagine that you have an AWS application that requires 24x7 availability and can be down only for a maximum of 15 minutes. How will you ensure that the database hosted on your EBS volume is backed up?**
```Automated backup are the key processes here as they work in the background without requiring any manual intervention. Whenever there is a need to back up the data, AWS API and AWS CLI play a vital role in automating the process through scripts. The best way is to prepare for a timely backup of EBS of the EC2 instance. The EBS snapshot should be stored on Amazon S3 and can be used for recovery of the database instance in case of any failure or downtime.```

#### Route53
* **You create a Route 53 latency record set from your domain to a system in Singapore and a similar record to a machine in Oregon. When a user located in India visits your domain, to which location will he be routed to?**
```Assuming that the application is hosted on Amazon EC2 instance and multiple instances of the applications are deployed on different EC2 regions. The request is most likely to go to Singapore because Amazon Route 53 is based on latency and it routes the requests based on the location that is likely to give the fastest response possible.```

#### ALB
* **Differentiate between vertical and horizontal scaling in AWS.** ```The main difference between vertical and horizontal scaling is the way in which you add compute resources to your infrastructure. In vertical scaling, more power is added to the existing machine while in horizontal scaling additional resources are added into the system with the addition of more machines into the network so that the workload and processing is shared among multiple devices. The best way to understand the difference is imagine that you are retiring your Toyota and buying a Ferrari because you need more horsepower. This is vertical scaling. Another way to get that added horsepower is not to ditch the Toyota for the Ferrari but buy another car. This can be related to horizontal scaling where you drive several cars all at once.When the users are up to 100, an EC2 instance alone is enough to run the entire web application or the database until the traffic ramps up. Under such circumstances when the traffic ramps up, it is better to scale vertically by increasing the capacity of the EC2 instance to meet the increasing demands of the application. AWS supports instances up to 128 virtual cores or 488GB RAM.When the users for your application grow up to 1000 or more, vertical cannot handle requests and there is need for horizontal scaling which is achieved through distributed file system, clustering, and load balancing.```

#### Database
* **Differentiate between Amazon RDS, Redshift and Dynamo DB.**

| Features                       | Amazon RDS                            | Redshift                 | Dynamo DB                       |
|--------------------------------|---------------------------------------|--------------------------|---------------------------------|
| Computing Resources            | Instances with 64 vCPU and 244 GB RAM | Nodes with vCPU and 244 GB RAM | Not specified, SaaS-Software as a Service.|
| Database Engine            | MySQL, Oracle DB, SQL Server,Amazon Aurora, Postgre SQL | Redshift | NoSQL |
| Primary Usage Feature            | Conventional Databases | Datawarehouse | Database for dynamically modified data |
| Feature            | (RDS) is a good solution for those, who want to run a common database engine with no need for dealing with administration and maintenance. AWS presupposes RDS to be a fully functional alternative to common hardware databases. It is fast, scalable and can be replicated among Availability Zones for greater accessibility. | is a tool designed to work with data of up to dozens of petabytes. Powered by PostgreSQL, it is mostly applied to any kind of SQL applications with minimum changes. The target feature of the service is creating a data warehouse, where a user may focus on data management without keeping an effortful and complex infrastructure.From the technical point of view, Redshift is a cluster database without such consistency features as a foreign key and the uniqueness of field values. The cluster includes a number of nodes with virtual databases powered by Amazon Elastic Compute Cloud (EC2) instances. Those nodes are basic database units that you can use for your tasks. | is a NoSQL database service by AWS designed for fast processing of small data, which dynamically grows and changes. The main non-relative feature of DynamoDB is the unstrict structure of a table – it consists of items (as compared to rows in a traditional table) and attributes (an analog to columns). Carrying over of relational engines, it resembles a table with an individual number of columns in each row. Database mutability and fast I/O rate is powered by an SSD used as the basic (and the only) storage hardware. |
