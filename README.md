# AWS ALB Path-Based Routing Project

## Project Overview

This project demonstrates **Path-Based Routing using AWS Application Load Balancer (ALB)**.

Two EC2 instances host two different web applications:

* Gmail Web Page
* Google Drive Web Page

Using **Application Load Balancer**, traffic is routed based on URL path.

Example:

```
http://ALB-DNS/gmail
```

Routes traffic to **Gmail Server**

```
http://ALB-DNS/drive
```

Routes traffic to **Drive Server**

---

## Architecture

Client → Application Load Balancer → Target Groups → EC2 Instances

```
User Request
     |
     v
Application Load Balancer
     |
 -------------------------
 |                       |
gmail-target-grp     drive-target-grp
 |                       |
Gmail EC2             Drive EC2
```

---

## AWS Services Used

* EC2
* Application Load Balancer
* Target Groups
* Security Groups
* GitHub
* Apache HTTP Server

---

## Project Workflow

1. Launch two EC2 instances
2. Install Apache Web Server
3. Install Git
4. Deploy Gmail and Drive applications
5. Create Target Groups
6. Create Application Load Balancer
7. Configure Path Based Routing
8. Test the application

---

## Expected Output

```
http://ALB-DNS/gmail
```

Displays Gmail page.

```
http://ALB-DNS/drive
```

Displays Google Drive page.

---

## Author

Nagaraj M
