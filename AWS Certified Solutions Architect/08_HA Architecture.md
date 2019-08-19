# ELASTIC LOAD BALANCER
## What is it?

It is a physical or virtual device that's designed to help you balance network load across multiple web servers.

You can also use it for applications, it does not have to necessarily be internet facing load balancer but typically they are internet facing and primarily they are used to balance load across web servers.

## Types
#### Application load balancer:

Are best suited for load balancing of HTTP and HTTPS traffic. They operate at Layer 7 and are application-aware. They are intelligent, and you can create advanced request routing, sending specified requests to specific web servers.

#### Network load balancer:

Are best suited for load balancing of TCP traffic where extreme performance is required. Operating at the connection level (Layer 4), Network Load Balancer are capable of handling millions of requests per second, while maintaining ultra-low latencies. Use for extreme performance!

#### Classic load balancer:

Are the legacy Elastic Load Balancers. You can load balance HTTP/HTTPS applications and use Layer 7-specific features, such as X-Forwarded and sticky sessions. You can also use strict Layer 4 load balancing for applications that rely purely on the TCP protocol.

If your application stops responding, the ELB (Classic Load Balancer) responds with a 504 error. This means that the application is having issues. This could be either at the web server layer or at the database layer. Identify where the application is failing, and scale it up or out where possible.

## Tips

- 504 errors means the gateway has timed out. This means that the application not responding within the idle timeout period.
- Trouble shoot the application. Is it the web server or database server?
- If you need the IPv4 address of your end user, look for the **X-Forwarded-For** header.

# ELB CREATION
## Load balancer type

Select *create load balancer*. (classic)

## Define load balancer

- **Load balancer name**: \<loadbalancername\>
- **Create LB inside**: \<vpcname\>
- [ ] Create an internal load balancer.
- [ ] Enable advanced VPC configuration.
- [ ] Listener configuration.
- **Load balancer protocol**: \<HTTP\>.

## Assign security groups

Select an existing or new security group.

## Configure health check

- **Ping protocol**: \<HTTP\>
- **Ping port**: \<80\>
- **Ping path**: \<projectpath-or-index.html\>

#### Advanced details:

- **Response timeout**: \<2\>
- **Interval**: \<5\>
- **Unhealthy threshold**: \<2\>
- **Healthy threshold**: \<3\>

## Select EC2 instances

Select all the instance to apply ELB.

- [x] Enable Cross-Zone load balancing.
- [x] Enable connection draining. \<300\>

#### Status of instance:

Check load balancer instances:
- [x] InService.
- [ ] OutOfService.

## Target group

Is basically where you load balancer is going to root request to the targets in that target group, and using the target that you specify and perform health checks.

So it is basically you could have a group of loot of easy two instances for your European customers, then you could have different ones for your American customers which have different language settings, etc. You can actually craete application load balancer that detect it and send it to the right groups.

#### Creation:

- **Target group name**: \<webgroupname\>
- **Target type**: \<Instance\>
- **Protocol**: <\HTTP\>
- **Port**: \<80\>
- **Vpc**: \<defaultone\>

- **Health check settings**:
	- Protocol: \<HTTP\>
	- Path: \<pathtoourweb\>
- **Advanced health check settings**:
	- Port: \<traffic-port\>
	- Healthy threshold: \<2\>
	- Unhealthy threshold: \<3\>
	- Timeout: \<5\>
	- Interval: \<6\>
	- Success codes: \<200\>
- Add instances to the registered target groups.

## Now create a load balancer with the target group

- Select *load balancer* and pick up the first option. (Application Load Balancer)
- Name: \<mynewloadbalancer\>
- Scheme: \<internet-facing\>

#### Listener:

On *listener* the rules can be edited.

# ADVANCED LOAD BALANCER
## What are Sticky Sessions?

Classic Load Balancer routes each request independently to the registered EC2 instance with the smallest load.

Sticky sessions allow you to bind a user's session to a specific EC2 instance. This ensures that all requests from the user during the session are sent to the same instance.

You cab enable Sticky Sessions for application Load Balancer as well, but the traffic will be sent to at the Target Group Level.

## Cross Zone Load Balancing

- Without CZLB:
	- A (50%)
		- A1: 12.5%.
		- A2: 12.5%.
		- A3: 12.5%.
		- A4: 12.5%.
	- B (50)
		- B1: 50%.

- With CZLB:
	- A (50%)
		- A1: 20%.
		- A2: 20%.
		- A3: 20%.
		- A4: 20%.
	- B (50)
		- B1: 20%.

## What are path patterns?

