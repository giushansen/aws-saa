# AWS-SAA notes

## EC2

### Selection

Choose CPU, RAM, storage space `EBS/EFS/EC2 instance store`, network card `speed, public IP`, firewall rules `security group`, bootstrap script `EC2 user data with root user` and Key pair creation `SSH and PEM file`

### Instance type

`General instance` (balance between Compute, Memory and Networking)'; for Web server, code repository (T, M, A)
`Compute optimized`: Batch processing, Game server, Media transcoding, High performance web server, High computing (C)  
`Memory optimized`: High peformance database, distributed cache store, In-memory database for Business Intelligence, Application with real-time processing of big data (R, X, z)  
`Storage optimized`: High frequency OLTP system, Database, Cache for database like Redis, Dataware housing applications, Distributed file systems (i, D, H1)  
*https://instances.vantage.sh/*

