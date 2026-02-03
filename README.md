# EC2 instance using Terraform

🚀 Launch EC2 Instance Using Terraform (With VPC & Key Pair)
📌 Project Overview

This project demonstrates how to provision an AWS EC2 instance using Terraform, including:

Custom VPC

Public Subnet

Internet Gateway

Route Table

Security Group

Key Pair

EC2 Instance

The goal is to understand Infrastructure as Code (IaC) and automate AWS infrastructure deployment.

🛠️ Technologies Used

AWS EC2

AWS VPC

Terraform

AWS IAM

Amazon Linux 2023

📋 Prerequisites

Before starting, ensure you have:

AWS Account

IAM user with:

AmazonEC2FullAccess

AmazonVPCFullAccess

AWS CLI installed & configured

Terraform installed

SSH key pair (.pem or .pub file)

Verify Terraform:

terraform -v

🔐 Configure AWS Credentials
aws configure


Provide:

AWS Access Key

AWS Secret Key

Default Region (e.g. ap-south-1)

Output format: json

📁 Project Structure
terraform-ec2-vpc/
│
├── provider.tf
├── vpc.tf
├── subnet.tf
├── internet_gateway.tf
├── route_table.tf
├── security_group.tf
├── ec2.tf
└── keypair.tf (optional)

🌐 Infrastructure Components
1️⃣ Provider Configuration
provider "aws" {
  region = "ap-south-1"
}

2️⃣ Create VPC
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"

  tags = {
    Name = "tf-vpc"
  }
}

3️⃣ Create Public Subnet
resource "aws_subnet" "public" {
  vpc_id                  = aws_vpc.main.id
  cidr_block              = "10.0.1.0/24"
  availability_zone       = "ap-south-1a"
  map_public_ip_on_launch = true

  tags = {
    Name = "tf-public-subnet"
  }
}

4️⃣ Internet Gateway
resource "aws_internet_gateway" "igw" {
  vpc_id = aws_vpc.main.id

  tags = {
    Name = "tf-igw"
  }
}

5️⃣ Route Table
resource "aws_route_table" "public_rt" {
  vpc_id = aws_vpc.main.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.igw.id
  }
}

resource "aws_route_table_association" "public_assoc" {
  subnet_id      = aws_subnet.public.id
  route_table_id = aws_route_table.public_rt.id
}

6️⃣ Security Group
resource "aws_security_group" "ec2_sg" {
  vpc_id = aws_vpc.main.id

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["YOUR_IP/32"]
  }

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

7️⃣ Key Pair
resource "aws_key_pair" "key" {
  key_name   = "tf-key"
  public_key = file("~/.ssh/id_rsa.pub")
}

8️⃣ EC2 Instance
resource "aws_instance" "web" {
  ami                    = "ami-0f5ee92e2d63afc18"
  instance_type          = "t2.micro"
  subnet_id              = aws_subnet.public.id
  vpc_security_group_ids = [aws_security_group.ec2_sg.id]
  key_name               = aws_key_pair.key.key_name

  user_data = <<-EOF
              #!/bin/bash
              yum update -y
              yum install httpd -y
              systemctl start httpd
              systemctl enable httpd
              EOF

  tags = {
    Name = "tf-ec2-instance"
  }
}

🚀 Deploy Infrastructure
Initialize Terraform
terraform init

Validate
terraform validate

Plan
terraform plan

Apply
terraform apply


Type yes to confirm.

🔗 Access EC2 Instance
chmod 400 tf-key.pem
ssh -i tf-key.pem ec2-user@<PUBLIC-IP>


Open browser:

http://<PUBLIC-IP>

🧹 Destroy Resources (Important)
terraform destroy

📘 What We Learn From This Project

How to use Terraform for AWS automation

How VPC networking works

How EC2 connects to the internet

Secure access using key pairs.

✅ Conclusion

This project demonstrates how Infrastructure as Code (IaC) simplifies cloud deployments by making infrastructure repeatable, version-controlled, and automated. Using Terraform with AWS allows teams to deploy scalable and secure cloud environments efficiently while reducing manual errors.


Infrastructure lifecycle management

Cost control using terraform destroy
