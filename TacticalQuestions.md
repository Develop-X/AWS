
|     |     |     |     |     |     |     |     |     |
|:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |:-:  |
| [#](#-names) 	| [EBS](#EBS) 	| [Route53](#Route53) 	| [ALB](#ALB) 	| [D](#d-names) 	| [E](#e-names) 	| [F](#f-names) 	| [G](#g-names) 	| [H](#h-names) 	|
| [I](#i-names) 	| [J](#j-names) 	| [K](#k-names) 	| [L](#l-names) 	| [M](#m-names) 	| [N](#n-names) 	| [O](#o-names) 	| [P](#p-names) 	| [Q](#q-names) 	|
| [R](#r-names) 	| [S](#s-names) 	| [T](#t-names) 	| [U](#u-names) 	| [V](#v-names) 	| [W](#w-names) 	| [X](#x-names) 	| [Y](#y-names) 	| [Z](#z-names)  	|


#### EBS

* What type of performance can you expect from Elastic Block Storage? How do you back it up and enhance the performance ?
```Performance of an elastic block storage varies i.e. it can go above the SLA performance level and after that drop below it. SLA provides an average disk I/O rate  which can at times frustrate performance experts who yearn for reliable and consistent disk throughput on a server. Virtual AWS instances do not behave this way. One can backup EBS volumes through a graphical user interface like elasticfox or use the snapshot facility through an API call. Also, the performance can be improved by using Linux software raid and striping across four volumes.```

* Imagine that you have an AWS application that requires 24x7 availability and can be down only for a maximum of 15 minutes. How will you ensure that the database hosted on your EBS volume is backed up?
```Automated backup are the key processes here as they work in the background without requiring any manual intervention. Whenever there is a need to back up the data, AWS API and AWS CLI play a vital role in automating the process through scripts. The best way is to prepare for a timely backup of EBS of the EC2 instance. The EBS snapshot should be stored on Amazon S3 and can be used for recovery of the database instance in case of any failure or downtime.```

#### Route53
* You create a Route 53 latency record set from your domain to a system in Singapore and a similar record to a machine in Oregon. When a user located in India visits your domain, to which location will he be routed to?
```Assuming that the application is hosted on Amazon EC2 instance and multiple instances of the applications are deployed on different EC2 regions. The request is most likely to go to Singapore because Amazon Route 53 is based on latency and it routes the requests based on the location that is likely to give the fastest response possible.```

#### ALB
* Differentiate between vertical and horizontal scaling in AWS.
```The main difference between vertical and horizontal scaling is the way in which you add compute resources to your infrastructure. In vertical scaling, more power is added to the existing machine while in horizontal scaling additional resources are added into the system with the addition of more machines into the network so that the workload and processing is shared among multiple devices. The best way to understand the difference is imagine that you are retiring your Toyota and buying a Ferrari because you need more horsepower. This is vertical scaling. Another way to get that added horsepower is not to ditch the Toyota for the Ferrari but buy another car. This can be related to horizontal scaling where you drive several cars all at once.

When the users are up to 100, an EC2 instance alone is enough to run the entire web application or the database until the traffic ramps up. Under such circumstances when the traffic ramps up, it is better to scale vertically by increasing the capacity of the EC2 instance to meet the increasing demands of the application. AWS supports instances up to 128 virtual cores or 488GB RAM.

When the users for your application grow up to 1000 or more, vertical cannot handle requests and there is need for horizontal scaling which is achieved through distributed file system, clustering, and load balancing.```
