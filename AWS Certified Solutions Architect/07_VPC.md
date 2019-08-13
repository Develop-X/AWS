# VPC

Important section for all exams☺. You should be able to build out own VPCs from memory.

## Introduction

  - **VPC is a logical data center within an AWS Region.**

  - **Control over network environment, select IP address range, subnets and configure route tables and gateways.**

  - **Do not span regions, but can span AZs.**

  - **Can create public facing subnet (Web) having internet access and private facing subnet (DB) with no internet access**

  - **Public Subnet** – Web Servers/ **Jump Boxes** (A jump box functions like a proxy server and is a way to isolate access to a private network. It is usually a computer that is connected to two networks and has two network cards. One network card is configured with an external IP address that is accessible from the Internet. The second network card provides an internal IP address that is only accessible to computers on the internal network. The jump box is then configured to correctly route traffic between the two networks.)

  - **Private Subnet** – Applications Servers / Database servers

  - **Leverage multiple layers of security** – Security groups and Network ACLs to control access to EC2 instances

  - Create hardware VPN connection between your local DC and AWS.

  - AWS gives a maximum of /16 network.

  - Bastion host/ Jump Box in Public subnet

  - Security groups, Network ACLs, Route Tables can span subnets/AZs.

  - Each subnet is always mapped to an availability zone. 1 subnet = 1 AZ

  - **Only one internet gateway per VPC. [Trick question – improve performance by adding Gateway – just not possible]**

  - **Security groups are stateful. Network ACLs are stateless.**

**By default, how many VPCs am I allowed in each AWS Region? == 5**

Typical Private IP address ranges – not publically routable.

  - 10.0.0.0 - 10.255.255.255 (10/8 prefix)

  - 172.16.0.0 - 172.31.255.255 (172.16/12 prefix)

  - 192.168.0.0 - 192.168.255.255 (192.168/16 prefix)

VPC Diagram - Public and Private subnets ![VPC with Public and Private subnets](https://user-images.githubusercontent.com/8856857/62901631-a5778000-bda0-11e9-8563-305d02d0cf4d.jpg)

To use AWS Stencils download them at the [AWS Simple Icons for Architecture Diagrams](https://aws.amazon.com/architecture/icons/) site

## Default v/s Custom VPC

  - **When you create an account a default VPC is created for you in each Region.**

  - All subnets in default VPC have a route out to the internet

  - Each EC2 instance in default VPC will have a public and private IP address

  - If you delete default VPC, only way to restore it is by contacting Amazon.

## Custom VPC Info

  - **Default Security group, network ACL & route table are created for each custom VPC you create.**

  - Doesn’t create subnets or internet gateways out of the box.

  - **In each VPC you create, 5 IP addresses are reserved by AWS for itself. First 4 and last IP in the CIDR block.**

  - **You can't change the size of a VPC after you create it. If your VPC is too small to meet your needs, create a new, larger VPC, and then migrate your instances to the new VPC. To do this, create AMIs from your running instances, and then launch replacement instances in your new, larger VPC. You can then terminate your old instances, and delete your smaller VPC.**

  - You can’t attached multiple Internet Gateways to the VPC to boost performance.

  - When creating VPCs do not modify default route table to add your custom rules. If you modify the default route, it will affect all instances. Create a new route table for customization.

## NAT Instance & NAT Gateway

- **A NAT (Network Address Translation) instance is, like a bastion host, an EC2 instance that lives in your public subnet. A NAT instance, however, allows your private instances outgoing connectivity to the internet while at the same time blocking inbound traffic from the internet.**

  - **NAT Instance** is one EC2 instance. You are responsible for performance management, scale out and security groups. 
  - **NAT Gateway** is a managed service.
  
  ![NAT Instance v/s NAT Gateway](https://user-images.githubusercontent.com/8856857/62902311-9396dc80-bda2-11e9-9934-b6fa181d378d.png)


  - On NAT instance, *remember to disable source/destination IP check*. This is required to allow private subnet internet connectivity. This is not required on NAT Gateway.

  - Allow both HTTP and HTTPS access on security groups associated with NAT instances. Security groups are always associated with NAT Instances.

  - Both *NAT Instance and NAT Gateways are deployed to public subnet*. Elastic IP has to be added to NAT Instance. NAT Gateway is automatically assigned a public IP.

  - In VPC, update default route table to allow connectivity from Private subnet to NAT Instance and Gateway

  - **NAT instance is single point of failure. You can place NAT instance behind Auto Scaling group, multiple subnets in different AZs and scripted failover. To improve performance increase the size of the NAT instance to allow for higher throughput.**

  - You can use Network ACLs to control traffic for both NAT Instance and Gateway.

  - NAT Gateways scale up to 10GBps. No need to disable source/ destination checks on Gateways.

## Network ACLs & Security Groups
|Security Group| Network ACL|
|-------------|-------------| 
|Operates at the instance level (first layer of defense)| Operates at the subnet level (second layer of defense)|
|Supports allow rules only| Supports allow rules and deny rules|
|Is stateful: Return traffic is automatically allowed, regardless of any rules| Is stateless: Return traffic must be explicitly allowed by rules|
|We evaluate all rules before deciding whether to allow traffic| We process rules in number order when deciding whether to allow traffic. Lower order rules take effect in case of conflict with higher order rules.|
|Applies to an instance only if someone specifies the security group when launching the instance, or associates the security group with the instance later on| Automatically applies to all instances in the subnets it's associated with (backup layer of defense, so you don't have to rely on someone specifying the security group)|


  - **With default ACL, all inbound and outbound traffic is allowed automatically**

  - **When custom ACL, all inbound and outbound traffic is denied by default****

  - 1 subnet <=> 1 AZ <=> 1 ACL.  **ACLs can be associated to only 1 subnet at a time**. You can reassign to another subnet. If subnet is not associated with an ACL, the default ACL is applied.

  - AWS Recommends adding ACL rules in increments of 100s

  - **Ephemeral ports** – Allow inbound /outbound traffic from 1024 – 65535. As clients can initiate outbound connection from any random port. **Ports < 1024 reserved for super user access.**

  - **If you have to block a specific IP address / range, use ACLs instead of security groups**
  - **SGs can’t deny traffic – they only allow.**

## Custom VPC & ELB

  - To have HA in general or for ELB, ensure that you have at-least 2 public and or private subnets in different availability zones.

## NAT & Bastion

  - You cannot use NAT instance to SSH / RDP into private subnet. For that Bastion (Jump Box) is required.

  - Bastions are used for secure administrative tasks only. Bastions are placed in Public subnets and connect to private subnets via private IP

  - For Bastion HA, have multiple Bastions in different AZs – at least 2 public subnets. Auto scaling in multiple AZ, route 53 doing health checks.

  - NAT instance is used to provide internet connectivity to private subnets.

## VPC Flow Logs

  - Enable Flow Logs for Custom VPC to see all traffic.

  - Enable to capture IP traffic flow information for the NICs of your resources. All information is reported to CloudWatch

  - Create IAM role to allow all logs to flow into CloudWatch

  - Create log group in CloudWatch and inside that create stream where you can then see all the traffic flow.
