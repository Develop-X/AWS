# Everything AWS

### [Names](#names-1)
|     |     |     |     |     |     |     |     |     |
|:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |
| [#](#-names) 	| [A](#a-names) 	| [B](#b-names) 	| [C](#c-names) 	| [D](#d-names) 	| [E](#e-names) 	| [F](#f-names) 	| [G](#g-names) 	| [H](#h-names) 	|
| [I](#i-names) 	| [J](#j-names) 	| [K](#k-names) 	| [L](#l-names) 	| [M](#m-names) 	| [N](#n-names) 	| [O](#o-names) 	| [P](#p-names) 	| [Q](#q-names) 	|
| [R](#r-names) 	| [S](#s-names) 	| [T](#t-names) 	| [U](#u-names) 	| [V](#v-names) 	| [W](#w-names) 	| [X](#x-names) 	| [Y](#y-names) 	| [Z](#z-names)  	|


#### A names

* **API Gateway** - is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. With a few clicks in the AWS Management Console, you can create REST and WebSocket APIs that act as a “front door” for applications to access data, business logic, or functionality from your backend services, such as workloads running on Amazon Elastic Compute Cloud (Amazon EC2), code running on AWS Lambda, any web application, or real-time communication applications.

* **AMI** - An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.
An AMI includes the following:
  * One or more EBS snapshots, or, for instance-store-backed AMIs, a template for the root volume of the instance (for example, an operating system, an application server, and applications).
  * Launch permissions that control which AWS accounts can use the AMI to launch instances.
  * A block device mapping that specifies the volumes to attach to the instance when it's launched.

* **Athena**: SQL queries on S3

#### B names

#### C names

* **CDN** - A content delivery network (CDN) is a system of distributed servers (network) that deliver pages and other Web content to a user, based on the geographic locations of the user, the origin of the webpage and the content delivery server.

* **CloudFront**: Part of the CDN, consisting of edge locations to cache your assets, like videos, large media files etc.

* **Cloud Search / Elastic Search** : Search engine for your website or your application, Cloud search is fully managed service provided by AWS, Elastic search uses open source framework

#### D names

* **Direct connect**: Allows you to connect directly to where your Virtual Private Cloud(VPC) is located using connection links to Amazon data center into your VPC, and you don't need internet to access it

* **DynamoDB**: For NoSQL

* **DMS(Database Migration services)**: This allows migration of on-premise databases to AWS cloud

* **Data Pipeline**: Allows to move data from one place to another

#### E names

* **EC2** - Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. EC2: allowing one to provision instances inside your VPC, these are just virtual machines in the cloud that run on AWS

* **EC2 instance** - An EC2 instance is a virtual server in Amazon's Elastic Compute Cloud (EC2) for running applications on the Amazon Web Services (AWS) infrastructure. AWS is a comprehensive, evolving cloud computing platform; EC2 is a service that allows business subscribers to run application programs in the computing environment.

* **EC2 Container Service**: highly scalable, high performance container management service, supporting Docker containers, allowing you to run applications on a managed cluster of EC2 instances, eliminating the need to install, operate and scale your own cluster management infrastructure

* **Elastic Beanstalk** - is an orchestration service offered by Amazon Web Services for deploying applications which orchestrates various AWS services, including EC2, S3, Simple Notification Service (SNS), CloudWatch, autoscaling, and Elastic Load Balancers.
An easy to use service for developing and scaling web apps developed in Java, Dot Net etc., we can simply upload the code and EB will automatically handle the deployment from capacity provisioning, load balancing, autoscaling, app health and monitoring.

* **Edge location**: This is a CDN(Content-Delivery Network) endpoint. Edge locations are used by CloudFront to cache files near the user where they access them.

* **Elastic Load Balancing (ELB)** is a load-balancing service for Amazon Web Services (AWS) deployments. ELB automatically distributes incoming application traffic and scales resources to meet traffic demands.

* **EFS(Elastic File service)**: File based storage and you can share it, you can install databases, applications.

* **Elastic Cache**: Allows/offers an in-memory caching service for the AWS platform.

* **ElasticMapReduce(EMR)**:
  * A web service that makes it easy to quickly and cost-effectively process vast amounts of data.
  * Uses Hadoop, an open source framework to distribute your data and process across a resizeable cluster of Amazon EC2 instances.
  * It can also run other distributed framework such as Spark and Presto.
  * EMR is used in a variety of applications including log analysis, web-indexing, data warehousing, machine learning, financial analysis, scientific simulation, and Bioinformatics, customers launch millions of Amazon’s EMR clusters each year
  * Allows you root access(i.e. login via SSH)
  
#### F names

#### G names

* **Glacier**: Is an archiving service. Allows us to archive all our data in the Amazon cloud, not immediately accessible but take 3-5 hours to restore a file from Glacier,hence used for long-term storage

#### H names

#### I names

#### J names

#### K names

* **Kinesis**:
  * Is a fully-managed service for real-time processing of streaming data at massive scale.
  * Can continuously change and store terabytes of data per hour from several sources such as website clickstreams, social media, location tracking event.
  * With Kinesis client library ACL, we can build Amazon Kinesis apps, and use streaming data to power real time dashboards, generate alerts, implement dynamic pricing and advertising or more
  * We can emit data from Kinesis to other AWS services such as S3, redShift, Elastic MapReduce, and lambda

#### L names

* **Lambda** - AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running. With Lambda, you can run code for virtually any type of application or backend service - all with zero administration. Just upload your code and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app.
Lambda: Is Serverless. Upload your code to respond to events.

* **Lightsail**: A completely brand new service introduced in 2016. Allows anyone who does not understand AWS to deploy a site in a few seconds

#### M names

#### N names

#### O names

#### P names

#### Q names

* **Quick Sight** : used for creating visualizations, dashboards for BI/Analytics

#### R names

* **Regions**: A place where AWS resources exists a geographical area, there are 15 regions (as of 2015). Each region consists of multiple availability zones, currently 49 in total(as of 2017). An Availability Zone(AZ) is simply a data center. [Reigons and Availability Zones](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html)

* **Route 53**: Amazon’s DNS service, basically allows you to host your domain name with Amazon. 53 is the DNS port. When you open up DNS world you do this on port 53. You can use Amazon Route 53 to configure DNS health checks to route traffic to healthy endpoints or to independently monitor the health of your application and its endpoints.

* **RDS(Relational Database Services)** : Consists of elements such as SQLServer by MS, Oracle, PostgreSQL, MySQL, and Amazon’s own database engine known as Aurora completely MySQL compatible db but designed to run specifically on the AWS platform.

* **RedShift**: A fast, fully-managed petabyte scaled datawarehousing solution, that makes it simple and cost-effective to efficiently analyze your data using your existing BI tools. It is designed from the infrastructure layer upwards to maximize performance and minimize cost.

#### S names

* **S3(Simple Storage Service)**: S3 is a file-based storage or object based storage. Allows us to store files in the cloud of sizes ranging from 1 byte to 5 terabytes

* **Storage gateway**: A service that connects on-premise software appliance with cloud based storage to provide seamless and secure integration between organizations on premise IT equipment and AWS storage infrastructure.

* **Snowball**: This is a data transport solution that uses secure appliances to transfer large amounts of data, into and out of AWS. It addresses common challenges with large-scale data transfers such as high network costs, long transfer times, and security concerns.

* **SMS(Server Migration Service)**: does same work as the DMS but targets virtual machines, to replicate vms to aws cloud

#### T names

#### U names

#### V names

* **VPC (Virtual Private Cloud)**: A virtual data center as a collection of AWS resources, such as EC2 instances, EBS instances, and Load Balancers
