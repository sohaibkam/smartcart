# 🛒 SmartCart — Cloud-Native E-commerce Platform with Secure CI/CD & Monitoring

SmartCart is a fully containerized, cloud-native e-commerce microservices application built to simulate a real-world, production-grade deployment environment. It integrates modern DevOps practices, including infrastructure-as-code, secure CI/CD pipelines, observability, and scalable architecture using AWS EKS.

---

##  Project Purpose

In a world where users expect **zero-downtime** shopping experiences and businesses demand **rapid, secure deployments**, SmartCart was built as a hands-on project to demonstrate:

- How to design and deploy a **resilient microservices architecture**
- How to implement **end-to-end CI/CD automation** with security in mind
- How to integrate **real-time observability** using Prometheus, Grafana, and Loki
- How to enforce DevOps best practices in **cloud-native production setups**

---

##  Use Case & Overview

SmartCart acts as an **e-commerce backend** supporting the following:
- **Product catalog microservice**
- **User account service**
- **Cart and checkout workflows**
- **Order processing and inventory updates**
- A PostgreSQL backend for relational data
- A Redshift-based analytics pipeline for BI/dashboard use

These services were chosen to reflect typical business-critical modules in a modern web application.

---

## 🛠️ Tech Stack

| Layer               | Tools / Technologies                                |
|---------------------|-----------------------------------------------------|
| **Cloud Platform**   | AWS (EKS, S3, IAM, VPC, Redshift, RDS/PostgreSQL)   |
| **Containerization** | Docker                                              |
| **Orchestration**    | Kubernetes (EKS)                                    |
| **IaC**              | Terraform                                           |
| **CI/CD**            | GitHub Actions, Canary Deployments via K8s         |
| **Monitoring**       | Prometheus, Grafana, Loki                           |
| **Security**         | IAM Roles, S3 Encryption, Private Subnets, RBAC     |
| **Database**         | PostgreSQL (OLTP), Amazon Redshift (Analytics)     |

---

## Features & Highlights

### Infrastructure
- Created fully managed **EKS cluster** with Terraform
- Private **VPC setup** with public/private subnets for security
- IAM roles for fine-grained access control

### CI/CD Pipelines
- CI pipeline: Test, build Docker images, push to ECR
- CD pipeline: Deploy via Helm with **canary rollout strategy**
- Secrets managed securely using GitHub Actions + AWS IAM OIDC

### Observability
- **Prometheus** for metrics
- **Grafana** for dashboards (with alerting setup)
- **Loki** for centralized logging (sidecar pattern)

### Security
- Encrypted S3 buckets for config/assets
- RBAC and namespace isolation in Kubernetes
- Secrets and credentials never stored in plaintext

---

## Microservices Overview

| Service              | Description                               | Language | Ports |
|----------------------|-------------------------------------------|----------|-------|
| **Product Service**   | Handles product listing, pricing, stock   | Python   | 8081  |
| **User Service**      | Manages registration, login, profiles     | Node.js  | 8082  |
| **Cart Service**      | Manages cart add/remove and checkout flow| Go       | 8083  |
| **Order Service**     | Handles order confirmation and status     | Python   | 8084  |

---

## Architecture (To Be Added)

A diagram showing:

- EKS with multiple namespaces/services
- CI/CD flow from GitHub to Kubernetes
- Integration with Prometheus, Grafana, Loki
- PostgreSQL (RDS) + Redshift connection
- Network layout (public vs private subnets, NAT gateway)

*(Coming soon — will be added as `/docs/architecture.png`)*

---

## 🚦 How CI/CD Works

1. **Developer commits code** → triggers GitHub Actions workflow
2. **CI job runs**: test, lint, build Docker images, push to ECR
3. **CD job runs**: deploys to EKS using Helm, with **canary strategy**
4. **Monitoring pipelines** instantly pick up changes in metrics/logs

---

## Monitoring & Logs

- Dashboards built in Grafana for:
  - App health, error rates, request latency
  - Node metrics (CPU, memory, pod status)
- Alerts set for high 5xx errors and pod restarts
- Loki enables querying app logs by label (service name, pod name)

---

## Local Development

1. Clone the repo
2. Use Docker Compose or KIND (for local Kubernetes)
3. Each service has a `README.md` under `/services/` with run commands

---

## Future Improvements

- Add frontend React app for users
- Integrate AWS WAF and Shield for added protection
- Autoscaling with HPA & Cluster Autoscaler
- CI/CD notifications to Slack or Teams

