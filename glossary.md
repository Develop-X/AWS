# Everything AWS

### [Names](#names-1)
|     |     |     |     |     |     |     |     |     |
|:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |
| [#](#-names) 	| [A](#a-names) 	| [B](#b-names) 	| [C](#c-names) 	| [D](#d-names) 	| [E](#e-names) 	| [F](#f-names) 	| [G](#g-names) 	| [H](#h-names) 	|
| [I](#i-names) 	| [J](#j-names) 	| [K](#k-names) 	| [L](#l-names) 	| [M](#m-names) 	| [N](#n-names) 	| [O](#o-names) 	| [P](#p-names) 	| [Q](#q-names) 	|
| [R](#r-names) 	| [S](#s-names) 	| [T](#t-names) 	| [U](#u-names) 	| [V](#v-names) 	| [W](#w-names) 	| [X](#x-names) 	| [Y](#y-names) 	| [Z](#z-names)  	|


#### A names

* API Gateway - is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. With a few clicks in the AWS Management Console, you can create REST and WebSocket APIs that act as a “front door” for applications to access data, business logic, or functionality from your backend services, such as workloads running on Amazon Elastic Compute Cloud (Amazon EC2), code running on AWS Lambda, any web application, or real-time communication applications.

* AMI - An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.
An AMI includes the following:
  * One or more EBS snapshots, or, for instance-store-backed AMIs, a template for the root volume of the instance (for example, an operating system, an application server, and applications).
  * Launch permissions that control which AWS accounts can use the AMI to launch instances.
  * A block device mapping that specifies the volumes to attach to the instance when it's launched.

#### B names
#### C names

* CDN - A content delivery network (CDN) is a system of distributed servers (network) that deliver pages and other Web content to a user, based on the geographic locations of the user, the origin of the webpage and the content delivery server.

* CloudFront: Part of the CDN, consisting of edge locations to cache your assets, like videos, large media files etc.

#### D names

* Direct connect: Allows you to connect directly to where your Virtual Private Cloud(VPC) is located using connection links to Amazon data center into your VPC, and you don't need internet to access it

#### E names

* EC2 - Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. EC2: allowing one to provision instances inside your VPC, these are just virtual machines in the cloud that run on AWS

* EC2 instance - An EC2 instance is a virtual server in Amazon's Elastic Compute Cloud (EC2) for running applications on the Amazon Web Services (AWS) infrastructure. AWS is a comprehensive, evolving cloud computing platform; EC2 is a service that allows business subscribers to run application programs in the computing environment.

* EC2 Container Service: highly scalable, high performance container management service, supporting Docker containers, allowing you to run applications on a managed cluster of EC2 instances, eliminating the need to install, operate and scale your own cluster management infrastructure

* Elastic Beanstalk - is an orchestration service offered by Amazon Web Services for deploying applications which orchestrates various AWS services, including EC2, S3, Simple Notification Service (SNS), CloudWatch, autoscaling, and Elastic Load Balancers.
An easy to use service for developing and scaling web apps developed in Java, Dot Net etc., we can simply upload the code and EB will automatically handle the deployment from capacity provisioning, load balancing, autoscaling, app health and monitoring.

* Edge location: This is a CDN(Content-Delivery Network) endpoint. Edge locations are used by CloudFront to cache files near the user where they access them.

* Elastic Load Balancing (ELB) is a load-balancing service for Amazon Web Services (AWS) deployments. ELB automatically distributes incoming application traffic and scales resources to meet traffic demands.

#### F names

#### G names

* Glacier: Is an archiving service. Allows us to archive all our data in the Amazon cloud, not immediately accessible but take 3-5 hours to restore a file from Glacier,hence used for long-term storage

#### H names

#### I names

#### J names

#### K names

#### L names

* Lambda - AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running. With Lambda, you can run code for virtually any type of application or backend service - all with zero administration. Just upload your code and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app.
Lambda: Is Serverless. Upload your code to respond to events.

* Lightsail: A completely brand new service introduced in 2016. Allows anyone who does not understand AWS to deploy a site in a few seconds

#### M names

#### N names

#### O names

#### P names

#### Q names

#### R names

* Regions: A place where AWS resources exists a geographical area, there are 15 regions (as of 2015). Each region consists of multiple availability zones, currently 49 in total(as of 2017). An Availability Zone(AZ) is simply a data center. [Reigons and Availability Zones](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html)

* Route 53: Amazon’s DNS service, basically allows you to host your domain name with Amazon. 53 is the DNS port. When you open up DNS world you do this on port 53. You can use Amazon Route 53 to configure DNS health checks to route traffic to healthy endpoints or to independently monitor the health of your application and its endpoints.

#### S names

* S3(Simple Storage Service): S3 is a file-based storage or object based storage. Allows us to store files in the cloud of sizes ranging from 1 byte to 5 terabytes

#### T names

#### U names

#### V names

* VPC (Virtual Private Cloud): A virtual data center as a collection of AWS resources, such as EC2 instances, EBS instances, and Load Balancers
