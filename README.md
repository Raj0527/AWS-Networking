# AWS-Networking

# AWS Networking Lab Project

## Overview
As an **AWS Solutions Architect**, it's essential to understand the relationship between various AWS networking components and their functionality. In this project, I have created an **Amazon Virtual Private Cloud (VPC)** with both **public and private subnets**, an **internet gateway**, and a **NAT gateway**. This setup forms the basis of AWS networking architecture, covering critical concepts like infrastructure design, routing, and security.

The final architecture for this lab environment is represented in the following diagram:



## Objectives
After completing this lab, I gained the skills to:
- Create an Amazon VPC and configure networking components.
- Set up public and private subnets.
- Configure routing tables and gateways.
- Launch and connect to Amazon EC2 instances in public and private subnets securely.

---

## Project Tasks
Each task below details the steps I performed to build this networked environment on AWS.

### Task 1: Create an Amazon VPC
I began by creating an Amazon VPC to serve as a virtual network in the AWS Cloud:
1. Defined a VPC with a specific IPv4 CIDR block.
2. Ensured the VPC is isolated from other virtual networks in AWS, which forms the base for subsequent configurations.

### Task 2: Create Public and Private Subnets
I created both public and private subnets to isolate resources based on their accessibility needs:
1. Assigned a CIDR block to each subnet within the VPC's IP range.
2. Placed each subnet within a specified Availability Zone to ensure high availability.

### Task 3: Create an Internet Gateway
To enable internet access for the resources in the public subnet:
1. I created an internet gateway and attached it to the VPC.
2. This gateway serves as the bridge between the public subnet and external internet traffic.

### Task 4: Route Internet Traffic in the Public Subnet to the Internet Gateway
To route internet-bound traffic from the public subnet:
1. I created a route table and added a route that directs all internet traffic to the internet gateway.
2. Associated this route table with the public subnet to apply these routing rules.

### Task 5: Create a Public Security Group
To manage network traffic to the public instances:
1. I set up a security group allowing inbound traffic on specific ports like HTTP (80) and SSH (22).
2. Assigned this security group to my Amazon EC2 instance in the public subnet.

### Task 6: Launch an Amazon EC2 Instance into a Public Subnet
For testing internet access:
1. I launched an EC2 instance in the public subnet with a public IPv4 address.
2. Configured the instance to interact with external resources over the internet.

### Task 7: Connect to a Public Instance via HTTP
To validate connectivity and test the web server setup:
1. I configured the inbound rules of the public security group to allow HTTP access on port 80.
2. Connected to the instance's Apache web server page, confirming internet access and HTTP functionality.

### Task 8: Connect to the Public EC2 Instance via Session Manager
To access the instance securely without relying on SSH:
1. I used AWS Systems Manager Session Manager, which provided access to the EC2 instance console through the AWS Management Console.
2. This setup enhanced security by avoiding the need to expose SSH ports.

### Task 9: Create a NAT Gateway and Configure Private Subnet Routing
For instances in the private subnet needing internet access:
1. I created a NAT gateway in the public subnet.
2. Configured a route table with a route that directs non-local traffic from the private subnet to the NAT gateway.
3. Associated this route table with the private subnet, allowing internet access through the NAT gateway while keeping the instances isolated from inbound internet traffic.

### Task 10: Create a Security Group for Private Resources
To secure resources in the private subnet:
1. I created a security group that allows HTTP traffic from the instances in the public security group.
2. This setup supports multi-tiered architecture by allowing secure traffic from public to private resources without exposing the private subnet to the internet.

### Task 11: Launch an Amazon EC2 Instance into a Private Subnet
For internal-facing resources:
1. I launched an EC2 instance in the private subnet, ensuring it remains isolated from direct internet access.
2. This instance can only be accessed by instances within the VPC or using Systems Manager Session Manager.

### Task 12: Connect to the Private EC2 Instance using Session Manager
To access the instance securely:
1. I used AWS Systems Manager Session Manager to connect to the private instance.
2. This approach allowed secure and managed access without requiring a public IP or internet-facing access.

---

## Conclusion
This project involved creating a VPC with both public and private subnets, enabling the flexibility to launch tasks and services based on specific accessibility needs. Instances in private subnets can access external resources via a NAT gateway, maintaining isolation and enhancing security.

## Author
I performed this lab as a hands-on project to showcase my AWS networking skills, including VPC setup, subnet configuration, routing, and security best practices.
