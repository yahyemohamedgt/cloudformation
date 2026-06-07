# AWS CloudFormation Infrastructure Portfolio

7 templates. One progression. Built entirely as code.

This repository documents how I approached building 
production-style AWS infrastructure from scratch — 
starting with a single S3 bucket and ending with a 
multi-AZ, auto-scaling web stack with a managed 
database layer.

Everything version-controlled.

---

## The progression

```
template.yaml   ->  S3 bucket (baseline)
vpc.yaml        ->  3-tier VPC, Bastion Host, private subnet isolation
ec2.yaml        ->  ALB + Apache web servers, health checks, port 80 listener
asg.yaml        ->  Auto Scaling Group, CloudWatch alarm, scale-up at CPU > 70%
rds.yaml        ->  RDS MySQL, automated backups, private subnet placement
iam.yaml        ->  Users, groups, roles, least-privilege policy scoping
s3-static.yaml  ->  Static website hosting, public bucket policy
```

---

## Architecture (asg.yaml — most complete template)

```
Internet
    |
    v
[Internet Gateway]
    |
    v
[ Public Subnets: AZ-1a / AZ-1b ]
    [ALB]     - port 80, health checks
    [Bastion] - SSH restricted to x.x.x.x/32
    |
    v
[ Private App Subnets ]
    [EC2 via ASG] min 1 / desired 2 / max 3
    CloudWatch: CPU > 70% -> +1 instance
    |
    v
[ Private Data Subnets ]
    [RDS MySQL] db.t3.micro
    20GB / 7-day backup / private access only
```

## Decisions worth noting

**Why a Bastion Host instead of SSM Session Manager?**  
Bastion was intentional for learning SSH key management 
and security group chaining. SSM would be the production 
preference — no open ports, full audit trail.

**Why CloudWatch CPU alarm for scaling?**  
Simple and demonstrable. In production I'd layer in ALB 
request count and custom application metrics for more 
responsive scaling decisions.

**What I'd change in production**
- RDS password via Secrets Manager (currently hardcoded — never do this in production)
- NAT Gateway for private subnet egress
- VPC Flow Logs + CloudTrail enabled by default
- Separate stacks with cross-stack references instead of monolithic templates

---

## What's next

Rebuilding this stack in Terraform — same architecture, 
different tooling. Then deploying real AI workloads 
(RAG pipelines, LangGraph agents) on top of this 
infrastructure foundation.

## Screenshots

## Architecture

![Architecture](screenshots/Architecture.png)

## Bastion Host

![Bastion Host](screenshots/Bastianhost.png)

## Connectivity Validation

![Ping Success](screenshots/ping.png)
