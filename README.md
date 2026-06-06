# AWS CloudFormation Infrastructure Portfolio

## Overview

This repository contains a collection of AWS Infrastructure as Code (IaC) projects built using AWS CloudFormation.

The goal of this portfolio is to demonstrate practical experience deploying and managing AWS infrastructure components including networking, compute, storage, databases, load balancing, and auto scaling.

## Projects Included

### VPC & Networking

- Custom VPC (10.0.0.0/16)
- Public and Private Subnets across multiple Availability Zones
- Internet Gateway
- Route Tables
- Security Groups

### IAM

- IAM users
- IAM groups
- IAM policies
- Permission management using Infrastructure as Code

### EC2 Web Infrastructure

- EC2 instances deployed through CloudFormation
- Apache web server installation using User Data
- Multi-AZ deployment

### Application Load Balancer (ALB)

- Load balancing across multiple EC2 instances
- Target Groups
- Health Checks
- HTTP Listener configuration

### Auto Scaling Group (ASG)

- Launch Templates
- Auto Scaling Group
- Desired Capacity: 2
- Minimum Capacity: 1
- Maximum Capacity: 3
- CloudWatch Alarm
- Scaling Policy

### Amazon S3 Static Website Hosting

- Static website deployment
- Bucket Policies
- Public website endpoint
- HTML content hosting

### Amazon RDS

- MySQL database deployment
- CloudFormation-managed infrastructure
- Automated backups
- Database lifecycle management

## Technologies Used

- AWS CloudFormation
- Amazon VPC
- Amazon EC2
- Application Load Balancer
- Auto Scaling Groups
- Amazon S3
- Amazon RDS
- IAM
- CloudWatch
- Git
- GitHub

## Repository Structure

- vpc.yaml
- iam.yaml
- ec2.yaml
- asg.yaml
- s3-static.yaml
- rds.yaml

## Screenshots

## Architecture

![Architecture](screenshots/Architecture.png)

## Bastion Host

![Bastion Host](screenshots/Bastianhost.png)

## Connectivity Validation

![Ping Success](screenshots/ping.png)

## Key Lessons Learned

- Infrastructure can be deployed and version-controlled using CloudFormation.
- Networking, compute, storage, and databases can be managed consistently through IaC.
- Auto Scaling improves availability and elasticity.
- Load Balancers distribute traffic across multiple instances.
- S3 can host static websites with minimal operational overhead.
- RDS simplifies managed database operations.

