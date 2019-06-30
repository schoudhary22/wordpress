# High Availability Wordpress Setup

# Prerequisites
* Create EC2 Key Pair.

# Summary
1. Amazon Virtual Private Cloud
2. Internet Gateway
3. 2 Public and 2 Private subnets across ap-southeast-2a & ap-southeast-2b
4. Routing tables for public subnets routing through Internet Gateway
5. Mulitple VPC Security Groups for RDS, Wordpress instances & ALB
6. Amazon RDS Mysql cluster in private subnets with an option of Multi-AZ
7. Amazon Application Load Balancer in both public subnets
8. Auto Scaling Group launching Wordpress instances in both private subnets

# CloudFormation Template Details
The CloudFormation Template does the following:

1. EC2 Instance
    1. Amazon Linux
    2. EBS volume
    3. t2.micro (default)
    4. Public Subnet
2. Security Group
    1. Allow 80 Inbound
    2. Allow 22 Inbound
3. UserData (Bootstrapping)
    1. Yum Updates
    2. Install minimum packages
        1. cfn-init
        2. aws-cfn-bootstrap
        3. cloud-init
    3. Call cfn-init

# Cloud Init
1. Configure CFN INIT
2. Install_packages
    1. Install Nginx
    2. Install Php
    3. Download 5.1.1 Wordpress
    4. Install Wordpress
3. Configure Database to be used in Wordpress.
