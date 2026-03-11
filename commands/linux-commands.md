# Apache Installation

sudo yum update -y
sudo yum install httpd -y

# Start Apache

sudo systemctl start httpd

# Enable Apache on Boot

sudo systemctl enable httpd

# Install Git

sudo yum install git -y

# Create Application Folders

sudo mkdir /var/www/html/gmail
sudo mkdir /var/www/html/drive

# Copy Application Files

sudo cp index.html /var/www/html/gmail/
sudo cp index.html /var/www/html/drive/
