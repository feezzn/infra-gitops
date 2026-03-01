🚀 infra-gitops — GitOps Platform on Kubernetes (EKS)

This repository represents a GitOps-driven Kubernetes platform, designed to manage applications declaratively using ArgoCD, Helm, and Infrastructure as Code principles.
The goal of this project is to simulate an enterprise-grade DevOps / Platform Engineering setup, focusing on automation, reliability, and operational clarity.

🧠 Core Concepts
GitOps as the single source of truth
No manual kubectl deployments
Infrastructure and applications fully declarative
Separation of concerns between infra, platform and apps
Security-first approach (IAM roles, no static credentials)

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

📦 Repository Structure
```infra-gitops/
├── apps/
│   └── myapp/
│       └── application.yaml     # ArgoCD Application (Helm-based)
├── clusters/
│   └── dev/
│       └── root-app.yaml        # App of Apps (root application)
├── README.md
```

Explanation
clusters/dev/root-app.yaml
Root ArgoCD application (App of Apps pattern)
Responsible for bootstrapping all applications in the cluster
apps/*
Each directory represents an application managed by ArgoCD
Applications reference external repositories (Helm charts)

🔄 GitOps Workflow
Developer updates application configuration or Helm values
Changes are pushed to Git
ArgoCD detects drift
ArgoCD reconciles the cluster automatically
Kubernetes reflects the desired state
No manual deploys.
No imperative commands.
Everything flows through Git.

🔐 Security Model
AWS access is managed via IAM Roles
Local access uses AssumeRole + MFA
CI/CD uses OIDC (no long-lived credentials)
Kubernetes access is restricted via RBAC
ArgoCD UI exposed via ALB (dev environment)

🛠️ Stack
Cloud: AWS
Kubernetes: EKS
GitOps: ArgoCD
Templating: Helm
Infrastructure as Code: Terraform
CI/CD: GitHub Actions
Networking: ALB Ingress Controller

🎯 Goals of this Project
Practice real-world Platform Engineering patterns
Simulate enterprise DevOps workflows
Improve GitOps, Helm and Terraform proficiency
Build a reference architecture for interviews and knowledge sharing

⚠️ Disclaimer

This project is intended for learning and demonstration purposes.
Some configurations (e.g. open ingress) are acceptable for development/lab environments, but would require additional hardening in production.

📚 Related Repositories
Infrastructure (Terraform): infra
Application (Helm chart): myapp

## 👨‍💻 Author

Felipe  
☁️ Site Reliability / DevOps Engineer  
Focused on **secure**, **reproducible** and **operable** cloud infrastructure 🚀