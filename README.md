# Deployment Steps for HTML Page on AWS EC2 Ubuntu Server

# AWS Account Setup
- I opened an AWS account and selected the London region (eu-west-2) for my configuration.
- Launched an EC2 instance and created an Ubuntu virtual machine using the free tier options.
- During the setup, I created a key pair named "altschool-keypair1-benjamin" for authentication purposes.
- Allocated 20 GB of storage (out of the available 30 GB free-tier limit).

# Security Group Configuration
- Configured a security group with inbound and outbound rules to allow necessary traffic.
- Enabled access for HTTP (port 80) and custom TCP ports (e.g., 8081) for testing purposes.

# Testing Connectivity
- Used Terminus to test connectivity to the Ubuntu server.
- Successfully logged in and created a new user profile named benji, granting it sudo privileges and setting a password.

# Web Server Setup
- Installed Nginx (running on port 80) and Apache (configured to run on port 8080).
- Wrote a simple HTML file locally using VSCode and saved it as index.html for deployment.

# File Transfer to Server
- To deploy the HTML file:
- Ran the following command to securely copy the index.html file from my local machine to the Ubuntu server:
- scp -i ~/Documents/Altschool-aws/altschool-keypair1-benjamin.pem ~/Documents/Altschool-exam/index.html ubuntu@18.170.228.126:/tmp/
- Used SSH to access the Ubuntu server:
- ssh -i /Users/benjamindurojaiye/Documents/Altschool-aws/altschool-keypair1-benjamin.pem ubuntu@18.170.228.126

# Configuring and Deploying HTML File
- Once logged in, I ran the following commands to configure and deploy the HTML file:
- Moved the HTML file to the Nginx root directory:
- sudo mv /tmp/index.html /var/www/html/index.html
- Set the correct ownership and permissions for the file:
- sudo chown www-data:www-data /var/www/html/index.html
- sudo chmod 644 /var/www/html/index.html
- Restarted both web servers to apply the changes:
- sudo systemctl restart apache2
- sudo systemctl restart nginx

# Deployment Verification
- After completing the steps, I verified that the HTML file was accessible over the internet by navigating to the public IP address of the EC2 instance.
- deployed url : http://18.170.228.126

This documentation outlines the steps I took to successfully deploy an HTML page on an AWS EC2 Ubuntu server.




