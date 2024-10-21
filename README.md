# AWS-SAA notes

## AWS Global Infrastructure

### Global
To plan for high availability (HA) and disaster recovery (DR)
34 `Region`s -> 108 `Availability zones` -> One or more discrete `data centers` with independent and redundant power infrastructure, networking, and connectivity -> 600+ Point of Presences  

### Services scoping
`Global`: AWS IAM, AWS Organizations, Amazon CloudFront, Amazon Route53, AWS Global Accelerator, AWS Direct Connect, AWS Firewall Manager, AWS Web Application Firewall (WAF), and AWS Shield
`Region scoped`: EC2 (IaaS) - Beanstalk (PaaS) - Lambda (FaaS) - Rekognition (SaaS)  

## IAM

### Entities management
`Users` can have many `Groups` and vice versa  
`Policies` define `Permissions` for an action ie: _AdministatorAccess => {Effect: Allow,  Action: {ec2: Describe, cloudwatch: GetMetricsStatistics},  Resource: *}_  
Attach policies to IAM identities (`Users`, `Groups` to which users belong, or `Roles`)

### Password
Policy: _min length_ (upper case, lower, number) + allow IAM users to _change password_ + _expiration_ + prevent _password reuse_  
MFA = _password_ you know + _device_ you own  
- Virtual MFA: Google Authenticator (phone for multiple tokens and one device) or Authy (multi device)
- U2F (Universal 2nd factor) Yubikey by Yubico (multiple roots and users)
- Key Fob MFA device (Gemalto)  
- Key Fob MFA device (AWS Gov Cloud)  

### Accesses
`AWS Managment console` (MFA)  
`AWS CLI` (Access keys)  
`AWS SDK` (Access keys)  
Access keys generated by console: `Access key ID` ~= username & `Secret access key` ~= password  
Add permission to AWS Services with `IAM Role` (EC2, Lambda, Cloudformation)  


## EC2

### Selection

Choose CPU, RAM, storage space `EBS/EFS/EC2 instance store`, network card `speed, public IP`, firewall rules `security group`, bootstrap script `EC2 user data with root user` and Key pair creation `SSH and PEM file`

### Instance type

`General instance`: (balance between Compute, Memory and Networking)'; for Web server, code repository (T, M, A)
`Compute optimized`: Batch processing, Game server, Media transcoding, High performance web server, High computing (C)  
`Memory optimized`: High peformance database, distributed cache store, In-memory database for Business Intelligence, Application with real-time processing of big data (R, X, z)  
`Storage optimized`: High frequency OLTP system, Database, Cache for database like Redis, Dataware housing applications, Distributed file systems (i, D, H1)  
*https://instances.vantage.sh/*  

Purchase options:
- On-Demand Instances: short workload, predictable pricing, pay per second, high cost, no upfront payment or long-term commitment
- Reserved: (1 & 3 years)  
  - Reserved instances - long workloads
  - Convertible Reserved instances - long workloads with flexible instances but less discount   
- Savings plans: (1 & 3 years) commitment to an amount of $ usage, long workload
- Spot instances: short workload, cheap, can lose instance (less reliable) `current spot price < max spot` price then stop or terminate with 2 mins grace period OR `spot block for 1 to 6 hrs`
  - Spot fleets: Allow us to automatically request spot instances with `lowestPrice/diversified/capacityOptimized/priceCapacityOptimized(recommended)`     
- Dedicated host: book an entire `physical server`, control instance placement, most expensive
- Dedicated instance: no other customers will share your `hardware but for the same account`
- Capacity reservations: reserve capacity in a specific AZ for any duration, no billing discount, on demand rate, suitable for short term, uninterrupted workloads in specific AZ    

### Security Group

Act as a `Firewall` - Locked down to a region - Time out due to security group issue  
`Inbound` (default traffic is `Blocked`) and `Outbound` (default traffic is `Allowed`) rules for white listing of `Type`, `Protocol`, `Port`, `Source`  
Same security group instances are `Allowed`  
Good to maintain one security group dedicated to SSH access  

### SSH

`SSH`  
`Direct Connect`: (Simple web short lived SSH connection)  
`Session Manager`: Enable AWS CLI to establish SSH + Transfer files via SCP + use IAM policies to explicitly allow or deny users, groups, or roles to make SSH connections using Session Manager  
Use IAM roles for EC2  

### IP

#### Public IP

Public IP means the machine can be identified on the internet (WVVW) • Must be unique across the whole web (not two machines can have the same public IP). • Can be geo-located easily  

#### Private IP

- Private IP means the machine can only be identified on a private network only  
- The IP must be unique across the private network - two different private networks (two companies) can have the same IPs - connect to WWW using an internet gateway (a proxy) - Only a specified range of IPs can be used as private IP 

### Placement groups

- `Cluster`: clusters instances into a low-latency group in a single Availability Zone  
- `Spread`: spreads instances across underlying hardware (max 7 instances per group per AZ) — critical applications
- `Partition`: spreads instances across many different partitions (which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group (Hadoop, Cassandra, Kafka) 




