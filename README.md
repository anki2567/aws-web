# AWS Web Application Deployment

## Project Overview

This project demonstrates deployment of a simple static web application using Amazon Web Services (AWS).

The application is hosted in two ways:
1. Static website hosting using Amazon S3
2. Web server hosting using Amazon EC2 (Apache)

Infrastructure provisioning is automated using Terraform (Infrastructure as Code).

---

## Architecture Overview

User → Internet →

- Amazon S3 (Static Website Hosting)
- Amazon EC2 (Apache Web Server)

### Components Used:

- Amazon EC2 – Hosts Apache web server
- Amazon S3 – Hosts static website
- IAM – Manages secure access
- Security Groups – Controls network traffic
- Terraform – Automates infrastructure creation

---

## AWS Services Used

- Amazon EC2
- Amazon S3
- AWS IAM
- Security Groups
- Terraform

---

## Project Structure

aws-web/
│
├── infrastructure/
│   ├── provider.tf
│   ├── main.tf
│   └── variables.tf
│
├── scripts/
│
├── website/
│   └── index.html
│
└── README.md

---

## Prerequisites

- AWS Account (Free Tier)
- AWS CLI configured
- Terraform installed

---

## Setup Instructions

### 1. Clone Repository

git clone <repository-url>
cd aws-web

### 2. Configure AWS CLI

aws configure

### 3. Deploy Infrastructure Using Terraform

cd infrastructure
terraform init
terraform plan
terraform apply

Type `yes` when prompted.

---

## Accessing the Application

### EC2 Web Server

Open browser and visit:

http://<EC2-Public-IP>

### S3 Static Website

Open S3 static website endpoint:

http://<bucket-name>.s3-website-region.amazonaws.com

---

## Security Considerations

- IAM user used instead of root account
- Least privilege principle followed
- No AWS credentials committed to GitHub
- .terraform and state files excluded using .gitignore
- Security Group allows only:
  - Port 22 (SSH)
  - Port 80 (HTTP)
- .pem key file not committed

---

## Infrastructure as Code

Terraform automates:

- Security Group creation
- EC2 instance provisioning
- Apache installation via user_data

Commands used:

terraform init
terraform plan
terraform apply
terraform destroy

---

## Cleanup Steps (To Avoid AWS Charges)

After testing, run:

terraform destroy

Also delete:
- S3 bucket
- IAM user (if created specifically for this project)
