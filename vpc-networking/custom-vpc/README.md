#  Custom VPC Deployment – Animals for Life (A4L)

This project demonstrates the creation of a **custom Virtual Private Cloud (VPC)** in AWS as the foundational step in building a secure, multi-tier cloud architecture.
It’s part of a broader architecture called “Animals for Life,” and serves as the networking baseline for future components such as subnets, internet gateways, and route tables.

This lab was completed hands-on using the AWS Management Console in the **us-east-1 (N. Virginia)** region.

---

##  Services Used

- **Amazon VPC**
- **IPv4 / IPv6 CIDR Allocation**
- **AWS DNS Settings**
- **IAM (Admin user)**

---

##  What Was Configured

### VPC Creation
- **VPC Name**: `A4L-VPC1`
- **IPv4 CIDR**: `10.16.0.0/16` (defined in IP plan)
- **IPv6 CIDR**: AWS-provided `/56` block
- **Tenancy**: Default

Used the “VPC only” option in the AWS VPC creation wizard to create a clean, minimal VPC for custom infrastructure layering.

---

### DNS Settings Adjusted
- ✅ **Enabled DNS Resolution** *(default: enabled)*
- ✅ **Enabled DNS Hostnames** *(default: disabled — enabled manually)*

This ensures that any instances launched within this VPC and assigned public IPs will also receive **public DNS names**, making it easier to manage and troubleshoot later.

---

## Current Architecture

At the end of this initial setup, the VPC is:

- Created with both **IPv4 and IPv6 support**
- Not yet populated with subnets or gateways
- Ready for further configuration (e.g. IGW, routing, NAT)

This clean starting point allows full control over custom subnet layout and production-grade architecture.

---

## 🖼️ Screenshots

Visual proof of work is stored in the (./screenshots) folder, including:

- VPC configuration
- DNS settings
- CIDR allocation

---

##  What I Learned

- How to manually create a custom VPC using AWS best practices
- The importance of enabling DNS hostname resolution in custom VPCs
- How to allocate and interpret IPv6 CIDR blocks from AWS
- Why starting with a minimal VPC helps enforce clean network design

---

##  What’s Next

This project is the first of a multi-part networking build-out. In the next stages, I’ll be:

- Creating **public and private subnets**
- Attaching an **Internet Gateway**
- Defining **route tables**
- Preparing this VPC for application and service deployment

Stay tuned as this repo will evolve into a full cloud-native networking stack.
