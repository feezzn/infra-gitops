# 🚀 infra-gitops — GitOps Platform on Kubernetes (EKS)

This repository contains a **GitOps-based Kubernetes platform**, designed to manage applications declaratively using **ArgoCD**, **Helm**, and **Infrastructure as Code (Terraform)**.

The goal of this project is to **simulate a real enterprise DevOps / Platform Engineering environment**, focusing on automation, security, reliability, and operational clarity.

---

## 🧠 Core Concepts

- GitOps as the **single source of truth**
- No manual `kubectl apply` for applications
- Infrastructure and applications fully declarative
- Clear separation of concerns:
  - Infrastructure
  - Platform
  - Applications
- Security-first approach (IAM Roles, no static credentials)

---

## 🏗️ Architecture Overview

### High-level flow


🏗️ Architecture Overview
High-level flow:
```Git Repository
   ↓
ArgoCD (GitOps Controller)
   ↓
Helm Charts
   ↓
Kubernetes (EKS)
   ↓
AWS Load Balancer (ALB)
```

---

## 📦 Repository Structure

```infra-gitops/
├── apps/
│   └── myapp/
│       └── application.yaml     # ArgoCD Application (Helm-based)
├── clusters/
│   └── dev/
│       └── root-app.yaml        # App of Apps (root application)
├── README.md
```


### Structure Explanation

- **`clusters/dev/root-app.yaml`**
  - Root ArgoCD application (App of Apps pattern)
  - Responsible for bootstrapping all applications in the cluster

- **`apps/*`**
  - Each directory represents an application managed by ArgoCD
  - Applications reference external repositories (Helm charts)

---

## 🔄 GitOps Workflow

1. Developer updates Helm values or application configuration
2. Changes are pushed to Git
3. ArgoCD detects configuration drift
4. ArgoCD automatically reconciles the cluster
5. Kubernetes reflects the desired state

> No manual deployments  
> No imperative commands  
> Everything flows through Git

---

## 🔐 Security Model

- AWS access managed via **IAM Roles**
- Local access via **AssumeRole + MFA**
- CI/CD uses **OIDC (no long-lived credentials)**
- Kubernetes access controlled with RBAC
- ArgoCD UI exposed via ALB (development environment)

---

## 🛠️ Stack

- **Cloud**: AWS
- **Kubernetes**: EKS
- **GitOps**: ArgoCD
- **Templating**: Helm
- **Infrastructure as Code**: Terraform
- **CI/CD**: GitHub Actions
- **Networking**: AWS Load Balancer Controller (ALB)

---

## 🎯 Project Goals

- Practice real-world Platform Engineering patterns
- Apply GitOps principles end-to-end
- Improve Terraform, Helm and ArgoCD proficiency
- Build a reference architecture for interviews and knowledge sharing

---

## ⚠️ Disclaimer

This project is intended for **learning and demonstration purposes**.  
Some configurations (e.g. open ingress) are acceptable for **development/lab environments**, but would require additional hardening in production.

---

## 🔗 Related Repositories

- Infrastructure (Terraform): `infra`
- Application (Helm chart): `myapp`

---

## 👨‍💻 Author

Felipe  
☁️ Site Reliability / DevOps Engineer  
Focused on **secure**, **reproducible** and **operable** cloud infrastructure 🚀