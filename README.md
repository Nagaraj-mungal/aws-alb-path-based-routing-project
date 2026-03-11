# AWS Application Load Balancer with Path-Based Routing

## Project Overview

This project demonstrates how to deploy multiple web applications behind a single Application Load Balancer (ALB) using path-based routing in AWS.

Two EC2 instances are used to host different applications. The ALB routes incoming traffic based on the URL path.

Example:

/gmail → Gmail application  
/drive → Google Drive application

This setup improves scalability, availability, and efficient traffic distribution.

---

## Architecture

User Request → Application Load Balancer → Target Groups → EC2 Instances

Routing Logic:

/gmail → Gmail Target Group → Gmail EC2 Server  
/drive → Drive Target Group → Drive EC2 Server

---

## AWS Services Used

- Amazon EC2
- Application Load Balancer
- Target Groups
- Security Groups
- Git
- Apache Web Server

---

## Project Workflow

1. Launch two EC2 instances
2. Install Apache web server
3. Deploy web applications
4. Create target groups
5. Configure Application Load Balancer
6. Implement path-based routing
7. Test application access through ALB DNS

---

## Application Access

http://ALB-DNS/gmail
http://ALB-DNS/drive

---

## Final Result

Both applications are accessible from a single Application Load Balancer endpoint.

This architecture is commonly used in microservices-based applications.

---

## Author

Nagaraj M  
Cloud & DevOps Learner

