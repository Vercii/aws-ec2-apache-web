# AWS EC2 Apache + PHP Portfolio Project Commands

This file lists all the commands I used to set up my cloud portfolio project on AWS EC2.  
Each command has an explanation about **what it does** and **why it’s important**.

---
## 1. SSH into EC2
```bash
ssh -i ~/.ssh/cloud-portfolio-key.pem ec2-user@<PUBLIC_IP>
```

## 2. Update the server packages
```bash
sudo yum update -y
