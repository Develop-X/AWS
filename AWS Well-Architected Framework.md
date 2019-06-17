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

