# Task-3
AWS Core Services – Overview Report
1. Introduction

Amazon Web Services (AWS) is a leading cloud computing platform that provides on-demand access to computing resources such as servers, storage, databases, and networking.
This report covers core AWS services, explaining their purpose, key features, and how they work together to build scalable, secure, and cost-efficient cloud solutions.

2. What is Cloud Computing?

Cloud computing is the delivery of computing services over the internet, allowing users to:

Avoid upfront infrastructure costs

Scale resources on demand

Pay only for what they use

Cloud Service Models

IaaS (Infrastructure as a Service) – EC2, EBS

PaaS (Platform as a Service) – Elastic Beanstalk

SaaS (Software as a Service) – AWS-hosted applications

3. Core AWS Services Overview
3.1 Compute Services

Compute services provide processing power to run applications.

Amazon EC2 (Elastic Compute Cloud)

Virtual servers in the cloud

Multiple instance types for different workloads

Supports Auto Scaling and Load Balancing

AWS Lambda

Serverless compute service

Runs code without managing servers

Charged only for execution time

Use Case: Hosting backend APIs, automation tasks, event-driven applications

3.2 Storage Services

Storage services store data securely and reliably.

Amazon S3 (Simple Storage Service)

Object storage for files, images, and backups

Highly durable and scalable

Supports versioning and lifecycle policies

Amazon EBS (Elastic Block Store)

Block storage for EC2 instances

Used for OS disks and databases

Use Case: Application data storage, backups, static website hosting

3.3 Database Services

Database services manage structured and unstructured data.

Amazon RDS (Relational Database Service)

Managed relational databases (MySQL, PostgreSQL, Oracle)

Automated backups and patching

Amazon DynamoDB

Fully managed NoSQL database

High performance and low latency

Use Case: Application databases, real-time data storage

3.4 Networking Services

Networking services control traffic flow and connectivity.

Amazon VPC (Virtual Private Cloud)

Isolated network environment

Control IP ranges, subnets, and routing

Elastic Load Balancer (ELB)

Distributes traffic across multiple EC2 instances

Improves availability and fault tolerance

Use Case: Secure networking and traffic management

3.5 Security & Identity Services

Security services manage access and protect resources.

AWS IAM (Identity and Access Management)

Manage users, roles, and permissions

Enforces least-privilege access

AWS Security Groups

Virtual firewalls for EC2 instances

Control inbound and outbound traffic

Use Case: Access control and infrastructure security

3.6 Monitoring & Management Services

Monitoring services help observe and manage AWS resources.

Amazon CloudWatch

Collects logs and metrics

Enables alarms and automated actions

AWS CloudTrail

Tracks API calls and user activity

Useful for auditing and compliance

Use Case: System monitoring, debugging, and auditing

4. How AWS Core Services Work Together

AWS services are designed to integrate seamlessly:

EC2 hosts applications

S3 stores application data and backups

RDS manages databases

VPC secures network communication

IAM controls access

CloudWatch monitors performance

This integration enables high availability, scalability, and security.

5. Advantages of Using AWS Core Services

Scalability: Easily scale resources up or down

Cost Optimization: Pay-as-you-go pricing

High Availability: Global infrastructure

Security: Built-in security best practices

Automation: Infrastructure can be managed using code

6. Real-World Use Cases

Hosting web and mobile applications

CI/CD pipelines for DevOps

Data backup and disaster recovery

Serverless applications

Monitoring and logging systems

7. Conclusion & Key Learnings
Conclusion

AWS Core services form the foundation of cloud computing by providing reliable, scalable, and secure infrastructure. By combining compute, storage, networking, security, and monitoring services, AWS enables organizations to build modern cloud-native applications efficiently.

What We Learn from AWS Core Services

How cloud infrastructure replaces traditional data centers

Importance of scalability and fault tolerance

How security and access control are managed in the cloud

How automation and monitoring improve reliability

How cost optimization is achieved using pay-as-you-go models
