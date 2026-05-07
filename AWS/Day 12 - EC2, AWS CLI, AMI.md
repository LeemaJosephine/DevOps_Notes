# EC2 (Elastic Compute Cloud)
 
Virtual server in the cloud. Used to run applications, websites, and databases.
 
## EC2 Analogy — Renting a House
 
| EC2 Concept        | Analogy              | Description                                      |
|--------------------|----------------------|--------------------------------------------------|
| **AMI**            | House Blueprint      | Template used to create EC2 — OS + preinstalled software |
| **Instance Type**  | House Size           | Defines specifications like CPU, RAM, performance |
| **EBS**            | Furniture/Closet     | Persistent storage attached to EC2 — stores files, OS, data |
| **Security Group** | Security Guard       | Controls inbound/outbound traffic                |
| **Key Pair**       | House Key            | Used to log in securely via SSH                  |
| **VPC**            | Colony/Society       | Network where EC2 runs                           |
 
### Security Group
 
Controls inbound/outbound traffic:
- Allow port 22: SSH
- Allow port 80: HTTP
### Key Pair
 
- `.pem` file
- Used with SSH
### VPC (Virtual Private Cloud)
 
- Private network
- Subnet
---
 
## Demo 1: Launch EC2 and Install Apache HTTP Server
 
Test the web page using EC2 public IP.
 
**Installation commands:**
 
```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl status apache2
```
 
---
 
# EC2 User Data
 
User data is a script that runs automatically when an EC2 instance starts (boot time).
 
**Key idea:**
 
```
Launch EC2 → Script runs automatically → Instance gets configured
```
 
**Why Use User Data? — Automate setup:**
- Install software
- Configure server
- Deploy app
---
 
# EC2 Instance Metadata
 
## What is EC2 Metadata?
 
**Metadata** = information about your EC2 instance, accessible from inside the instance.
 
```
Instance → asks itself → gets its own details
```
 
**What information you can get:**
- Instance ID
- Public IP
- Private IP
- AMI ID
- Security groups
- Region
---
 
## Hands-on Demo
 
### Step 1: Connect to EC2
 
SSH into your EC2 instance using your key pair.
 
### Step 2: Get Token
 
```bash
TOKEN=$(curl -X PUT "http://169.254.169.254/latest/api/token" \
  -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")
```
 
### Step 3: Access Metadata Service
 
```bash
curl -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/
```
 
### Step 4: Get Specific Value — Instance ID
 
```bash
curl -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/instance-id
```
 
---
 
# AWS CLI (Command Line Interface)
 
## What is AWS CLI?
 
A tool to manage AWS services using terminal/command line.
 
## Why AWS CLI is Important
 
**Automation:**
- Scripts
- CI/CD pipelines
**Faster than UI:**
- No clicking
- Direct execution
**Check if CLI is installed:**
 
```bash
aws --version
```
 
---
 
## Demo: Create an S3 Bucket Using AWS CLI
 
```bash
aws s3 mb s3://<bucket-name>
```
