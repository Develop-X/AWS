# AWS Well-Architected Framework

* The AWS Well-Architected Framework helps you understand the pros and cons of decisions you make while building systems on AWS
* Architectural best practices for designing and operating reliable, secure, eﬃcient, and cost-eﬀective systems in the cloud
* This framework is intended for those in technology roles, such as chief technology oﬃcers (CTOs), architects, developers, and operations team members

* **The AWS Well-Architected Framework is based on ﬁve pillars — operational excellence, security, reliability, performance eﬃciency, and cost optimization.**

## The pillars of the AWS Well-Architected Framework [OSRPC]

* **Operational Excellence** The ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures. 
* **Security** The ability to protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies. 
* **Reliability** The ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconﬁgurations or transient network issues. 
* **Performance Eﬃciency** The ability to use computing resources eﬃciently to meet system requirements, and to maintain that eﬃciency as demand changes and technologies evolve.
* **Cost Optimization** The ability to run systems to deliver business value at the lowest price point.

## AWS Well-Architected Framework uses these terms:

* A **component** is the code, conﬁguration and AWS Resources that together deliver against a requirement. A component is often the unit of technical ownership, and is decoupled from other components. 
* We use the term **workload** to identify a set of components that together deliver business value. The workload is usually the level of detail that business and technology leaders communicate about.
* **Milestones** mark key changes in your architecture as it evolves throughout the product lifecycle (design, testing, go live, and in production).
* We think about **architecture** as being how components work together in a workload. How components communicate and interact is often the focus of architecture diagrams. 
* Within an organization the **technology portfolio** is the collection of workloads that are required for the business to operate.

## On Architecture
* In on-premises environments customers often have a **central team** for technology architecture that acts as an overlay to other product or feature teams to ensure they are following best practice. Technology architecture teams are often composed of a set of roles such as **Technical Architect (infrastructure), Solutions Architect (software), Data Architect, Networking Architect, and Security Architect**. Often these teams use **TOGAF or the Zachman Framework** as part of an enterprise architecture capability.

* At AWS, we prefer to **distribute capabilities** into teams rather than having a centralized team with that capability. There are **risks when you choose to distribute decision making authority**, for example, ensuring that teams are meeting internal standards. We mitigate these risks in two ways. 
  * First, we have **practices** that focus on enabling each team to have that capability, and we put in place experts who ensure that teams raise the bar on the standards they need to meet. 
  * Second, we implement **mechanisms** that carry out automated checks to ensure standards are being met. This distributed approach is supported by the **Amazon leadership principles**, and establishes a culture across all roles that works back from the customer. **Customerobsessed teams** build products in response to a customer need.
* For architecture this means that we expect every team to have the capability to create architectures and to follow best practices. To help new teams gain these capabilities or existing teams to raise their bar, we enable access to a **virtual community of principal engineers** who can review their designs and help them understand what AWS best practices are. The **principal engineering community** works to make best practices visible and accessible. One way they do this, for example, is through lunchtime talks that focus on applying best practices to real examples. These talks are recorded and can be used as part of onboarding materials for new team members.
* AWS best practices emerge from our experience running thousands of systems at internet scale. We prefer to use data to deﬁne best practice, but we also use **subject matter experts like principal engineers to set them**. **As principal engineers see new best practices emerge they work as a community to ensure that teams follow them**. In time, these best practices are formalized into our **internal review processes**, as well as into mechanisms that enforce compliance. Well-Architected is the customerfacing implementation of our internal review process, where we have codiﬁed our principal engineering thinking across ﬁeld roles like Solutions Architecture and internal engineering teams. Well-Architected is a scalable mechanism that lets you take advantage of these learnings.

* **“Good intentions never work, you need good mechanisms to make anything happen” Jeﬀ Bezos. This means replacing humans best eﬀorts with mechanisms (often automated) that check for compliance with rules or process.**
* **Working backward is a fundamental part of our innovation process. We start with the customer and what they want, and let that deﬁne and guide our eﬀorts.**

## General Design Principles

*  **Stop guessing your capacity needs**: Eliminate guessing about your infrastructure capacity needs. When you make a capacity decision before you deploy a system, you might end up sitting on expensive idle resources or dealing with the performance implications of limited capacity. With cloud computing, these problems can go away. You can use as much or as little capacity as you need, and scale up and down automatically. 
* **Test systems at production scale**: In the cloud, you can create a production-scale test environment on demand, complete your testing, and then decommission the resources. Because you only pay for the test environment when it's running, you can simulate your live environment for a fraction of the cost of testing on premises. 
* **Automate to make architectural experimentation easier**: Automation allows you to create and replicate your systems at low cost and avoid the expense of manual eﬀort. You can track changes to your automation, audit the impact, and revert to previous parameters when necessary. 
* **Allow for evolutionary architectures**: Allow for evolutionary architectures. In a traditional environment, architectural decisions are often implemented as static, one-time events, with a few major versions of a system during its lifetime. As a business and its context continue to change, these initial decisions might hinder the system's ability to deliver changing business requirements. In the cloud, the capability to automate and test on demand lowers the risk of impact from design changes. This allows systems to evolve over time so that businesses can take advantage of innovations as a standard practice.
* **Drive architectures using data**: In the cloud you can collect data on how your architectural choices aﬀect the behavior of your workload. This lets you make fact-based decisions on how to improve your workload. Your cloud infrastructure is code, so you can use that data to inform your architecture choices and improvements over time. 
* **Improve through game days**: Test how your architecture and processes perform by regularly scheduling game days to simulate events in production. This will help you understand where improvements can be made and can help develop organizational experience in dealing with events.

