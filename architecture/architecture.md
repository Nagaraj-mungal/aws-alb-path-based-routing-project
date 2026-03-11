# Architecture Overview

This project uses an Application Load Balancer to route traffic to different EC2 instances based on the URL path.

Components:

User
↓
Application Load Balancer
↓
Target Groups
↓
EC2 Instances

EC2 Instance 1
Gmail Application

EC2 Instance 2
Drive Application

Routing Rules

/gmail → Gmail Target Group  
/drive → Drive Target Group

Benefits

High availability  
Centralized traffic management  
Better scalability
