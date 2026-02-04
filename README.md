# EC2 Beginner Guide with Terraform 🚀

## 1. What is Amazon EC2?

**Simple definition**  
Amazon EC2 (Elastic Compute Cloud) is like **renting a virtual computer** in the cloud. You don’t buy hardware; you create servers on demand in AWS and pay only while they run.

**Why EC2 is used**
- Scalable servers for websites, APIs, and applications
- On‑demand labs for learning Linux, DevOps, and cloud
- Flexible OS choices (Ubuntu, Amazon Linux, Windows)
- Pay‑as‑you‑go pricing

**Real‑world use cases**
- Hosting a portfolio website or blog
- Running backend services (Node.js, Django, Spring Boot)
- CI/CD tools like Jenkins, GitLab Runner
- Practice machines for Docker, Kubernetes, Ansible

---

## 2. Core Components of EC2

- **AMI** – Operating system image  
- **Instance type** – CPU and RAM size  
- **Key pair** – SSH authentication file (.pem)  
- **Security group** – Virtual firewall  
- **VPC & subnet** – Network and segment  
- **Public IP** – Internet‑reachable address  
- **EBS volume** – Storage disk  
- **IAM role** – Permissions for AWS services  

---

## 3. Manual EC2 Creation (AWS Console)

1. Login to AWS Console  
2. Open EC2 → Launch Instance  
3. Name: `Manual-EC2-Server`  
4. AMI: Ubuntu 24.04 / Amazon Linux (Free Tier)  
5. Instance type: `t2.micro`  
6. Create key pair (`.pem`)  
7. Security group:
   - SSH 22 → My IP
   - HTTP 80 → Anywhere (optional)
8. Storage: default 8 GB
9. Launch instance

---

## 4. Connect to EC2 (SSH)

```bash
chmod 400 my-ec2-key.pem
ssh -i my-ec2-key.pem ubuntu@PUBLIC_IP
```

---

## 5. Terraform EC2 Setup

### Requirements
- AWS account + IAM user
- AWS CLI configured
- Terraform installed

### Terraform config (ec2.tf)

```hcl
provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "ec2" {
  ami           = "ami-0f5ee92e2d63afc18"
  instance_type = "t2.micro"

  tags = {
    Name = "Simple-EC2"
  }
}
```

### Terraform commands

```bash
terraform init
terraform plan
terraform apply
terraform destroy
```

---

## 6. Manual vs Terraform

| Aspect | Manual | Terraform |
|------|-------|-----------|
| Creation | Console | Code |
| Repeatable | No | Yes |
| Version control | No | Yes |
| Destroy | Console | terraform destroy |

---

## 7. Summary

This guide covers:
- EC2 basics
- Manual EC2 creation
- SSH access
- Terraform‑based EC2 automation


