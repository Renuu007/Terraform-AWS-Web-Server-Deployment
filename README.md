# Terraform AWS Web Server Deployment

This repository contains Terraform code to deploy an Apache web server on an AWS EC2 instance. The setup includes a VPC, subnet, security group, internet gateway, route table, and an Elastic IP for public access.

## Architecture Overview

The Terraform configuration sets up the following AWS resources:

- **VPC**: A custom Virtual Private Cloud (VPC) with a CIDR block of `10.0.0.0/16`.
- **Subnet**: A public subnet (`10.0.1.0/24`) within `ap-south-1a` availability zone.
- **Internet Gateway**: Enables internet access for instances.
- **Route Table**: Configured to route traffic through the internet gateway.
- **Security Group**: Allows inbound access for HTTP (80), HTTPS (443), and SSH (22) from any IP (can be restricted for security).
- **Elastic IP**: Ensures a static public IP for the instance.
- **EC2 Instance**: A `t2.micro` instance with Ubuntu, pre-installed Apache web server.

## Prerequisites

Before deploying, ensure you have the following:

- An AWS account with appropriate permissions.
- Terraform installed ([Download Here](https://www.terraform.io/downloads.html)).
- AWS CLI configured with credentials (`aws configure`).
- SSH key pair created in AWS (update `main.tf` with your key name).

## Installation & Deployment

1. **Clone the Repository**
   git clone https://github.com/yourusername/your-repo.git
   cd your-repo

2. **Initialize Terraform**
   terraform init

3. **Validate the Configuration**
   terraform validate

4. **Plan the Deployment**
   terraform plan

5. **Apply the Configuration**
   terraform apply -auto-approve

6. **Get the Public IP**
   After deployment, the public IP will be displayed as output. You can also fetch it using:
   terraform output public_ip

7. **Access the Web Server**
   Open a browser and navigate to:
   http://<public-ip>
   You should see a page displaying: `my very first web server`.

## Clean Up

To destroy all created resources:
terraform destroy -auto-approve

## File Structure
.
├── main.tf         # Terraform configuration for AWS resources
├── output.tf       # Outputs public IP of the instance
├── README.md       # Project documentation

## Notes
- Modify `main.tf` to restrict SSH access for better security.
- If using a different AWS region, update `provider` block and `availability_zone`.
- Ensure your SSH key pair exists in AWS before applying.
