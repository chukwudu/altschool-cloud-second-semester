# Server Setup and Configuration Guide

## Overview

This document outlines the steps taken to provision and configure a Linux server to host a simple HTML webpage.

## Steps

### 1. Provision an EC2 Instance

1. Log in to AWS and navigate to the EC2 Dashboard.
2. Launch a new instance:
   - AMI: Ubuntu 22.04
   - Instance type: t2.micro
   - Security group: Allow SSH (port 22) and HTTP (port 80).
3. Associate an Elastic IP for a static public IP.

### 2. Connect to the Instance

1. Open a terminal or Termius and connect using SSH:

   ```bash
   ssh -i <your-key.pem> ubuntu@<your-public-ip>

### 3.Install Apache2

1.Update the system:
sudo apt update && sudo apt upgrade -y

2.Install Apache2:
sudo apt install apache2 -y

3.Verify Apache is running:
sudo systemctl status apache2

### 4 Configure DocumentRoot

1.Create a directory for your website:
sudo mkdir -p /var/www/html/landing

2.Set the appropriate permissions:
sudo chown -R $USER:$USER /var/www/html/landing

3.Update Apache's configuration:
sudo nano /etc/apache2/sites-available/000-default.conf
.Replace the DocumentRoot line with:
DocumentRoot /var/www/html/landing

4.Restart Apache:
sudo systemctl restart apache2

### 5. Upload Your HTML File

1.Navigate to the document root:
cd /var/www/html/landing
2.Create the index.html file:
nano index.html
3.Paste the content of your index.html

### 6. Verify Webpage

Open your browser and navigate to:
http://<your-public-ip>
