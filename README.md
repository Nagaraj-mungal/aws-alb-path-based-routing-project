# AWS ALB Path-Based Routing Project

## Project Overview

This project demonstrates **Path-Based Routing using AWS Application Load Balancer (ALB)**.  

Two EC2 instances host two different web applications:

* Gmail Web Page  
* Google Drive Web Page  

Traffic is routed based on URL path using **Application Load Balancer**.

Example:

---

## Architecture

Client → Application Load Balancer → Target Groups → EC2 Instances
User Request
|
v
Application Load Balancer
|

| |
gmail-target-grp drive-target-grp
| |
Gmail EC2 Drive EC2

**Architecture Diagram:**

![Application Load Balancer](screenshots/application-load-balancer.png)

---

## AWS Services Used

* EC2
* Application Load Balancer
* Target Groups
* Security Groups
* GitHub
* Apache HTTP Server

---

## Project Workflow & Screenshots

### 1. Launch EC2 Instances

**Gmail Instance:**

![Launching Gmail Instance](screenshots/launching-gmail-instance.png)  

**Drive Instance:**

![Launching Drive Instance](screenshots/launching-drive-instance.png)  

---

### 2. Install Apache Web Server

**Gmail Instance (Step 1 & 2):**

![Apache Installation in Gmail Instance 1](screenshots/apache-installation-in-gmail-instance-1.png)  
![Apache Installation in Gmail Instance 2](screenshots/apache-installation-in-gmail-instance-2.png)  

**Drive Instance (Step 1 & 2):**

![Apache Installation in Drive Instance 1](screenshots/apache-installation-in-drive-instance-1.png)  
![Apache Installation in Drive Instance 2](screenshots/apache-installation-in-drive-instance-2.png)  

---

### 3. Configure Target Groups

![Target Groups](screenshots/target-groups.png)  

---

### 4. Configure Listener Rules

![Listener Rules](screenshots/listener-rules.png)  

---

### 5. Test Applications

**Gmail Application Open:**

![Gmail Application Opens](screenshots/gmail-application-opens.png)  

**Drive Application Open:**

![Drive Application Opens](screenshots/drive-application-opens.png)  

---

## Expected Output

Accessing the ALB URL with specific paths routes traffic correctly:

---

