# 🧱 Multi-Tier Subnet Design

This project demonstrates the **manual creation of a multi-tier subnet structure** across three Availability Zones within a custom VPC in AWS. It forms the network backbone for a scalable application environment following best practices for tiered infrastructure.

All subnets were configured manually in the AWS Console as part of a hands-on lab to reinforce deep understanding of subnet planning, IPv6 allocation, and VPC zoning.

---

##  Services & Features Used

- **Amazon VPC**
- **Subnets**
- **IPv4 / IPv6 Allocation**
- **Availability Zones (AZs)**
- **Auto-assign IPv6 Addresses**

---

## Subnet Design Overview

Subnets were created for **four tiers** in **three AZs** (A, B, and C):

- **Reserved**
- **Database**
- **Application**
- **Web**

✅ **12 total subnets**, 4 per AZ.

Each subnet was manually configured with:
- A unique **IPv4 CIDR block** (per the IP plan)
- A distinct **IPv6 /64 block**, segmented from the VPC’s allocated /56 range
- Proper **availability zone assignment**
- **Auto-assign IPv6** enabled

---

## Subnet Naming Convention

| Tier       | AZ A        | AZ B        | AZ C        |
|------------|-------------|-------------|-------------|
| Reserved   | SN-RES-A    | SN-RES-B    | SN-RES-C    |
| Database   | SN-DB-A     | SN-DB-B     | SN-DB-C     |
| App Tier   | SN-APP-A    | SN-APP-B    | SN-APP-C    |
| Web Tier   | SN-WEB-A    | SN-WEB-B    | SN-WEB-C    |

---

## Key Configuration Highlights

- **Manual IPv4 entry** for each subnet (e.g., 10.16.x.x/24 format)
- **Manual IPv6 segmentation**:
  - VPC provided a /56 IPv6 CIDR block
  - Subnets carved into /64 blocks using AWS subnetting tool
  - Unique hexadecimal index (`::00`, `::01`, etc.) used per subnet
- **Used subnet wizard** to create 4 subnets at a time per AZ
- **Enabled Auto-Assign IPv6** for all subnets

---

## 🖼️ Screenshots

Screenshots for each step — subnet creation, IPv6 range allocation, and configuration — are available in the [`/screenshots`](./screenshots) folder.

---

## What I Learned

- How to plan and configure a **multi-tier network layout** in AWS manually
- How **IPv6 subnetting works** in combination with AWS's auto-allocated /56 block
- Why enabling **auto-assign IPv6 addresses** is important for modern networking
- The value of understanding **manual network setup before automating it**

---

## What’s Next

This project is part of a broader architecture for the **Animals for Life** environment. The next stages will include:

- Attaching an **Internet Gateway**
- Creating and associating **Route Tables**
- Building NAT configurations and Security Groups
- Automating future deployments with CloudFormation or Terraform

