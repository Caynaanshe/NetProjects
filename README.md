# AWS Networking Project

## Overview
This project demonstrates the deployment of a multi-tier web application architecture on AWS using **AWS CloudFormation**. It includes the following components:
- A Virtual Private Cloud (VPC) with public and private subnets.
- Security Groups to enforce access controls.
- NAT Gateway for secure internet access from private subnets.
- An EC2-based web server running Apache
- An RDS MySQL database.
- An Application Load Balancer (ALB) for traffic distribution.

The project is designed to be scalable, secure, and cost-effective, leveraging AWS Free Tier resources where possible.

---

## Features
- Fully automated infrastructure setup using CloudFormation.
- Multi-tier architecture with separate web and database layers.
- Secure communication between tiers using Security Groups.
- High availability by spreading resources across multiple Availability Zones.
- Elastic IP for consistent access to the web server.
- Application Load Balancer for traffic distribution and scalability.

---

## Architecture Diagram
![arhcitecture-diagram JPEG](https://github.com/user-attachments/assets/f42a9a26-52a7-4ec9-b3b2-099cb262b5d6)

---

## Prerequisites
- An active AWS account.
- AWS CLI installed and configured (optional for advanced users).
- Basic knowledge of AWS services such as VPC, EC2, RDS, and ALB.

---

## Deployment Steps

### **1. Clone the Repository**
Clone this repository to your local machine:
```bash
git clone https://github.com/<your-username>/aws-networking-project.git
cd aws-networking-project
```

### **2. Deploy the CloudFormation Template**
1. Log in to the AWS Management Console.
2. Navigate to the **CloudFormation** service.
3. Click on **Create Stack** and choose "With new resources (standard)".
4. Upload the `main-template.yaml` file located in the `cloudformation/` directory.
5. Follow the prompts and provide necessary parameters (e.g., key pair name, database credentials).
6. Wait for the stack creation process to complete.

### **3. Access the Web Server**
- Once the stack is deployed, navigate to the EC2 Dashboard.
- Find the public IP or DNS name of the EC2 instance hosting the web server.
- Open a browser and access the server:


## Project Structure
```plaintext
aws-networking-project/
├── cloudformation/
│   └── main-template.yaml        # CloudFormation template
├── docs/
│   ├── architecture-diagram.png # Architecture diagram (optional)
│   └── troubleshooting.md       # Notes on troubleshooting
├── README.md                    # Project documentation
└── LICENSE                      # License file (optional)
```

---

## Security Groups Configuration
- **Web Server Security Group**:
  - Allows inbound HTTP (port 80) and HTTPS (port 443) traffic from `0.0.0.0/0`.
- **Database Security Group**:
  - Restricts inbound MySQL traffic (port 3306) to the Web Server Security Group.

---

## Troubleshooting
1. **Web Server Not Accessible**:
   - Ensure the security group attached to the EC2 instance allows inbound HTTP/HTTPS traffic.
   - Verify the public subnet’s route table routes `0.0.0.0/0` to the Internet Gateway.
2. **Database Connection Issues**:
   - Ensure the database is deployed in the private subnet.
   - Verify the Web Server Security Group is specified as the source in the Database Security Group.
3. **CloudFormation Stack Fails**:
   - Check the events tab in the CloudFormation console for specific error messages.
   - Ensure you have provided valid parameters during stack creation.

---


## Contact
For questions or suggestions, feel free to reach out:
- GitHub: https://github.com/Caynaanshe
- Email: mohamedabdirahmanali1@gmail.com

