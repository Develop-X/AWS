# Important links to review
Review Exam [Blueprint](http://awstrainingandcertification.s3.amazonaws.com/production/AWS_certified_solutions_architect_associate_blueprint.pdf)

AWS [Cheat Sheets](https://tutorialsdojo.com/aws-cheat-sheets/)


## Tiers

 - Practitioner - Certified Cloud Practioner
 - Assosciate - Certified Solutions Architect Assosciate | Certified Developer Assosciate | Certified Sysops administrator assosciate
 - Professional - Certified Solutions Architect Professional | Devops Professional
 - Speciality - Big Data | Machine Learning | Security | Advanced Networking

## Exam Blueprint

The table below lists the domains measured by this examination and the extent to which they are represented

|Domain | % of Examination|
|------------- |:-------------:|
|1.0 Designing highly available, cost efficient, fault tolerant, scalable systems |60% |
|2.0 Implementation/Deployment |10% |
|3.0 Data Security| 20% |
|4.0 Troubleshooting |10% |
|**Total**|100%|

The exam is approximately 60 questions in 80 minutes. Pass marks not advertised but generally > 70%

**CROPS - Cost Optimized | Resilient | Operational Excellent | Performant | Secure |

```Domain 1```
## Design Resilient Architecture 34%
```Domain 2```
## Define Performant Architecture 24%
```Domain 3```
## Specify Secure applications and architecture 26%
```Domain 4```
## Design Cost Optimized architectures 10%
```Domain 5```
## Define Operational Excellent architectures 6%

- 65 questions 130 minutes


### Design Resilient Architecture

- ``` Choose resilient/reliable storage```
- ``` Determine how to design decoupling mechanism using AWS services```
- ``` Determine how to design multi tier architecture```
- ``` Determine how to design hig availability / fault tolerant systems.```

#### EC2 Instance Store
- Ephemeral Volumes ( are lost when terminates/stops)
- Only certain EC2 instances have instance stores
- Fixed Capacity (size is fixed)
- Disk type and capacity depends on EC2 instance type (SSD or HDD depends on instance type and so is capacity)
- Application level durability
- Used for caching or storing other temporary data for fast access that can be replicated else where 

#### EBS (Elastic Block Storage
- Different types
- Encryption
- Snapshot
- Provisioned Capacity
- Indepndent lifecycle than EC2 instance
- Multiple volumes striped to create large volumes


