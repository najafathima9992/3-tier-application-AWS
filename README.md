# CloudCore AWS Project 🚀

## 📌 Overview

Designed and deployed a scalable cloud architecture using AWS services including VPC, EC2, Auto Scaling, ALB, RDS, CloudWatch, SNS, and Lambda.

## 🛠️ Services Used

* VPC (Public & Private Subnets)
* EC2 with Launch Template
* Auto Scaling Group
* Application Load Balancer
* RDS (MySQL)
* CloudWatch (Monitoring & Alerts)
* SNS (Notifications)
* Lambda (Auto-healing)

## ⚙️ Architecture Highlights

* Secure 3-tier architecture
* Private subnet for EC2 & RDS
* Bastion host for SSH access
* Auto scaling for high availability
* ALB for traffic distribution

## 📊 Features

* Auto-recovery using Lambda
* Monitoring with custom metrics
* Email alerts via SNS
* High availability & fault tolerance

#Explanation

  1. Networking Layer (VPC Setup)

created a custom VPC (10.0.0.0/16)

Components:
Public Subnets
Used for:
Bastion Host
Application Load Balancer
Private Subnets
Used for:
EC2 instances (application)
RDS database
Key Elements:
Internet Gateway
→ Allows public internet access
NAT Gateway
→ Allows private EC2 to access internet (for updates)


🔹 2. Compute Layer (EC2 + Bastion Host)
🔸 Bastion Host
Placed in public subnet
Used to SSH into private EC2
🔸 EC2 Instances
Hosted in private subnet
Installed Apache (httpd) using user data
No direct public access (security best practice)


🔹 3. Auto Scaling (High Availability)
Created Auto Scaling Group
Min: 1 | Desired: 2 | Max: 3
Why?
Automatically adds/removes servers based on load


🔹 4. Load Balancer (Traffic Distribution)
Application Load Balancer
Placed in public subnet
Distributes incoming HTTP traffic
Flow:
User → ALB → Target Group → EC2 Instances

👉 Benefits:

Load distribution
Fault tolerance
Zero downtime

🔹 5. Database Layer (RDS)
Amazon RDS (MySQL)
Placed in private subnet
Only EC2 can access DB

👉 🔥 Security:

No public access
Controlled via Security Groups

🔹 6. Monitoring & Alerts
Amazon CloudWatch

You configured:

CPU > 70%
ALB 5XX errors
RDS storage alerts
Custom Metrics:
Memory usage
Disk usage

👉 This shows advanced monitoring skills 👏

🔹 7. Notifications (SNS)
Amazon SNS
Sends email alerts when thresholds are crossed

👉 Example:

High CPU → Email alert
🔹 8. Auto-Healing (Lambda)
AWS Lambda
Triggered by CloudWatch alarm
Automatically:
→ Reboots unhealthy EC2 instances



🔄 Complete Flow (End-to-End)
User hits ALB URL
ALB routes traffic to EC2
EC2 processes request
EC2 interacts with RDS
CloudWatch monitors everything
If issue:
SNS sends alert
Lambda fixes it automatically

## 🌐 Outcome

Healthy Application
