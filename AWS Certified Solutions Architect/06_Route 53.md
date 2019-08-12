# Route 53

## DNS 101

DNS = Convert Human Friendly domain names into IP addresses.

**IP4 (32 bit), IP6 (128 bits)** - created to address exhaustion of IP addresses in IP4 space

**VPCs are now IP6 compatible.**

**Top level domains vs second level domains** - In the Domain Name System (DNS) hierarchy, a second-level domain (SLD or 2LD) is a domain that is directly below a top-level domain (TLD). For example, in example.com, example is the second-level domain of the .com TLD.

**Domain Registrars** - assign domain names under one or more top level domain names.

### Types of DNS Records -

1. SOA Record (Start Of Authority)

2. NS Record (Name Server) - AWS is now a Domain Registrar as well. 

3. A Record (Host address) - fundamental 

4. CNAME - Canonical - resolve one domain name to another. Can’t use CNAME for Naked domains.

5. ALIAS record (Auto resolved alias) - only on AWS - are used to map resource record sets in your hosted zone to ELBs, Cloud Front Distribution, or S3 buckets that are configured as websites. E.g. you can have DNS names which point to ELB domain names -w/o the need for changing IP when ELB Ip changes.  Route 53 automatically recognizes changes in the record sets. Most common usage- map naked domain name (zone apex) to ELB names. Always use Alias v/s CNAME as Alias has no charges. Answering CNAME queries has a cost on Route53

6. AAAA Record – Ipv6

* A (Host address)
* AAAA (IPv6 host address)
* ALIAS (Auto resolved alias)
* CNAME (Canonical name for an alias)
* MX (Mail eXchange)
* NS (Name Server)
* PTR (Pointer)
* SOA (Start Of Authority)
* SRV (location of service)
* TXT (Descriptive text)

**TTL - Cache the DNS record for TTL seconds. Before DNS migration, shorten the TTLs - so no more responses are cached. **

### Hosted Zone

Collection of resource record sets. NS, SOA, CNAME, Alias etc. types of records for a particular domain.

e.g. [https://www.tcpiputils.com/dns-lookup/google.com/ALL](https://www.tcpiputils.com/dns-lookup/google.com/ALL)

## Route53 Routing Policies

Most of the questions are scenario based.

1. **Simple - Default** - when a single resource performs function for your domain - only one webserver serves content

2. **Weighted** – send x% of traffic to site A and remainder (100 – x) % of it to site B. Need not be two different regions. Can be even two different ELBs.  This split is over length of day not based on number of individual subsequent requests.

Weights – a number between 0 and 255. Route53 calculates auto %age

AWS Takes Global view of DNS – not local / ISP view.

**A/B testing is perfect use case for Weighted Routing policy**

3. **Latency** – allows you to route traffic based on lowest network latency for your end user. To the region which gives fastest response time

Create record set for EC2 or ELB resource in each region that hosts website. When R53 receives a query it will then determine response based on lowest latency

How will the users get the best experience?  – evaluated dynamically by R3.

4. **Failover** – When you want to create an active / passive setup. DR site. R53 monitors health of site. If active fails then R53 routes traffic to passive site.   Here you designate a primary and secondary endpoint for your hosted zone record.

5. **Geo-location** – Choose where to route traffic based on geographic location of users.

Different from Latency based as the routing is hardwired irrespective of latency.

6. **Geoproximity routing policy** – Use when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another. ... 

## DNS Exam Tips

  - **ELBs cost money – ensure to delete them when not using.**

  - **ELBs always have DNS name – no public IP Addresses.** Trick question might induce you into believing IP4 address for ELB

  - Remember difference between Alias and CNAME

  - **Given a choice between Alias Record vs CNAME – always choose Alias. Alias records are free and can connect to AWS resources.**

  - R53 supports zone apex records

  - **With Route 53, there is a default limit of 50 domain names. However, this limit can be increased by contacting AWS support.**

  - **Naked domain – which doesn’t have the www in front of the domain e.g. acloud.guru. [www.acloud.guru](http://www.acloud.guru) isn’t**

****
