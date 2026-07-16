### 🚀 Production-Inspired Cloud-Native Platform on Google Kubernetes Engine (GKE)

A production-inspired Kubernetes platform demonstrating Infrastructure as Code, GitOps, DevSecOps, Progressive Delivery, Observability, Runtime Security, and Automated Platform Operations.

<!-- ![Project Overview](docs/images/Canary-vs-blue-green.gif "Project Demo") -->

---
## 📖 Project Overview

This repository demonstrates how a modern cloud-native platform can be built
using production-inspired platform engineering practices on Google Kubernetes
Engine (GKE).

The project provisions infrastructure using Terraform, deploys applications
through GitOps with Argo CD, secures workloads using Kyverno and External
Secrets, implements Progressive Delivery with Argo Rollouts, monitors the
platform using Prometheus and Grafana, and automates operational tasks such as
autoscaling, certificate management, and cost visibility.

Rather than focusing on deploying a single application, this project showcases
the end-to-end lifecycle of designing, deploying, securing, observing, and
operating a Kubernetes platform.

---
### Solution Architecture

The following architecture illustrates the complete platform deployment on GCP.
![Architecture Diagram](docs/images/platform_solution.png "Platform Architecture")

---
###  Platform Highlights

<p align="left">

![Google Kubernetes Engine](https://img.shields.io/badge/Google_Kubernetes_Engine-GKE-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-IaC-844FBA?style=for-the-badge&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI/CD-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-GitOps-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![Gateway API](https://img.shields.io/badge/Gateway_API-Traffic_Management-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Argo Rollouts](https://img.shields.io/badge/Argo_Rollouts-Progressive_Delivery-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![Kyverno](https://img.shields.io/badge/Kyverno-Policy_as_Code-326CE5?style=for-the-badge)
![Falco](https://img.shields.io/badge/Falco-Runtime_Security-00ADEF?style=for-the-badge)
![External Secrets](https://img.shields.io/badge/External_Secrets-Secrets_Management-4CAF50?style=for-the-badge)
![Prometheus](https://img.shields.io/badge/Prometheus-Monitoring-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-Dashboards-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Alertmanager](https://img.shields.io/badge/Alertmanager-Alerts-E6522C?style=for-the-badge)
![Kubecost](https://img.shields.io/badge/Kubecost-Cost_Optimization-00A36C?style=for-the-badge)
![KEDA](https://img.shields.io/badge/KEDA-Event_Driven_Autoscaling-326CE5?style=for-the-badge)
![cert-manager](https://img.shields.io/badge/cert--manager-TLS_Automation-4285F4?style=for-the-badge)

</p>

---
## 📂 Repository Structure

This portfolio is organized into four repositories, each representing a core layer of a production-inspired Platform Engineering ecosystem.

```text
Platform Engineering Portfolio
│
├── platform-infra/                    # Infrastructure as Code
│   ├── terraform/
│   │   ├── environments/
│   │   └── modules/
│   └── .github/workflows/
│
├── gitops-microservices-platform/     # GitOps & Kubernetes Platform
│   ├── apps/
│   ├── infrastructure/
│   ├── platform/
│   ├── security/
│   ├── governance/
│   ├── automation/
│   └── argocd/
│
├── voting-app/                        # Application Source Code
│   ├── vote/
│   ├── result/
│   ├── worker/
│   └── .github/workflows/
│
└── platform-automation/               # Day-2 Platform Operations
    ├── automation/
    ├── reports/
    └── scripts/
```

| Repository | Description |
|------------|-------------|
| **platform-infra** | Terraform modules and environment configurations for provisioning Google Cloud infrastructure and installing core platform components. |
| **gitops-microservices-platform** | GitOps repository containing Kubernetes manifests, Argo CD ApplicationSets, platform services, security policies, governance, and environment-specific configurations. |
| **voting-app** | Polyglot microservices application with CI pipelines for building, testing, security scanning, and publishing container images. |
| **platform-automation** | Python-based platform automation for operational tasks, scheduled jobs, health checks, reporting, and Day-2 platform operations. |

---
### 📂 Project Repositories

| Repository | Purpose | Link |
|------------|---------|------|
| 🏗️ Infrastructure | Terraform modules provisioning the complete GCP platform | https://github.com/stackcouture/platform-infra |
| 🚀 GitOps | ArgoCD applications, ApplicationSets, Kustomize overlays and platform manifests | https://github.com/stackcouture/gitops-microservices-platform |
| 🗳️ Voting Application | Vote, Worker and Result microservices with Kubernetes manifests | https://github.com/stackcouture/voting-app |
| 🤖 Platform Automation | Kubernetes CronJobs, Slack notifications, backup automation and operational scripts | https://github.com/stackcouture/platform-automation |

---
### 📚 Documentation

Explore the platform through the following documentation.

| Document                                                   | Description                                                                                                                           |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 📘 [PROJECT_OVERVIEW.md](docs/PROJECT_OVERVIEW.md)         | Complete overview of the platform, goals, repository organization, and key capabilities.                                              |
| 📂 [REPOSITORY_STRUCTURE.md](docs/REPOSITORY_STRUCTURE.md) | Multi-repository architecture, repository organization, responsibilities, relationships, layered architecture, and design principles. |
| 🏗️ [ARCHITECTURE.md](docs/ARCHITECTURE.md)                | Platform architecture, design principles, and component interactions.                                                                 |
| ☸️ [KUBERNETES.md](docs/KUBERNETES.md)                     | Kubernetes cluster design, namespaces, workloads, scheduling, storage, and platform services.                                         |
| ☁️ [INFRASTRUCTURE.md](docs/INFRASTRUCTURE.md)             | Terraform modules, environment layout, GKE provisioning, networking, IAM, and cloud resources.                                        |
| 🚀 [GITOPS.md](docs/GITOPS.md)                             | GitOps workflow, Argo CD, ApplicationSets, Kustomize, and deployment strategy.                                                        |
| ⚙️ [CICD.md](docs/CICD.md)                                 | GitHub Actions workflows, container builds, security scanning, SBOM generation, image signing, and deployment automation.             |
| 🔒 [SECURITY.md](docs/SECURITY.md)                         | Platform security, Kyverno policies, Falco runtime security, External Secrets, RBAC, and certificate management.                      |
| 🌐 [NETWORKING.md](docs/NETWORKING.md)                     | Gateway API, ingress, TLS automation, DNS, and traffic management.                                                                    |
| 📊 [OBSERVABILITY.md](docs/OBSERVABILITY.md)               | Monitoring, logging, metrics, dashboards, alerting, and operational visibility.                                                       |
| 📈 [AUTOSCALING.md](docs/AUTOSCALING.md)                   | Horizontal Pod Autoscaler (HPA), KEDA, Cluster Autoscaler, and scaling strategies.                                                    |
| 🏛️ [DECISIONS.md](docs/DECISIONS.md)                      | Architecture Decision Records (ADRs), design trade-offs, and technology choices.                                                      |


---
## 🚀 Platform Capabilities

| Area | Technologies |
|------|--------------|
| ☁️ Infrastructure | Terraform, Google Cloud Platform (GCP) |
| ☸️ Kubernetes | Google Kubernetes Engine (GKE), Kubernetes |
| 🔄 GitOps | Argo CD, ApplicationSets, Kustomize |
| ⚙️ Continuous Integration | GitHub Actions |
| 🚀 Progressive Delivery | Argo Rollouts |
| 🔒 Security | Kyverno, Falco, RBAC |
| 🔑 Secrets Management | External Secrets Operator, Google Secret Manager, Vault |
| 🌐 Networking | Gateway API, NGINX Gateway Fabric, cert-manager |
| 📊 Observability | Prometheus, Grafana, Alertmanager |
| 📈 Autoscaling | Horizontal Pod Autoscaler (HPA), KEDA, Cluster Autoscaler |
| 💾 Data Platform | PostgreSQL, Redis |
| 💰 Cost Optimization | Kubecost |
| 🤖 Platform Automation | Python Automation, Kubernetes CronJobs |

---
## ✨ Platform Features

| Feature | Description |
|---------|-------------|
| 🚀 Infrastructure as Code | Provisions Google Cloud infrastructure using reusable Terraform modules |
| ☸️ Private GKE Cluster | Deploys workloads on a private Google Kubernetes Engine cluster |
| 🔄 GitOps Deployment | Uses Argo CD to continuously synchronize Kubernetes resources from Git |
| ⚙️ CI Pipeline | Automates build, test, vulnerability scanning, image signing, and image publishing with GitHub Actions |
| 📦 Multi-Environment Support | Manages development and production environments using Kustomize overlays |
| 🔐 Workload Identity | Provides secure authentication between Kubernetes workloads and Google Cloud services |
| 🔑 External Secret Management | Synchronizes secrets from Google Secret Manager and HashiCorp Vault using External Secrets Operator |
| 🛡️ Policy Enforcement | Enforces Kubernetes security policies using Kyverno |
| 🦅 Runtime Threat Detection | Detects suspicious runtime activity using Falco |
| 📈 Progressive Delivery | Supports Canary and Blue-Green deployments with Argo Rollouts |
| 🌐 Modern Networking | Uses Gateway API and NGINX Gateway Fabric for HTTP routing and traffic management |
| 🔒 Automatic TLS | Provisions and renews TLS certificates automatically using cert-manager and Let's Encrypt |
| 📊 Centralized Observability | Monitors applications and infrastructure with Prometheus, Grafana, and Alertmanager |
| 📉 Event-Driven Autoscaling | Scales worker pods dynamically using KEDA based on Redis queue length |
| 📈 Horizontal Autoscaling | Scales application pods automatically using Horizontal Pod Autoscaler (HPA) |
| ☁️ Cluster Autoscaling | Automatically adjusts GKE node capacity based on workload demand |
| 💰 Cost Monitoring | Tracks Kubernetes resource utilization and costs with Kubecost |
| 🗄️ Database Monitoring | Monitors PostgreSQL and Redis using Prometheus exporters |
| 📚 Architecture Documentation | Includes comprehensive documentation covering architecture, infrastructure, GitOps, networking, security, observability, autoscaling, and architectural decisions |

---
## 📸 Demo Screenshots

### 🏗️ Platform Architecture

<p align="left">
  <img src="assets/screenshots/architecture.png" width="550" alt="Architecture">
</p>

---
### 🚀 GitOps with Argo CD
<b> ArgoCD Output</b>
<p align="left">
  <img src="assets/screenshots/argocd-output.png" width="650" alt="ArgoCD Output">
</p>

<b>Vote ArgoCD</b>
<p align="left">
  <img src="assets/screenshots/vote-argocd.png" width="650" alt="Vote ArgoCD">
</p>
<b>Worker ArgoCD</b>
<p align="left">
  <img src="assets/screenshots/worker-argocd.png" width="650" alt="Worker ArgoCD">
</p>
<b>Result ArgoCD</b>
<p align="left">
  <img src="assets/screenshots/result-argocd.png" width="650" alt="Result ArgoCD">
</p>

---
### 🚀 Argo Rollouts Strategy
<b>Blue-Green Deployment</b>
<p align="left">
  <img src="assets/screenshots/blue-green-deployment.gif" width="650" alt="Blue-Green Deployment">
</p>
<b>Canary Deployment</b>
<p align="left">
  <img src="assets/screenshots/canary-deployment.gif" width="650" alt="Canary Deployment">
</p>

---
## Learning Outcomes

Over the past months, I designed, deployed, troubleshot, and operated a production-style Platform Engineering environment on **Google Cloud Platform (GCP)**. This project provided hands-on experience across the complete software delivery lifecycle—from infrastructure provisioning to Kubernetes operations, GitOps, security, observability, and automation.

---

## Skills Gained

| Area                             | Learning Outcomes                                                                                                                                                                 |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Infrastructure & Cloud**       | Designed modular Terraform infrastructure, managed remote state, configured VPC networking, Cloud NAT, IAM, Workload Identity Federation, and resolved cloud provisioning issues. |
| **Platform Engineering**         | Built a production-ready Kubernetes platform integrating GitOps, observability, security, autoscaling, backup, and shared platform services.                                      |
| **GitOps & Continuous Delivery** | Implemented GitOps with ArgoCD and Kustomize, configured Argo Rollouts, and learned declarative deployment and reconciliation workflows.                                          |
| **CI/CD & DevSecOps**            | Developed GitHub Actions pipelines for automated testing, container builds, vulnerability scanning, SBOM generation, image signing, and GitOps updates.                           |
| **Security**                     | Implemented Policy as Code, RBAC, Workload Identity Federation, External Secrets, runtime security, and secure software supply chain practices.                                   |
| **Observability**                | Built centralized monitoring using Prometheus, Grafana, Alertmanager, ServiceMonitors, and database exporters for operational visibility.                                         |
| **Reliability**                  | Implemented backup and recovery, autoscaling, cost optimization, and operational best practices for production environments.                                                      |

---

## Troubleshooting Experience

Throughout the project, I investigated and resolved real-world engineering challenges, including:

* Terraform provisioning failures
* Google Cloud quota limitations
* IAM permission and authentication issues
* Kubernetes scheduling and resource allocation problems
* Node pools, taints, tolerations, and affinity configuration
* Helm deployment failures
* DNS, Gateway API, and ingress configuration
* TLS certificate issuance and renewal
* External Secrets synchronization
* Persistent storage provisioning
* Container registry authentication
* GitOps synchronization and reconciliation
* Progressive deployment configuration
* Monitoring and alerting configuration
* Kubernetes networking and traffic routing

---
## Key Takeaways

Through this project, I strengthened my ability to:

* Build production-grade cloud infrastructure using Infrastructure as Code.
* Design and operate Kubernetes platforms following Platform Engineering principles.
* Implement GitOps-based application delivery using ArgoCD.
* Build secure CI/CD pipelines with integrated DevSecOps practices.
* Apply observability, automation, and reliability best practices.
* Troubleshoot complex cloud-native infrastructure systematically.
* Integrate infrastructure, Kubernetes, GitOps, CI/CD, security, and observability into a cohesive Platform Engineering platform.

---
## Acknowledgements

The sample application used in this portfolio is based on Docker's Example Voting App.

- Original project: https://github.com/dockersamples/example-voting-app
- Original authors: Docker, Inc.
- License: Apache License 2.0

This repository extends the original sample by implementing a production-oriented Platform Engineering solution on Google Cloud Platform, including Infrastructure as Code (Terraform), GitOps with Argo CD, CI/CD with GitHub Actions, Kubernetes platform services, security, observability, progressive delivery, backup and disaster recovery, cost optimization, and platform automation.

---