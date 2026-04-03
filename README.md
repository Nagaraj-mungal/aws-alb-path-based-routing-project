# 🚀 Application Load Balancer with Path-Based Routing (AWS)

## 📌 Project Overview

This project demonstrates how to design and implement a real-time, highly available web architecture using AWS Application Load Balancer (ALB) with path-based routing.
The goal is to host multiple applications behind a single Load Balancer and route traffic intelligently based on URL paths instead of exposing multiple public IP addresses.

---

## 🏢 Real-Time Scenario

In production environments, companies host multiple applications under one domain:

- example.com/gmail  
- example.com/drive  

Instead of managing separate servers and URLs, an Application Load Balancer is used to:

- Accept incoming user requests  
- Inspect the request path  
- Route traffic to the correct backend server  

In this project:

- `/gmail` → Gmail Application (EC2 Instance 1)  
- `/drive` → Drive Application (EC2 Instance 2)  

---

## ☁️ Services Used

- AWS EC2 (Elastic Compute Cloud)  
- Application Load Balancer (ALB)  
- Target Groups  
- Security Groups  

---

## 🛠️ Technologies Used

- Apache (httpd)  
- Git  
- Linux (Amazon Linux)  

---

## 🏗️ Architecture

User → Application Load Balancer → Target Groups → EC2 Instances  

- ALB works at Layer 7 (HTTP/HTTPS)  
- Routes traffic based on path  
- Performs health checks on instances  

---

## 🖥️ Implementation Steps

### 1️⃣ Launch EC2 Instances

Create two EC2 instances:

- Gmail Server  
- Drive Server  

Configure Security Group:
- Allow SSH (Port 22)  
- Allow HTTP (Port 80)  

---

### 2️⃣ Install Apache & Git

Run on both servers:
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
sudo yum install git -y

---

### 3️⃣ Deploy Applications

cd /var/www/html

# Gmail Application
git clone https://github.com/CloudNinjaa/gmail-main-page-template
mv gmail-main-page-template gmail

# Drive Application
git clone https://github.com/akshay-mudda/Google-Drive-Clone
mv Google-Drive-Clone drive

# Set permissions
sudo chown -R apache:apache /var/www/html

---

### 4️⃣ Verify Applications

Open in browser:
http://EC2-PublicIP/gmail⁠�
http://EC2-PublicIP/drive⁠�
Both applications should load successfully.

---

### 5️⃣ Create Target Groups

Create two target groups:
Gmail Target Group
Name: Gmail-target-grp
Health Check Path: /gmail/index.html
Drive Target Group
Name: drive-target-grp
Health Check Path: /drive/index.html
Register respective EC2 instances.

---

### 6️⃣ Create Application Load Balancer

Type: Internet Facing
Listener: HTTP (Port 80)
Select 2 Availability Zones
Default Target Group → Gmail-target-grp

---

###7️⃣ Configure Path-Based Routing

Go to: EC2 → Load Balancer → Listeners → Rules → Add Rule
Condition:

Path = /drive*
Action:

Forward to drive-target-grp
Priority: 2
---

🌐 Final Output

Access applications using ALB DNS:
http://ALB-DNS/gmail⁠�
http://ALB-DNS/drive⁠�

---

##🔎 How It Works

User sends request to Load Balancer
ALB checks the URL path
Routing logic:
/gmail → Gmail Server
/drive → Drive Server
Target Groups forward request to EC2 instances
Health checks ensure only healthy instances receive traffic

---

##🚨 Troubleshooting

🔴 502 Bad Gateway
Cause: Apache service not running
Fix: sudo systemctl start httpd

🔴 503 Service Unavailable
Cause:
No healthy targets
Incorrect health check path
Fix:
Verify /gmail/index.html and /drive/index.html exist
Check Target Group health status

---

🎯 Key Learning Outcomes

Understanding Layer 7 Load Balancing
Implementing Path-Based Routing
Configuring Target Groups and Health Checks
Troubleshooting ALB Errors
Designing real-time cloud architecture

🙌 Conclusion
This project demonstrates how modern cloud architectures use Application Load Balancers to efficiently manage multiple applications, ensuring scalability, reliability, and better user experience.
