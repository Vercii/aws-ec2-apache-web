# AWS Management Console Notes – EC2 Portfolio Project

This document summarizes the steps I performed in the **AWS Management Console** to set up and manage my EC2 portfolio server.

---

## 1. Launching an EC2 Instance

1. Go to **EC2 - Instances - Launch Instances**.  
2. Choose **Amazon Linux 2023** as the operating system.  
3. Select instance type:
   - I chose **t3.micro** for testing.  
4. Configure key pair:
   - Created a new **key pair** for SSH access (`cloud-portfolio-key.pem`).  
   - Downloaded the key securely since this is needed to log in later.  
5. Configure security group:
   - Added **HTTP (port 80)** to allow web traffic to my website.  
6. Click **Launch** to start the instance.

---

## 2. Viewing and Managing Instances

- On the **EC2 - Instances** page, you can see:
  - **Instance State:** Running, Stopped, etc.  
  - **Public IPv4:** the IP to access the server in a browser.  
- Clicking on an instance gives details like:
  - **Instance ID**  
  - **Elastic IP association**  
  - **Security groups**  

---

## 3. Security Groups

- Security groups act as a firewall for your instance.  
- For my project, I configured:
  - **SSH (port 22)** - to connect via terminal  
  - **HTTP (port 80)** - to allow browsers to access my website  

---

## 4. Elastic IP

1. Go to **EC2 - Elastic IPs - Allocate Elastic IP address**  
2. Click **Allocate** to get a new static IP.  
3. Associate it with your **running EC2 instance**:  
   - Select the instance  
   - Choose private IP (default is fine)  
4. Once associated:
   - The EC2 instance now has a permanent public IP.
   - Added as a link in the release package.

The Elastic IP remains the same even if the instance is stopped and started, AS LONG AS IT STAYS ATTACHED.  

---

## 5. Stopping and Starting the Instance

- **Stop Instance:**  
  - Select instance - **Instance state - Stop instance**  
  - The server stops running, but Elastic IP stays attached  
- **Start Instance:**  
  - Select instance - **Instance state - Start instance**  
  - The server boots up again, keeping the same Elastic IP  

The website link will remain valid because the Elastic IP does not change.  

---

### ✅ Summary

- **EC2 instance**: virtual server for hosting portfolio  
- **Security groups**: firewall to control traffic  
- **Elastic IP**: permanent public IP for a stable link  
- **Instance state management**: stop/start without losing setup  

This workflow allows me to **host a dynamic portfolio website** on AWS EC2 and safely share a permanent link.
