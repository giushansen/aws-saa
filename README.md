# AWS-SAA notes

## AWS Global Infrastructure

### Global

To plan for high availability (HA) and disaster recovery (DR)
34 `Region`s -> 108 `Availability zones` -> One or more discrete `data centers` with independent and redundant power infrastructure, networking, and connectivity -> 600+ Point of Presences  

### Services scoping

`Global`: AWS IAM, AWS Organizations, Amazon CloudFront, Amazon Route53, AWS Global Accelerator, AWS Direct Connect, AWS Firewall Manager, AWS Web Application Firewall (WAF), and AWS Shield
`Region scoped`: EC2 (IaaS) - Beanstalk (PaaS) - Lambda (FaaS) - Rekognition (SaaS)  

## IAM

## EC2

### Selection

Choose CPU, RAM, storage space `EBS/EFS/EC2 instance store`, network card `speed, public IP`, firewall rules `security group`, bootstrap script `EC2 user data with root user` and Key pair creation `SSH and PEM file`

### Instance type

`General instance`: (balance between Compute, Memory and Networking)'; for Web server, code repository (T, M, A)
`Compute optimized`: Batch processing, Game server, Media transcoding, High performance web server, High computing (C)  
`Memory optimized`: High peformance database, distributed cache store, In-memory database for Business Intelligence, Application with real-time processing of big data (R, X, z)  
`Storage optimized`: High frequency OLTP system, Database, Cache for database like Redis, Dataware housing applications, Distributed file systems (i, D, H1)  
*https://instances.vantage.sh/*

### Security Group

Act as a `Firewall` - Locked down to a region - Time out due to security group issue  
`Inbound` (default traffic is `Blocked`) and `Outbound` (default traffic is `Allowed`) rules for white listing of `Type`, `Protocol`, `Port`, `Source`  
Same security group instances are `Allowed`  
Good to maintain one security group dedicated to SSH access  

### SSH

`SSH`  
`Direct Connect`: (Simple web short lived SSH connection)  
`Session Manager`: Enable AWS CLI to establish SSH + Transfer files via SCP + use IAM policies to explicitly allow or deny users, groups, or roles to make SSH connections using Session Manager  



