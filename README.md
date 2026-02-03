# Launch EC3 using AWS

Launch EC2 Instance Manually (With VPC, Subnet & Key Pair)

1️⃣ Login & Select Region

Login to AWS Management Console

Select a region
👉 Example: ap-south-1 (Mumbai)

2️⃣ Create a Custom VPC
Step 2.1: Go to VPC Service

Search VPC → Click Your VPCs

Click Create VPC

Step 2.2: Configure VPC
Setting	Value
Name	my-vpc
IPv4 CIDR	10.0.0.0/16
Tenancy	Default

Click Create VPC

3️⃣ Create a Public Subnet
Step 3.1: Subnet Settings

Go to Subnets → Create subnet

Select my-vpc

Setting	Value
Subnet name	public-subnet
AZ	ap-south-1a
CIDR	10.0.1.0/24

Click Create subnet

4️⃣ Create and Attach Internet Gateway
Step 4.1: Create IGW

Go to Internet Gateways

Click Create internet gateway

Name: my-igw

Step 4.2: Attach IGW to VPC

Select my-igw

Click Actions → Attach to VPC

Choose my-vpc

5️⃣ Create Route Table for Public Access
Step 5.1: Create Route Table

Go to Route Tables

Click Create route table

Name: public-rt

VPC: my-vpc

Step 5.2: Add Route to Internet

Select public-rt

Click Edit routes

Add:

Destination: 0.0.0.0/0

Target: Internet Gateway (my-igw)

Save

Step 5.3: Associate Route Table

Go to Subnet associations

Edit → Select public-subnet

Save

6️⃣ Create Key Pair (For SSH Access)

Go to EC2 → Key Pairs

Click Create key pair

Name: ec2-key

Type: RSA

Format: .pem

Click Create

⚠️ Download & store securely — cannot be re-downloaded

7️⃣ Create Security Group
Step 7.1: Security Group Rules

Go to Security Groups

Click Create security group

Rule	Port	Source
SSH	22	My IP
HTTP	80	0.0.0.0/0

VPC: my-vpc

Click Create security group

8️⃣ Launch EC2 Instance
Step 8.1: Choose AMI

Amazon Linux 2023 (Free Tier eligible)

Step 8.2: Instance Type

t2.micro

9️⃣ Configure Networking (VERY IMPORTANT)
Setting	Value
VPC	my-vpc
Subnet	public-subnet
Auto-assign Public IP	Enable
Security Group	ec2-sg
Key Pair	ec2-key
🔟 Configure Storage

Default 8 GB gp3 → OK

1️⃣1️⃣ (Optional) User Data Script
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd

1️⃣2️⃣ Launch Instance

Click Launch instance

Instance state → Running 🎉

1️⃣3️⃣ Verify VPC Connectivity
Check:

Instance has Public IPv4

Route table has IGW route

Security group allows SSH/HTTP

1️⃣4️⃣ Connect to EC2 via SSH
chmod 400 ec2-key.pem
ssh -i ec2-key.pem ec2-user@<PUBLIC-IP>

1️⃣5️⃣ Test Application

Open browser:

http://<PUBLIC-IP>

🔐 Best Practices (Interview Gold ✨)

Use private subnets for databases

Use NAT Gateway for outbound internet

Never expose SSH to 0.0.0.0/0

Use IAM Roles, not access keys

🧠 What You Learn From This

How EC2 connects to a VPC

How public internet access works

How key pairs enable secure login

How AWS networking components interact