You can create a listener with rules to forward requests based on the URL path. This is known as path-based routing. If you are running microservices, you can route traffic to multiple back-end services uing path-based routing. For example, you can route general requests to one target group and requests to render images to another target group.

## Advanced Load Balancer Theory

- Sticky Sessions enable your users to stick to the same EC2 instance. Can be useful if you are storing information locally to that instance.
- Cross Zone Load Balancing enables you to load balance across multiple availability zones.
- Path patters allow you to direct traffic to different EC2 instances based on the URL contained in the request.

# AUTO SCALING GROUP
## Create launch configuration

- **Name**: \<nameoflc\>
- [ ] Request spot instances.
- **IAM role**: <anyrole>
- [ ] Enable CloudWatch detailed monitoring.

#### Advanced details:

- **Kernel ID**: default.
- **RAM disk ID**: default.
- **User data**: \<scrip\> (any script)
- **IP address type**: Only assign a public IP address to instances launched in the default VPC and subnet. (default)

## Create auto scaling group

- **Group name**: \<asgname\>
- **Launch configuration**: \<nameoflc\>
- **Group size**: Star with \<3\> instances.
- **Subnet**: all.
- [ ] Keep this group at its initial size.
- [x] Use scaling policies to adjust the capacity of this group.

#### Conf:

- **Name**: \<scalegroupsize\>
- **Metric type**: \<Average CPU Utilization\>
- **Targer value**: \<80\>
- [ ] Disable scale-in.

## Tips

If we remove (termination) an instance of EC2, a new one is automatically created in the same availability zone to satisfy the established minimum requirement.

# HA ARCHITECTURE
## Remember the following

- Always design for failure.
- Use multiple AZ's and multiple regions where ever you can.
- Know the difference between multi-az and read replicas for RDS.
- Know the difference between scaling out and scaling up.
- Read the question carefully and always consider the cost element.
- Know the different S3 storage class.

# CLOUDFORMATION
## Slack

- Select *create slack*.
- [x] Use a sample template.
- Sample templates: WordPress blog.

#### Stack name:

- **DB Name**: \<dbname\>
- **DB Password**: \<dbpassword\>
- **DB Root Password**: \<mysqldbpassword\>
- **Db User**: \<dbusername\>
- **Instance Type**: \<t2.small\>
- **Key Name**: \<keyname\> (.pem)
- **SSH Location**: \<\>

## AWS CloudFormation
* Gives developers and system administrators an easy way to create and manage a collection fo related AWS resources provisioning and updating them so in an orderly and predictable fashion
### Templates and Stacks
| Templates|Stacks|                
| ------|---------------------------
| Templates are architectural designs     | Stacks are deployed resources 
| You can create, update and delete templates | You can create, update and delete stacks using templates
| CloudFormation templates are written in JSON 
### Templates
* You don't need to figure out the order for provisioning AWS services
* You don't need to worry about making dependencies to work 
* Modify and update templates ina a controlled and predictable way
    * In effect applying version control
* Visualize with the AWS Cloudformation Designer
### Deploying Stacks
* AWS Management Console
* Command Line Interface
* APIs
### Template Elements
* File format and version (required)
* List of resources and associated configuration values (required)
* Template parameters (optional - up to 60)
* Output values(optional - up to 60)
* List of data tables
### Intrinsic Function
* Provides several built-in functions that help you manage your stacks 
* Assing values to properties that are not available until runtime
* Functions include: Fn::Base64, condition functions, Fn::FindInMap, Fn::GetAZs, Fn::Join, Fn::Select
### Need to Know
* Puppet and Chef integration
* Bootstrap scripts
* Define deletion policies
* Provides wait condition
* Create roles in IAM
* VPCs can be created and customized
* VPC peering in the same AWS account
* Route 53 supported
### Stack Creation Errors
* Automatic rollback on error is enabled by default 
* You will be chrged for resources provisioned even if there is an error
* CloudFormation is free


## Tips

- Is a way of completely scripting your cloud environment.
- Quick start is a bunch of CloudFormation templates already built by AWS Solution Architects allowing you to create complex environments very quickly.

# ELASTIC BEANSTALK
## Get started

- **Application name**: \<elasticbeanstalkname\>
- **Platform**: \<php\>
- [x] Sample application. (application code)

## Tips

With Elastic BeanStalk, you can quickly deploy and manage applications in the AWS Cloud without worrying about the infrastructure that runs those applications. You simply upload your application, and Elastic BeanStalk automatically handles the details of capacity provisioning, load balancing, scaling, and application health monitoring.
