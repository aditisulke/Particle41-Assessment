# 🚀 SimpleTimeService - DevOps Assessment Project

## 📌 Overview

SimpleTimeService is a lightweight backend microservice built using Node.js that returns the current timestamp and the client’s IP address in JSON format.

This project demonstrates an end-to-end DevOps workflow including application development, containerization, infrastructure provisioning, and CI/CD automation.

---

## 🧱 Architecture

The application is deployed using the following architecture:

* AWS VPC provisioned using Terraform
* Public and private subnet structure (if configured)
* EC2 instance hosting the Docker container
* Application exposed via public IP / Load Balancer
* CI/CD pipeline using GitHub Actions for automated build and deployment

---

## 🎯 Application Details

### Endpoint

```bash
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

## 📁 Project Structure

```
.
├── app/                # Node.js application
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

## 🔧 Prerequisites

Ensure the following tools are installed:

* Git → https://git-scm.com/
* Docker → https://docs.docker.com/get-docker/
* Terraform → https://developer.hashicorp.com/terraform/downloads
* AWS CLI → https://aws.amazon.com/cli/

---

## 🔐 AWS Configuration

Configure AWS credentials locally:

```bash
aws configure
```

Provide:

* AWS Access Key
* AWS Secret Key
* Region

⚠️ Do not commit credentials to the repository.

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

### 3. Access Application

Open in browser:

```
http://localhost:3000
```

---

## ☁️ Deploy Infrastructure (Terraform)

### 1. Navigate to Terraform Directory

```bash
cd terraform
```

### 2. Initialize Terraform

```bash
terraform init
```

### 3. Preview Changes

```bash
terraform plan
```

### 4. Apply Configuration

```bash
terraform apply
```

Type `yes` when prompted.

---

## 🌐 Access Deployed Application

After deployment, access the application using:

* EC2 Public IP
  OR
* Load Balancer URL (if configured)

Example:

```
http://<your-public-ip>
```

---

## 🔄 CI/CD Pipeline

This project uses GitHub Actions to automate the workflow.

### Pipeline Steps:

1. Triggered on push to `main` branch
2. Builds Docker image
3. Pushes image to DockerHub
4. (Optional) Deploys infrastructure using Terraform

### Required GitHub Secrets

Configure the following secrets in your repository:

* `DOCKER_USERNAME`
* `DOCKER_PASSWORD` (Docker access token)
* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`

---

## 🔐 Security Practices

* No credentials stored in code
* Sensitive data managed using GitHub Secrets
* Docker container runs as a non-root user

---

## ⚡ Design Decisions

* Node.js chosen for lightweight and fast API development
* Docker used for consistent and portable runtime
* Terraform used for reproducible infrastructure provisioning
* EC2 chosen for simplicity and control over deployment
* GitHub Actions used to automate CI/CD pipeline

---

## 📈 Scalability

The current architecture supports horizontal scaling. The setup can be extended using AWS Auto Scaling Groups to handle increased traffic based on demand.

---
## 🚀 Future Enhancements

The following improvements can be implemented to further enhance the project:

- Add monitoring and logging using AWS CloudWatch
- Configure a remote Terraform backend (S3 + DynamoDB) for state management and locking
- Introduce container image versioning for better release management
- Add health checks and improve fault tolerance
- Implement a CI/CD pipeline with environment-based deployments (dev/staging/production)
- Enhance security using IAM roles and least-privilege access policies

---

## 🧹 Cleanup

To avoid unnecessary cloud charges, destroy resources:

```bash
terraform destroy
```

---

## 👩‍💻 Author

**Aditi Sulke**

---

## 📌 Notes

This project was developed as part of a DevOps assessment to demonstrate practical knowledge of containerization, infrastructure as code, and CI/CD automation in a cloud environment.

---
