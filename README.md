# 🚀 SimpleTimeService - DevOps Project

## 📌 Overview

This project demonstrates an end-to-end DevOps workflow by building, containerizing, and deploying a simple web service using modern tools and best practices.

The application returns the current timestamp and the visitor's IP address in JSON format.

This project showcases:

* Infrastructure as Code (Terraform)
* Containerization (Docker)
* CI/CD Automation (GitHub Actions)
* Cloud Deployment (AWS)

---

## 🧱 Architecture

The application is deployed using the following architecture:

* VPC with public and private subnets
* Application running in private subnet
* Load Balancer in public subnet for external access
* Docker container deployed via ECS (Fargate)
* CI/CD pipeline using GitHub Actions

---

## ⚙️ Tech Stack

| Category       | Tool           |
| -------------- | -------------- |
| Language       | Node.js        |
| Container      | Docker         |
| CI/CD          | GitHub Actions |
| IaC            | Terraform      |
| Cloud Provider | AWS            |
| Registry       | DockerHub      |

---

## 📁 Project Structure

```
.
├── app/                # Application source code
│   ├── index.js
│   ├── package.json
│   └── Dockerfile
│
├── terraform/          # Infrastructure as Code
│   ├── main.tf
│   ├── variables.tf
│   └── terraform.tfvars
│
└── .github/workflows/  # CI/CD Pipeline
    └── ci-cd.yml
```

---

## 🚀 Application Details

### Endpoint

```
GET /
```

### Response

```json
{
  "timestamp": "2026-01-01T12:00:00.000Z",
  "ip": "client-ip-address"
}
```

---

## 🔧 Prerequisites

Ensure the following tools are installed:

* Git → https://git-scm.com/
* Docker → https://docs.docker.com/get-docker/
* Terraform → https://developer.hashicorp.com/terraform/downloads
* AWS CLI → https://aws.amazon.com/cli/

---

## 🔐 AWS Setup

Configure AWS credentials:

```bash
aws configure
```

Provide:

* Access Key
* Secret Key
* Region

⚠️ Do NOT commit credentials to the repository.

---

## 🐳 Run Application Locally

### 1. Build Docker Image

```bash
cd app
docker build -t simple-time-service .
```

### 2. Run Container

```bash
docker run -p 3000:3000 simple-time-service
```

### 3. Access

```
http://localhost:3000
```

---

## ☁️ Deploy Infrastructure (Terraform)

### 1. Navigate to Terraform Directory

```bash
cd terraform
```

### 2. Initialize

```bash
terraform init
```

### 3. Plan

```bash
terraform plan
```

### 4. Apply

```bash
terraform apply
```

Type `yes` when prompted.

---

## 🌐 Access Application

After deployment, Terraform outputs the Load Balancer URL.

Open in browser:

```
http://<load-balancer-url>
```

---

## 🔄 CI/CD Pipeline

This project uses GitHub Actions for automation.

### Pipeline Steps:

1. Trigger on push to `main`
2. Build Docker image
3. Push image to DockerHub
4. Deploy infrastructure using Terraform

### Required Secrets

Add the following in GitHub:

* `DOCKER_USERNAME`
* `DOCKER_PASSWORD` (Docker access token)
* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`

---

## 🔐 Security Considerations

* No credentials stored in code
* Uses GitHub Secrets for sensitive data
* Application runs as non-root user in container

---

## ⚡ Design Decisions

* **ECS Fargate** chosen for serverless container management
* **Terraform** used for reproducible infrastructure
* **Docker** ensures consistent runtime environment
* **CI/CD pipeline** automates deployment

---

## 🌟 Possible Improvements

* Auto-scaling configuration
* Monitoring (CloudWatch)
* Remote Terraform backend (S3 + DynamoDB)
* Blue/Green deployments
* Health checks

---

## 🧹 Cleanup

To avoid AWS charges:

```bash
terraform destroy
```

---

## 👩‍💻 Author

**Aditi Sulke**

---

## 📌 Notes

This project was created as part of a DevOps assessment to demonstrate practical knowledge of modern cloud-native workflows and infrastructure automation.

---
