# What is Cloud Computing?
 
Cloud Computing is the on-demand delivery of IT resources over the internet with a pay-as-you-go pricing model.
 
Cloud Computing asks you to stop thinking about your infrastructure in terms of hardware and start thinking about your infrastructure in terms of software.
 
---
 
## Cloud Service Models
 
### IaaS (Infrastructure as a Service)
 
Cloud provider gives virtual machines, storage, and networking.
 
**You manage:**
- OS
- Software
- Applications
**Examples:** Amazon EC2, Azure VMs, Google Compute Engine
 
---
 
### PaaS (Platform as a Service)
 
Platform to deploy applications without managing OS.
 
**You manage:**
- Code
- Application
**Cloud manages:**
- OS
- Runtime
- Infrastructure
**Examples:** AWS Elastic Beanstalk
 
---
 
### SaaS (Software as a Service)
 
Ready-to-use software over the internet.
 
**You manage:** Nothing (just use it)
 
**Examples:** Gmail, Zoom, Google Docs
 
---
 
## Big Picture — Who Manages What
 
| Layer            | On-Premises | IaaS         | PaaS         | SaaS         |
|------------------|-------------|--------------|--------------|--------------|
| Applications     | You         | You          | You          | Provider     |
| Data             | You         | You          | You          | Provider     |
| Runtime          | You         | You          | Provider     | Provider     |
| Middleware       | You         | You          | Provider     | Provider     |
| Operating System | You         | You          | Provider     | Provider     |
| Virtualization   | You         | Provider     | Provider     | Provider     |
| Servers          | You         | Provider     | Provider     | Provider     |
| Networking       | You         | Provider     | Provider     | Provider     |
 
**One Line Memory Trick:**
- IaaS = Build everything
- PaaS = Build app only
- SaaS = Just use
---
 
# Technical Jargons
 
## Fault Tolerance vs High Availability
 
### High Availability
 
Maximizing the uptime and minimizing the downtime. The system stays available most of the time, even if failures happen.
 
**Use High Availability for:**
- Websites
- Apps
- E-commerce
### Fault Tolerance
 
System continues working **without any interruption**, even during failure.
 
**Use Fault Tolerance for:**
- Banking
- Military Systems
- Critical Healthcare
---
 
## Reliability vs High Availability
 
### Reliability
 
Ability of a system to perform correctly and consistently over time without failure.
 
**Key Focus:**
- Correctness
- Stability
- Fewer Failures
### High Availability
 
Ability of a system to be accessible with minimal downtime.
 
**Scenario:**
 
**Case 1: Reliable but NOT highly available**
- Single server
- Works perfectly
- But if it crashes → site down
**Case 2: Highly Available but NOT Reliable**
- Multiple servers
- But app has bugs
---
 
## Elasticity vs Scalability
 
**Elasticity = Automatic Scaling**
 
### Scalability
 
Ability of a system to handle the load by adjusting the resources.
 
### Elasticity
 
Ability of a system to automatically adjust the resources based on demand.
 
**Types of Scaling:**
 
| Scaling Type        | Direction  | Description                      |
|---------------------|------------|----------------------------------|
| Horizontal Scaling  | Scale Out  | Add more instances               |
| Horizontal Scaling  | Scale In   | Remove instances                 |
| Vertical Scaling    | Scale Up   | Increase size/power of instance  |
| Vertical Scaling    | Scale Down | Decrease size/power of instance  |
 
---
 
# IAM (Identity and Access Management)
 
**Who has access to What**
 
- **Who:** Entity who makes a call to AWS
- **What:** AWS Resources
- **Access:** Set of permissions (set of actions to perform)
IAM manages two things:
- **Authentication** — verifying who you are
- **Authorization** — what you're allowed to do
---
 
## Demo 1: Create First IAM User in AWS
 
**Who was the first user created when you set up the AWS account?**
 
**Root User** — the original account owner created when you sign up for AWS. Uses your email + password.
 
---
 
## Interfaces to Interact with AWS Services
 
- **AWS Management Console** — User Interface (web browser)
- **AWS CLI** — Command Line Interface
- **AWS SDK** — Software Development Kit (Programming Interface)
- **API** — Application Program Interface
---
 
## IAM Policy
 
A JSON template with the set of instructions defining the actions an entity can perform in an AWS account.
 
**Types of IAM Policies:**
 
**Managed Policy**
- **AWS Managed Policy** — created and maintained by AWS
- **Customer Managed Policy** — created and maintained by you
**Inline Policy (embedded)** — directly embedded into a single user, group, or role
 
---

# Principle of Least Privileges
 
Give only the minimum permissions required to perform a task.
 
**Minimum Access = Maximum Security**
 
---
 
# Customer Managed Policy
 
A policy created and managed by **you (the customer)** in AWS.
 
**Benefits:**
- Reusable across users/roles
- Central control
- Easy updates
**Problems with CMP:**
- Duplicate policies
- Hard to manage
**Example: S3 (Simple Storage Service)**
 
**Case:** User wants to have read access for S3.
 
---
 
# Quiz
 
**Who has unlimited access in AWS?**
- A. IAM User
- B. Admin User
- C. **Root User** ✅
- D. Guest
**Which command takes user input in a shell?**
- A. input
- B. **read** ✅
- C. scan
- D. echo
**Which variable stores the first argument?**
- A. $0
- B. **$1** ✅
- C. $@
- D. $#
**Which service model gives maximum control?**
- A. SaaS
- B. **IaaS** ✅
- C. PaaS
- D. FaaS
**You launched EC2 and installed everything manually — which model?**
- A. SaaS
- B. **IaaS** ✅
- C. PaaS
- D. Hybrid
**What will happen?**
 
```bash
for ((i=1; i<=3; i++))
do
  echo $i
done
```
 
- A. **1 2 3** ✅
- B. 0 1 2
- C. Infinite
- D. Error
 
