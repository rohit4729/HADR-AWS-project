# 🌐 HADR Project on AWS

## 📌 Overview
The **HADR Project** (High Availability and Disaster Recovery) is designed to demonstrate a highly available, fault-tolerant, and resilient architecture for hosting a website using **Amazon Web Services (AWS)**.  
The setup ensures minimal downtime and efficient failover between two AWS regions — **Mumbai** (Primary) and **Virginia** (Secondary).

---

## 🏗 Architecture & Implementation

### 1️⃣ VPC Creation
- Created a **Virtual Private Cloud (VPC)** with:
  - **Public Subnet** (Internet-accessible)
  - **Private Subnet** (Internal workloads)
- Added a **NAT Gateway** in the public subnet to allow outbound internet access from the private subnet.

### 2️⃣ EC2 Instances
- Launched **two EC2 instances**:
  - **Public Subnet Instance** – Accessible over the internet.
  - **Private Subnet Instance** – Accessed via SSH tunneling through the public instance.
  
### 3️⃣ Website Deployment
- Deployed the **website** on the **private instance**.
- Configured **NGINX** on the **public instance** (Ubuntu) as a reverse proxy to serve website content.
- Modified the NGINX server block to allow access via the public IP.

### 4️⃣ NAT Gateway Removal
- After setup completion, removed the **NAT Gateway** to optimize costs.

### 5️⃣ AMI & Launch Template
- Created an **Amazon Machine Image (AMI)** of the public instance.
- Built a **Launch Template** using this AMI.

### 6️⃣ Auto Scaling Group (ASG)
- Created an **Auto Scaling Group** from the launch template.
- Attached the ASG to an **Application Load Balancer (ALB)** for efficient load distribution.

### 7️⃣ Replication in Secondary Region
- Replicated the **entire infrastructure** in the **US-East (Virginia)** region for disaster recovery.

### 8️⃣ DNS Configuration
- Created a **Hosted Zone** in Route 53.
- Added **CNAME records** with **Failover Routing Policy**:
  - **Primary:** Mumbai infrastructure
  - **Secondary:** Virginia infrastructure

---
🚀 Key AWS Services Used

   1. Amazon VPC
      
   2. Amazon EC2
      
   3.Amazon Machine Image (AMI)
   
   4.Launch Templates
   
   5.Auto Scaling Groups (ASG)
   
   6.Application Load Balancer (ALB)
   
   7.Amazon Route 53
   
   8.NAT Gateway
   
   9.NGINX (on Ubuntu)

## 📊 Architecture Diagram
*(Insert your architecture diagram image here)*  
Example:  
```markdown
![AWS HADR Architecture](path/to/diagram.png)
