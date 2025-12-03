# *Secure EC2 Hosting in a Custom VPC with IAM Roles, S3 Logging & CloudWatch Monitoring*

This project demonstrates how to deploy a *highly secure, production-ready EC2 environment* inside a custom VPC using a bastion host, strict security groups, IAM roles, S3 logging, and CloudWatch monitoring — all built *100% through the AWS Management Console*.

---

## 🚀 *Project Purpose*

Design and deploy a secure compute environment on AWS using EC2 instances in both public and private subnets, ensuring:

* No public exposure of application servers
* Controlled SSH access via bastion host
* Secure routing using IGW + NAT
* S3-based logging
* CloudWatch monitoring and alarms
  (From page 1 of the project PDF )

---

## 📌 *Architecture Diagram*

md
![EC2 Architecture](secure-ec2-deployment/Architecture_Diagram.png)


---

# ⭐ *Key Features*

### *🌐 Custom VPC Design*

* VPC CIDR: 10.0.0.0/16
* Public Subnet: 10.0.1.0/24
* Private Subnet: 10.0.2.0/24
* Internet Gateway for public subnet
* NAT Gateway for outbound access from private subnet
  (Page 1–2 of PDF )

---

### *🛡️ Secure EC2 Deployment*

*Bastion Host (Public Subnet)*

* Used for SSH access into private EC2
* SSH allowed only from *your IP*
  (Page 3 )

*Application Server (Private Subnet)*

* No public IP
* SSH allowed only from bastion security group
* Outbound allowed for updates & logs
  (Page 3–4 )

---

### *🔒 IAM Security*

A dedicated EC2 IAM role is created to:

* Upload system logs to S3
* Send metrics to CloudWatch
  Role name: EC2-logging-role
  (Page 4 )

---

### *📂 S3 Logging Setup*

S3 bucket: app-logs-secure

* Block Public Access
* Versioning enabled
* SSE-S3 encryption enabled
  (Page 5 )

---

### *📊 CloudWatch Monitoring*

Monitored metrics:

* CPU Utilization
* Disk usage
* Network In/Out
* Memory metrics (via CloudWatch Agent)

CloudWatch Alarms:

* CPU > 80%
* Disk space low
* System status check failed
  (Page 5–6 )

---

### *🔐 Security Hardening*

* SSH allowed only via bastion
* No public IP for private EC2
* MFA enabled on IAM
* S3 public access blocked
  (Page 6 )

---

# 🧩 *AWS Services Used*

* Amazon EC2
* Amazon VPC
* Internet Gateway (IGW)
* NAT Gateway
* Amazon S3
* IAM Roles
* Amazon CloudWatch
* CloudWatch Agent
* Security Groups

---

# 📂 *Project Structure*


.
├── README.md
├── secure-ec2-deployment/
│   ├── Secure EC2 Deployment in AWS.pdf
│   └── Architecture_Diagram.png


---

# 🛠️ *High-Level Steps*

### *1. Create VPC*

* VPC + public and private subnets
* IGW + NAT setup
  (Page 1–2)

### *2. Deploy Bastion Host (Public Subnet)*

* SSH access only from your IP
  (Page 3)

### *3. Deploy Application EC2 (Private Subnet)*

* Accessible only via bastion
  (Page 3–4)

### *4. Configure IAM Role for Logging*

(Page 4)

### *5. Enable S3 Logging Bucket*

(Page 5)

### *6. Install CloudWatch Agent & Setup Alarms*

(Page 5–6)

---

# 🎯 *What I Learned*

* Building secure compute architectures
* Private vs public subnet design
* Secure SSH tunneling using bastion
* IAM role-based security
* CloudWatch observability
* S3 log storage
* VPC routing fundamentals

---

# 🧹 *Cleanup*

* Terminate EC2 instances
* Delete NAT Gateway (charges!)
* Delete S3 logging bucket
* Remove role & policies
* Delete VPC & networking components
