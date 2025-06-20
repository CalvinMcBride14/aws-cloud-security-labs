# 🌐 Public Subnet Configuration

This project demonstrates how to manually convert **private subnets into public subnets** within a custom VPC in AWS, enabling instances launched within them to communicate with the public internet.

This builds upon a previously created VPC architecture for **Amazon for Life**, featuring a multi-tier design spread across three Availability Zones (AZs), with this project specifically configuring the **Web tier subnets (Web-A, Web-B, Web-C)** for internet access.

---

## AWS Services Involved

- Amazon VPC  
- Internet Gateway  
- Route Tables  
- EC2 Bastion Host (for testing)  
- IPv4 / IPv6 Routing  
- Security Groups  

---

## Architecture Overview

- **VPC CIDR**: `10.16.0.0/16` (IPv4), AWS-provided `/56` (IPv6)
- **Subnets Involved**: `SN-WEB-A`, `SN-WEB-B`, `SN-WEB-C`
- **Goal**: Make Web subnets publicly accessible

---

## Configuration Steps

### 1. Create and Attach an Internet Gateway
- Named `a4l-vpc1-igw`
- Attached to the `A4L-VPC1` custom VPC

### 2. Create a Public Route Table
- Named `A4L-VPC1-RT-Web`
- Associated with the three Web subnets (A, B, C)

### 3. Add Default Routes
- `0.0.0.0/0 → IGW` (IPv4)
- `::/0 → IGW` (IPv6)
- This enables internet-bound traffic from Web subnets

### 4. Modify Web Subnet Settings
Enabled the following for **each Web subnet**:
- ✅ Auto-assign Public IPv4 address
- ✅ Auto-assign IPv6 address

---

## Test the Configuration

### Launch a Bastion EC2 Instance:
- **Instance Name**: `A4L-Bastion`
- **AMI**: Amazon Linux (Free Tier eligible)
- **Instance Type**: `t2.micro`
- **Subnet**: `SN-WEB-A`
- **Public IP**: Auto-assigned
- **Security Group**: `A4L-Bastion-SG` (Allow SSH from anywhere)

### Verify:
- Instance receives both public/private IPv4 addresses
- Instance is reachable via:
  - ✅ EC2 Instance Connect
  - ✅ SSH from local terminal (using downloaded PEM key)

---

##  Tear Down / Cleanup Steps

To avoid charges and reset the environment I:
1. Terminated the Bastion EC2 instance
2. Deleted the `A4L-VPC1` VPC  
   > This also deletes associated subnets, route tables, and the IGW

---

## 📸 Screenshots

Screenshots of each configuration step — including IGW setup, route table creation, and EC2 connectivity — are available in the [`/screenshots`](./screenshots) folder.

---

## What I Learned

- How to configure **internet access** in AWS using an Internet Gateway and routing
- The difference between **local vs. default routes** in a VPC
- The necessity of **public IP allocation settings** for true external connectivity
- How to **launch and connect** to EC2 instances in public subnets using both EC2 Instance Connect and SSH

---

> ✅ This project reflects **real-world, production-relevant AWS networking tasks**, all implemented manually to solidify core cloud fundamentals.
