# 🌐 Static & Dynamic Website Deployment on AWS

[← Back to profile](https://github.com/amaraeleoba)

A two-part project demonstrating how to design, deploy, and secure a **3-tier architecture** on AWS — once for a static website and once for a dynamic website. Both projects follow the same presentation / application / data tier pattern, with the data tier changing from S3 (static assets) to RDS (relational database) as the application gains server-side logic.

---

## 📖 Overview

| Project | Purpose | 3 Tiers | GitHub |
|---|---|---|---|
| **1. Static Website** | Highly available static site, no server-side logic | Presentation (ALB) → Application (EC2) → Data (S3) | [/static-website](./static-website) |
| **2. Dynamic Website** | 3-tier web app with a persistent database backend | Presentation (ALB) → Application (EC2) → Data (RDS + S3) | [/dynamic-website](./dynamic-website) |

Both projects use a custom VPC for network isolation and an Application Load Balancer as the presentation tier — the dynamic project adds a private-subnet RDS database as its data tier, on top of S3 for static assets.


---

## 🧩 Project 1: Static Website on AWS

**Stack:** S3 · VPC · EC2 · Application Load Balancer
**GitHub:** [/static-website](./static-website)

Deployed a highly available static website using a 3-tier design: an Application Load Balancer as the presentation tier, EC2 instances across multiple Availability Zones as the application tier, and S3 as the data tier for static asset storage.

**What it demonstrates**
- 3-tier separation of concerns even without a database
- Custom VPC design (subnets, route tables, internet gateway)
- Load balancer target groups & health checks
- Multi-AZ EC2 deployment for fault tolerance
- S3 as the data tier for static asset hosting

**Outcome:** Achieved 99.9%+ uptime by distributing traffic across multiple Availability Zones, removing the single point of failure present in a single-server hosting setup.

---

## 🧩 Project 2: Dynamic Website on AWS

**Stack:** S3 · VPC · RDS · EC2 · Application Load Balancer
**GitHub:** [/dynamic-website](./dynamic-website)

Extended the static architecture into a full 3-tier dynamic web application: an Application Load Balancer (presentation tier), EC2 application servers (application tier), and RDS (data tier) — with public/private subnet separation to keep the database off the public internet.

**What it demonstrates**
- Classic 3-tier architecture (presentation / application / data)
- Public vs. private subnet design
- RDS deployment with restricted security group access (app tier only)
- Secure, least-exposure network design

**Outcome:** Reduced attack surface by isolating the database tier in a private subnet with no direct internet route, while keeping the application layer highly available behind the load balancer.

---

## 🛠️ Tech Stack

`AWS S3` `AWS EC2` `AWS VPC` `AWS RDS` `Application Load Balancer` `IAM`

---

## 📈 Key Outcomes

- Consistent 3-tier architecture pattern applied across both a static and dynamic workload
- Multi-AZ high availability with no single point of failure
- Secure network segmentation (public application tier / private data tier)
- Hands-on VPC, ALB, EC2, RDS, and S3 configuration from the ground up
