
---

# Static Website Hosting on AWS

This project demonstrates how to host a static HTML web application on AWS, utilizing various AWS services to ensure a secure, scalable, and highly available deployment. The website is hosted on EC2 instances within a VPC configured with public and private subnets across multiple availability zones.

## Project Overview

In this project, I set up a Virtual Private Cloud (VPC) to host a static website on AWS. The project includes the following key components:

1. **Virtual Private Cloud (VPC) Configuration:**
   - Configured a VPC with both public and private subnets across two different availability zones to enhance fault tolerance and reliability.

2. **Internet Gateway Deployment:**
   - Deployed an Internet Gateway to allow instances within the VPC to connect to the internet.

3. **Security Groups:**
   - Established Security Groups as a network firewall to control inbound and outbound traffic for EC2 instances.

4. **Availability Zones:**
   - Utilized two Availability Zones to distribute resources and improve system reliability.

5. **Public Subnets:**
   - Hosted infrastructure components such as the NAT Gateway and Application Load Balancer in public subnets.

6. **EC2 Instance Connect Endpoint:**
   - Implemented an EC2 Instance Connect Endpoint to enable secure connections to instances within both public and private subnets.

7. **Private Subnets:**
   - Positioned web servers (EC2 instances) within private subnets to enhance security.

8. **NAT Gateway:**
   - Enabled instances in both private application and data subnets to access the internet via the NAT Gateway.

9. **Web Hosting:**
   - Hosted the static website on EC2 instances within the private subnets.

10. **Application Load Balancer:**
    - Employed an Application Load Balancer and a target group to distribute web traffic evenly across an Auto Scaling Group of EC2 instances deployed across multiple Availability Zones.

11. **Auto Scaling Group:**
    - Configured an Auto Scaling Group to automatically manage the EC2 instances, ensuring the website's availability, scalability, fault tolerance, and elasticity.

12. **Version Control:**
    - Stored web files in a GitHub repository for version control and collaboration.

13. **Secure Communications:**
    - Secured application communications using AWS Certificate Manager.

14. **Monitoring and Notifications:**
    - Configured AWS Simple Notification Service (SNS) to send alerts regarding activities within the Auto Scaling Group.

15. **Domain Name and DNS Configuration:**
    - Registered a domain name and set up DNS records using AWS Route 53.

## Project Setup

### Prerequisites

- AWS Account
- Domain name (for DNS setup)
- GitHub repository containing the static website files

### Deployment Steps

1. **Clone the Project Repository:**
   ```bash
   # Switch to the root user to gain full administrative privileges
   sudo su
   
   # Update all installed packages to their latest versions
   yum update -y
   
   # Install Apache HTTP Server
   yum install -y httpd
   
   # Change the current working directory to the Apache web root
   cd /var/www/html
   
   # Install Git
   yum install git -y
   
   # Clone the project GitHub repository to the current directory
   git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
   
   # Copy all files, including hidden ones, from the cloned repository to the Apache web root
   cp -R host-a-static-website-on-aws/. /var/www/html/
   
   # Remove the cloned repository directory to clean up unnecessary files
   rm -rf host-a-static-website-on-aws
   
   # Enable the Apache HTTP Server to start automatically at system boot
   systemctl enable httpd 
   
   # Start the Apache HTTP Server to serve web content
   systemctl start httpd
   ```