# The Five Pillars of the Framework
## Operational Excellence 
* The Operational Excellence pillar includes the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures. The operational excellence pillar provides an overview of design principles, best practices, and questions
### Design Principles 
* There are six design principles for operational excellence in the cloud: 
  * **Perform operations as code**: In the cloud, you can apply the same engineering discipline that you use for application code to your entire environment. You can deﬁne your entire workload (applications, infrastructure) as code and update it with code. You can implement your operations procedures as code and automate their execution by triggering them in response to events. By performing operations as code, you limit human error and enable consistent responses to events. 
  * **Annotate documentation**: In an on-premises environment, documentation is created by hand, used by people, and hard to keep in sync with the pace of change. In the cloud, you can automate the creation of annotated documentation after every build (or automatically annotate hand-crafted documentation). Annotated documentation can be used by people and systems. Use annotations as an input to your operations code. 
  * **Make frequent, small, reversible changes**: Design workloads to allow components to be updated regularly. Make changes in small increments that can be reversed if they fail (without aﬀecting customers when possible). 
  * **Reﬁne operations procedures frequently**: As you use operations procedures, look for opportunities to improve them. As you evolve your workload, evolve your procedures appropriately. Set up regular game days to review and validate that all procedures are eﬀective and that teams are familiar with them. 
  * **Anticipate failure**: Perform “pre-mortem” exercises to identify potential sources of failure so that they can be removed or mitigated. Test your failure scenarios and validate your understanding of their impact. Test your response procedures to ensure that they are eﬀective, and that teams are familiar with their execution. Set up regular game days to test workloads and team responses to simulated events.
  * **Learn from all operational failures**: Drive improvement through lessons learned from all operational events and failures. Share what is learned across teams and through the entire organization.  

### Best Practices 
* **Prepare** Eﬀective preparation is required to drive operational excellence. Business success is enabled by shared goals and understanding across the business, development, and operations. Common standards simplify workload design and management, enabling operational success. **Design workloads with mechanisms to monitor and gain insight into application, platform, and infrastructure components, as well as customer experience and behavior**.
Create mechanisms to validate that workloads, or changes, are ready to be moved into production and supported by operations. Operational readiness is validated through checklists to ensure a workload meets deﬁned standards and that required procedures are adequately captured in **runbooks and playbooks**. Validate that there are suﬃcient trained personnel to eﬀectively support the workload. Prior to transition, test responses to operational events and failures. Practice responses in supported environments through failure injection and game day events. 
AWS enables operations as code in the cloud and the ability to safely experiment, develop operations procedures, and practice failure. Using **AWS CloudFormation enables you to have consistent, templated, sandbox development, test, and production environments with increasing levels of operations control**. AWS enables visibility into your workloads at all layers through various log collection and monitoring features. **Data on use of resources, application programming interfaces (APIs), and network ﬂow logs can be collected using Amazon CloudWatch, AWS CloudTrail, and VPC Flow Logs.** You can use the collectd plugin, or the CloudWatch Logs agent, to aggregate information about the operating system into CloudWatch.
The following questions focus on these considerations for operational excellence.:
  * **OPS 1:  How do you determine what your priorities are?** Everyone needs to understand their part in enabling business success. Have shared goals in order to set priorities for resources. This will maximize the beneﬁts of your eﬀorts. 
  * **OPS 2:  How do you design your workload so that you can understand its state?** Design your workload so that it provides the information necessary for you to understand its internal state (for example, metrics, logs, and traces) across all components. This enables you to provide eﬀective responses when appropriate. 
  * **OPS 3:  How do you reduce defects, ease remediation, and improve ﬂow into production?** Adopt approaches that improve ﬂow of changes into production, that enable refactoring, fast feedback on quality, and bug ﬁxing. These accelerate beneﬁcial changes entering production, limit issues deployed, and enable rapid identiﬁcation and remediation of issues introduced through deployment activities.
  * **OPS 4:  How do you mitigate deployment risks?** Adopt approaches that provide fast feedback on quality and enable rapid recovery from changes that do not have desired outcomes. Using these practices mitigates the impact of issues introduced through the deployment of changes. 
  * **OPS 5:  How do you know that you are ready to support a workload?** Evaluate the operational readiness of your workload, processes and procedures, and personnel to understand the operational risks related to your workload.



