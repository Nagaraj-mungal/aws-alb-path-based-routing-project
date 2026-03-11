# Step 1: Launch EC2 Instances

Create two Amazon Linux EC2 instances.

Instance 1
Name: Gmail-Server

Instance 2
Name: Drive-Server

Security Group Rules

SSH - Port 22  
HTTP - Port 80

---

# Step 2: Connect to EC2

ssh -i key.pem ec2-user@public-ip

---

# Step 3: Install Apache Web Server

sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
 sudo systemctl enable httpd

 ---

# Step 4: Create Application Directories

sudo mkdir /var/www/html/gmail 
sudo mkdir /var/www/html/drive

---

# Step 5: Deploy Applications

Copy application files.

---

# Step 6: Create Target Groups

Create two target groups.

gmail-target-group

Health check path:

/gmail/index.html

drive-target-group

Health check path:

/drive/index.html

---

# Step 7: Register Targets

Register Gmail EC2 instance to gmail-target-group.

Register Drive EC2 instance to drive-target-group.

---

# Step 8: Create Application Load Balancer

Type: Internet Facing

Listener: HTTP Port 80

Attach two Availability Zones.

---

# Step 9: Configure Listener Rules

Default Rule

Forward → gmail-target-group

Add Rule

Path: /drive*

Forward → drive-target-group

---

# Step 10: Test the Application

Open browser

http://ALB-DNS/gmail

Gmail application opens.

http://ALB-DNS/drive

Drive application opens.

This confirms successful path-based routing.
