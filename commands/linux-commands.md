# Linux Commands Used in This Project

---------------------------------------

1. Update the System

sudo yum update -y

---------------------------------------

2. Install Apache Web Server

sudo yum install httpd -y

Start Apache Service

sudo systemctl start httpd

Enable Apache Service

sudo systemctl enable httpd

Check Apache Status

sudo systemctl status httpd

---------------------------------------

3. Install Git

sudo yum install git -y

---------------------------------------

4. Go to Web Root Directory

cd /var/www/html

---------------------------------------

5. Clone Gmail Web Application

GitHub Repository

https://github.com/CloudNinja9/gmail-main-page-template

Clone Repository

sudo git clone https://github.com/CloudNinja9/gmail-main-page-template

Rename Folder

sudo mv gmail-main-page-template gmail

---------------------------------------

6. Clone Google Drive Web Application

GitHub Repository

https://github.com/akshay-mudda/Google-Drive-Clone

Clone Repository

sudo git clone https://github.com/akshay-mudda/Google-Drive-Clone

Rename Folder

sudo mv Google-Drive-Clone drive

---------------------------------------

7. Clone Google Homepage (Optional)

GitHub Repository

https://github.com/JacobGrisham/Google-Homepage-HTML-and-CSS

Clone Repository

sudo git clone https://github.com/JacobGrisham/Google-Homepage-HTML-and-CSS

Move Files

sudo mv Google-Homepage-HTML-and-CSS/* .

---------------------------------------

8. Verify Web Applications

Gmail Application

http://Public-IP/gmail

Drive Application

http://Public-IP/drive

---------------------------------------

9. Restart Apache (if required)

sudo systemctl restart httpd

---------------------------------------

Project Deployment Summary

1. Installed Apache Web Server
2. Installed Git
3. Cloned Gmail Web Application from GitHub
4. Cloned Google Drive Web Application from GitHub
5. Deployed applications on EC2 servers
6. Verified applications using Public IP
7. Configured AWS Application Load Balancer for path-based routing
