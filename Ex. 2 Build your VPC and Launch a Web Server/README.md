# Build Your VPC and Launch a Web Server (AWS) 

## Author

* **Name**: HARIRAM R
* **Register Number**: 212224240050
* **Date of Submission**: 24/02/2026

---

## Objective

The objective of this experiment is to understand how to design and configure a basic network infrastructure in AWS using a Virtual Private Cloud (VPC). This lab focuses on creating a VPC with a public subnet, configuring an Internet Gateway and route table, launching an EC2 instance, and hosting a simple web server that can be accessed over the internet.

---

## Prerequisites

* Basic understanding of cloud computing concepts
* AWS account or AWS Academy Lab access
* Web browser with internet connectivity

---

## Tools Used

* AWS Management Console
* Amazon VPC
* Amazon EC2
* Internet Gateway
* Route Table
* Security Groups

---

## Tasks Performed

### Task 1: Create a VPC

Create a new Virtual Private Cloud (VPC) with a private IP address range. The VPC acts as a logically isolated network in AWS where all other resources will be deployed.

Students should create a VPC with an appropriate CIDR block (for example, 10.0.0.0/16) and assign a meaningful name.


### Task 2: Create a Public Subnet

Create a subnet inside the VPC to host public resources. Enable auto-assign public IPv4 so that instances launched in this subnet receive a public IP address.

The subnet should use a smaller CIDR range (for example, 10.0.1.0/24).


### Task 3: Create and Attach Internet Gateway

Create an Internet Gateway (IGW) and attach it to the VPC. This allows communication between resources in the VPC and the internet.


### Task 4: Configure Route Table

Create a route table and add a default route (0.0.0.0/0) pointing to the Internet Gateway. Associate this route table with the public subnet.

This step ensures that traffic from the subnet can reach the internet.


### Task 5: Create Security Group

Create a security group to act as a virtual firewall for the EC2 instance. Configure inbound rules to allow:

SSH on port 22

HTTP on port 80


### Task 6: Launch EC2 Instance

Launch an EC2 instance inside the public subnet using Amazon Linux 2 AMI and a suitable instance type (t2.micro).

Attach the previously created security group and key pair.


### Task 7: Configure Web Server

Install and start a web server (Apache HTTPD) on the EC2 instance using user data or manual commands.

Create a simple HTML page and verify that it can be accessed from a web browser using the public IP address of the instance.---

## Workflow (Student Explanation)

### Task 1: Create Your VPC

Step 1
In the search box to the right of Services, search for and choose VPC to open the VPC console.

Step 2
Begin creating a VPC.

Step 3
In the top right of the screen, verify that N. Virginia (us-east-1) is the region.

Step 4
Choose the VPC dashboard link which is towards the top left of the console.

Step 5
Choose Create VPC.

Step 6
If you do not see a button with that name, choose the Launch VPC Wizard button instead.

Step 7
Configure the VPC details in the VPC settings panel on the left.

Step 8
Choose VPC and more.

Step 9
Under Name tag auto-generation, keep Auto-generate selected, however change the value from project to lab.

Step 10
Keep the IPv4 CIDR block set to 10.0.0.0/16.

Step 11
For Number of Availability Zones, choose 1.

Step 12
For Number of public subnets, keep the 1 setting.

Step 13
For Number of private subnets, keep the 1 setting.

Step 14
Expand the Customize subnets CIDR blocks section.

Step 15
Change Public subnet CIDR block in us-east-1a to 10.0.0.0/24.

Step 16
Change Private subnet CIDR block in us-east-1a to 10.0.1.0/24.

Step 17
Set NAT gateways to In 1 AZ.

Step 18
Set VPC endpoints to None.

Step 19
Keep both DNS hostnames and DNS resolution enabled.

Step 20
In the Preview panel on the right, confirm the settings you have configured.

Step 21
At the bottom of the screen, choose Create VPC.

Step 22
Wait until all resources are created and NAT Gateway activates.

Step 23
Choose View VPC.

Step 24
Browse through the VPC console links to view resource details like Subnets and Route tables.

