
# Troubleshooting Guide for AWS Networking Project

## **1. Web Server Not Accessible**
### **Symptoms:**
- You cannot access the web server via its public IP or DNS.
### **Possible Causes and Solutions:**
1. **Security Group Rules:**
   - Ensure the web server's Security Group allows inbound HTTP (port 80) and HTTPS (port 443) traffic from `0.0.0.0/0`.
   - Verify the NACL for the public subnet permits traffic on these ports.
2. **Route Table Issues:**
   - Check if the public subnet's route table includes a route to `0.0.0.0/0` via the Internet Gateway.
3. **Instance State:**
   - Confirm the EC2 instance is in a running state and not stopped or terminated.
4. **Firewall Rules:**
   - Ensure there are no restrictive firewall rules in the EC2 instance OS itself.

---

## **2. Database Connection Issues**
### **Symptoms:**
- The web server cannot connect to the RDS database.
### **Possible Causes and Solutions:**
1. **Security Group Rules:**
   - Ensure the database's Security Group allows inbound MySQL (port 3306) traffic from the web server's Security Group.
2. **Private Subnet Configuration:**
   - Verify the database is deployed in the private subnet and its route table includes a NAT Gateway for outgoing traffic.
3. **Credentials:**
   - Confirm that the correct database credentials are being used in the web server application.

---

## **3. CloudFormation Stack Fails to Deploy**
### **Symptoms:**
- The stack creation process fails or rolls back.
### **Possible Causes and Solutions:**
1. **Invalid Parameters:**
   - Double-check the parameters provided during stack creation, such as key pair name and database credentials.
2. **Resource Limits:**
   - Ensure you have not exceeded AWS Free Tier limits or default quotas (e.g., Elastic IPs, VPCs).
3. **Dependency Issues:**
   - Check the CloudFormation events log for detailed error messages and resolve any dependency issues.

---

## **4. ALB Not Distributing Traffic**
### **Symptoms:**
- Traffic is not being distributed to the web server.
### **Possible Causes and Solutions:**
1. **Target Group Health:**
   - Verify that the web server instance is registered with the ALB target group and shows as healthy.
2. **Listener Configuration:**
   - Ensure the ALB has listeners configured for HTTP (port 80) or HTTPS (port 443).
3. **Security Group Rules:**
   - Ensure the ALB's Security Group allows inbound traffic on the listener ports.

---

## **5. Cost Management Concerns**
### **Symptoms:**
- Unexpected charges appear in your AWS account.
### **Possible Causes and Solutions:**
1. **Free Tier Limits:**
   - Confirm that the resources (e.g., RDS, NAT Gateway) are within AWS Free Tier limits.
2. **Unused Resources:**
   - Delete any unused resources or test stacks to avoid unnecessary charges.
3. **Billing Alerts:**
   - Set up AWS Budgets and Billing Alerts to monitor and manage costs effectively.

---
