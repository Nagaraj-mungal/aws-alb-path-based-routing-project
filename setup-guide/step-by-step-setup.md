# Step-by-Step Setup Guide

## Step 1 Create EC2 Instances

Create two EC2 instances:

1. Gmail Server
2. Drive Server

Instance configuration:

AMI: Amazon Linux 2
Instance Type: t2.micro

Security Group:

Allow ports:

22 (SSH)
80 (HTTP)

---

## Step 2 Install Apache

Login to both servers.

```
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

## Step 3 Install Git

```
sudo yum install git -y
```

---

## Step 4 Deploy Gmail Web Page

Login to Gmail Server.

```
cd /var/www/html
sudo git clone https://github.com/CloudNinjaa/gmail-main-page-template
sudo mv gmail-main-page-template gmail
```

Verify:

```
http://Gmail-Public-IP/gmail
```

---

## Step 5 Deploy Google Drive Web Page

Login to Drive Server.

```
cd /var/www/html
sudo git clone https://github.com/akshay-vmudda/Google-Drive-Clone
sudo mv Google-Drive-Clone drive
```

Verify:

```
http://Drive-Public-IP/drive
```

---

## Step 6 Create Target Groups

Create two target groups.

Target Group 1

Name: gmail-target-grp
Health Check Path:

```
/gmail/index.html
```

Target Group 2

Name: drive-target-grp
Health Check Path:

```
/drive/index.html
```

Register respective EC2 instances.

---

## Step 7 Create Application Load Balancer

Go to:

EC2 → Load Balancers → Create Load Balancer

Choose:

Application Load Balancer

Configuration:

Scheme: Internet Facing
Listener: HTTP (80)

Attach:

gmail-target-grp

Create Load Balancer.

---

## Step 8 Configure Path Based Routing

Go to:

Load Balancer → Listeners → View Rules

Add new rule.

Condition:

```
Path = /drive*
```

Action:

Forward to:

```
drive-target-grp
```

Priority:

```
2
```

Save rule.

---

## Step 9 Test Application

Open browser.

```
http://ALB-DNS/gmail
```

Gmail page loads.

```
http://ALB-DNS/drive
```

Google Drive page loads.