### Task 2: Create Additional Subnets

Step 25
In the left navigation pane, choose Subnets.

Step 26
Choose Create subnet.

Step 27
Configure second public subnet:
VPC ID: lab-vpc
Subnet name: lab-subnet-public2
Availability Zone: us-east-1b
IPv4 CIDR block: 10.0.2.0/24

Step 28
Choose Create subnet.

Step 29
Choose Create subnet again to create private subnet.

Step 30
Configure second private subnet:
VPC ID: lab-vpc
Subnet name: lab-subnet-private2
Availability Zone: us-east-1b
IPv4 CIDR block: 10.0.3.0/24

Step 31
Choose Create subnet.

Step 32
In left navigation pane, choose Route tables.

Step 33
Select lab-rtb-private1-us-east-1a route table.

Step 34
Choose Routes tab and verify destination 0.0.0.0/0 → NAT Gateway.

Step 35
Choose Subnet associations tab.

Step 36
Choose Edit subnet associations.

Step 37
Select lab-subnet-private2 along with existing subnet.

Step 38
Choose Save associations.

Step 39
Select lab-rtb-public route table.

Step 40
Verify route 0.0.0.0/0 → Internet Gateway.

Step 41
Choose Subnet associations tab.

Step 42
Choose Edit subnet associations.

Step 43
Select lab-subnet-public2 along with existing subnet.

Step 44
Choose Save associations.

### Task 3: Create a VPC Security Group

Step 45
In left navigation pane, choose Security groups.

Step 46
Choose Create security group.

Step 47
Configure:
Security group name: Web Security Group
Description: Enable HTTP access
VPC: lab-vpc

Step 48
In Inbound rules pane, choose Add rule.

Step 49
Configure rule:
Type: HTTP
Source: Anywhere-IPv4
Description: Permit web requests

Step 50
Choose Create security group.

### Task 4: Launch a Web Server Instance

Step 51
Search and open EC2 console.

Step 52
Choose Launch instance.

Step 53
Name instance Web Server 1.

Step 54
Keep default Amazon Linux 2023 AMI.

Step 55
Keep instance type t2.micro.

Step 56
Select key pair vockey.

Step 57
Edit Network settings:
Network: lab-vpc
Subnet: lab-subnet-public2
Auto-assign public IP: Enable

Step 58
Under Firewall, select existing security group Web Security Group.

Step 59
Keep default storage settings.

Step 60
Expand Advanced details.

Step 61
Paste user data script:

#!/bin/bash
# Install Apache Web Server and PHP
dnf install -y httpd wget php mariadb105-server
# Download Lab files
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-ACCLFO-2/2-lab2-vpc/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
# Turn on web server
chkconfig httpd on
service httpd start

Step 62
Choose Launch instance.

Step 63
Choose View all instances.

Step 64
Wait until status shows 2/2 checks passed.

Step 65
Select Web Server 1.

Step 66
Copy Public IPv4 DNS.

Step 67
Open browser and paste DNS.

Step 68
Verify webpage displaying AWS logo and metadata.

## Output Screenshots (Attach 3)

### Screenshot 1: VPC and Subnet Details

<img width="1913" height="1148" alt="Screenshot 2026-02-13 201128" src="https://github.com/user-attachments/assets/aa19748c-5209-4e06-a900-bd88a8be723b" />


---

### Screenshot 2: EC2 Instance Running

<img width="1919" height="1089" alt="Screenshot 2026-02-13 202059" src="https://github.com/user-attachments/assets/c751baf2-f059-4470-927a-4003c7263fe7" />


---

### Screenshot 3: Web Server Output in Browser

<img width="1916" height="1141" alt="Screenshot 2026-02-13 203713" src="https://github.com/user-attachments/assets/ee616d28-ddc1-4784-a466-b4e38ec427ff" />


---

## Result 

This experiment successfully demonstrated the creation of a custom VPC and deployment of a public-facing web server in AWS. By configuring networking components such as subnets, route tables, and security groups, and by launching an EC2 instance with a web server, the basic architecture of a cloud-hosted application was understood.
