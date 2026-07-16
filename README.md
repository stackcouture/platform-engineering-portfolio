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

| Document | Description |
|----------|-------------|
| 📘 [PROJECT_OVERVIEW.md](docs/PROJECT_OVERVIEW.md) | Complete overview of the platform, goals, repository organization, and key capabilities. |
| 🏗️ [ARCHITECTURE.md](docs/ARCHITECTURE.md) | Platform architecture, design principles, and component interactions. |
| ☸️ [KUBERNETES.md](docs/KUBERNETES.md) | Kubernetes cluster design, namespaces, workloads, scheduling, storage, and platform services. |
| ☁️ [INFRASTRUCTURE.md](docs/INFRASTRUCTURE.md) | Terraform modules, environment layout, GKE provisioning, networking, IAM, and cloud resources. |
| 🚀 [GITOPS.md](docs/GITOPS.md) | GitOps workflow, Argo CD, ApplicationSets, Kustomize, and deployment strategy. |
| ⚙️ [CICD.md](docs/CICD.md) | GitHub Actions workflows, container builds, security scanning, SBOM generation, image signing, and deployment automation. |
| 🔒 [SECURITY.md](docs/SECURITY.md) | Platform security, Kyverno policies, Falco runtime security, External Secrets, RBAC, and certificate management. |
| 🌐 [NETWORKING.md](docs/NETWORKING.md) | Gateway API, ingress, TLS automation, DNS, and traffic management. |
| 📊 [OBSERVABILITY.md](docs/OBSERVABILITY.md) | Monitoring, logging, metrics, dashboards, alerting, and operational visibility. |
| 📈 [AUTOSCALING.md](docs/AUTOSCALING.md) | Horizontal Pod Autoscaler (HPA), KEDA, Cluster Autoscaler, and scaling strategies. |
| 🏛️ [DECISIONS.md](docs/DECISIONS.md) | Architecture Decision Records (ADRs), design trade-offs, and technology choices. |

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
## How It Fits Together

The platform follows a layered architecture where each layer has a clearly defined responsibility and lifecycle.

### Infrastructure Layer

The infrastructure is provisioned using reusable **Terraform modules** and serves as the foundation of the platform. It creates and manages the networking, Kubernetes cluster, managed database, container registry, and cloud identity resources. The same Terraform modules are reused across **Development** and **Production** environments, with environment-specific configuration provided through variables.

### Platform Layer

After the infrastructure is available, the platform layer installs the shared Kubernetes services required by all workloads. These services provide continuous delivery, traffic management, security policy enforcement, runtime protection, monitoring, autoscaling, cost visibility, backup, and operational automation. Since these components are shared, they operate independently of any individual application.

### Application Layer

Applications are deployed using a **GitOps** workflow rather than manual deployment. All application manifests are version-controlled in Git, and **ArgoCD** continuously reconciles the desired state with the live Kubernetes cluster. This approach eliminates manual deployment steps and ensures deployments are repeatable, auditable, and consistent across environments.

### Separation of Responsibilities

Each layer is independently managed and can evolve without impacting the others. Infrastructure changes are isolated from platform services, while platform upgrades can be performed without modifying application code. This separation of concerns improves maintainability, scalability, and long-term platform evolution.

---
## Infrastructure Provisioning

The entire platform is provisioned using **Terraform**, providing a fully automated, repeatable, and production-ready deployment process. The infrastructure is organized into reusable modules and deployed consistently across environments using environment-specific variables.

Infrastructure provisioning includes both **Google Cloud resources** and the **Kubernetes platform services** required to operate the cluster.

### Google Cloud Infrastructure

Terraform provisions the following cloud resources:

- Virtual Private Cloud (VPC)
- Private Subnets
- Cloud Router
- Cloud NAT
- Firewall Rules
- Google Kubernetes Engine (GKE)
- Cloud SQL (PostgreSQL)
- Artifact Registry
- Cloud Storage
- IAM Roles and Service Accounts
- Workload Identity Federation

### Kubernetes Platform Components

After the GKE cluster is provisioned, Terraform automatically installs the shared platform services using the **Helm** and **Kubernetes** providers.

Platform services include:

- ArgoCD
- Argo Rollouts
- Cert-Manager
- External Secrets Operator
- NGINX Gateway Fabric
- Gateway API
- Kyverno
- Falco
- Prometheus
- Grafana
- Alertmanager
- Kubecost
- KEDA
- Reloader
- Velero
- Storage Classes
- Vault

### Infrastructure Deployment Workflow

Terraform executes the infrastructure deployment in a layered approach:

1. Provision Google Cloud infrastructure.
2. Create the GKE cluster and node pools.
3. Configure IAM and Workload Identity Federation.
4. Install Kubernetes platform components using Helm.
5. Configure storage classes, ingress, certificates, secrets, monitoring, security policies, and backup services.
6. Prepare the platform for GitOps-based application deployment with ArgoCD.

### Key Characteristics

- Fully automated infrastructure provisioning
- Modular Terraform architecture
- Environment-specific deployments
- Idempotent infrastructure changes
- Version-controlled Infrastructure as Code (IaC)
- Automated platform bootstrapping
- Production-ready Kubernetes foundation
---
## CI/CD Pipeline

The platform implements a fully automated CI/CD pipeline using **GitHub Actions**. Every change to the application source code is validated, secured, packaged, and promoted through a GitOps workflow before being deployed to the Kubernetes cluster.

### Pipeline Workflow

```text
Developer Push
      │
      ▼
GitHub Actions
      │
      ├── Checkout Source Code
      ├── Build Docker Image
      ├── Trivy Vulnerability Scan
      ├── Generate SBOM
      ├── Push Image to Artifact Registry
      ├── Sign Image with Cosign
      ├── Attest SBOM
      └── Update GitOps Repository
                │
                ▼
           ArgoCD Detects Change
                │
                ▼
      Synchronize Kubernetes Cluster
                │
                ▼
      Progressive Deployment using
           Argo Rollouts
```

### Pipeline Stages

| Stage | Description |
|--------|-------------|
| **Source Checkout** | Retrieves the latest application source code from GitHub. |
| **Container Build** | Builds a Docker container image for the application. |
| **Security Scanning** | Performs container vulnerability scanning using Trivy. |
| **SBOM Generation** | Generates a Software Bill of Materials (SBOM) in SPDX format. |
| **Container Registry** | Pushes the validated container image to Google Artifact Registry. |
| **Image Signing** | Cryptographically signs container images using Cosign keyless signing. |
| **SBOM Attestation** | Attaches the generated SBOM as an image attestation. |
| **GitOps Update** | Updates the image tag in the GitOps repository using Kustomize. |
| **Continuous Deployment** | ArgoCD automatically synchronizes the Kubernetes cluster with the updated GitOps manifests. |
| **Progressive Delivery** | Argo Rollouts performs Canary or Blue-Green deployments with automated rollout strategies. |

### Security Controls

The CI/CD pipeline integrates security throughout the software delivery lifecycle.

- Automated unit testing
- Container image vulnerability scanning with Trivy
- Software Bill of Materials (SBOM) generation
- Keyless container image signing using Cosign
- SBOM attestation
- Secure authentication to Google Cloud using Workload Identity Federation
- GitOps-based deployment with no direct cluster access

### GitOps Deployment Flow

1. A developer pushes code changes to the application repository.
2. GitHub Actions executes the CI pipeline.
3. A new container image is built and validated.
4. The image is pushed to Google Artifact Registry.
5. The image is signed and an SBOM attestation is generated.
6. The GitOps repository is automatically updated with the new image tag.
7. ArgoCD detects the Git commit and synchronizes the Kubernetes cluster.
8. Argo Rollouts performs a controlled application deployment using the configured rollout strategy.

---
## GitOps Workflow

The platform follows a **GitOps** operating model, where Git serves as the single source of truth for application and infrastructure configuration. All deployment changes are made through version-controlled repositories, ensuring that the live Kubernetes cluster continuously matches the desired state defined in Git.

Direct deployments to the cluster are not performed. Instead, **ArgoCD** continuously monitors the GitOps repository and reconciles any detected changes automatically.

---
![GitOps Diagram](docs/images/ci-cd-gitops-workflow.png "GitOps Flow")

---
### Workflow Overview

```text
Developer
    │
    ▼
Application Repository
    │
    ▼
GitHub Actions CI
    │
    ├── Build Docker Image
    ├── Execute Unit Tests
    ├── Trivy Security Scan
    ├── Generate SBOM
    ├── Cosign Image Signing
    └── Push Image to Artifact Registry
                │
                ▼
Update GitOps Repository
(Kustomize Image Tag)
                │
                ▼
ArgoCD Detects Git Commit
                │
                ▼
Synchronize Kubernetes Cluster
                │
                ▼
Argo Rollouts
(Canary / Blue-Green Deployment)
                │
                ▼
Production Workload
```

### Workflow Steps

1. A developer commits and pushes code changes to the application repository.
2. GitHub Actions validates the application by running automated tests.
3. A new container image is built and scanned for vulnerabilities using Trivy.
4. A Software Bill of Materials (SBOM) is generated, and the container image is signed using Cosign.
5. The validated image is pushed to Google Artifact Registry.
6. The CI pipeline updates the image tag in the GitOps repository using Kustomize.
7. ArgoCD detects the Git commit and synchronizes the Kubernetes cluster with the desired state.
8. Argo Rollouts performs a progressive deployment using the configured rollout strategy.
9. The application becomes available after the rollout completes successfully.

### GitOps Benefits

- Git as the single source of truth
- Declarative, version-controlled deployments
- Automated synchronization and drift detection
- Immutable deployment history
- Consistent deployments across environments
- Simplified rollback using Git history
- Progressive delivery with Argo Rollouts
- Fully automated deployment pipeline with no manual `kubectl apply`

### Repository Responsibilities

| Repository | Responsibility |
|------------|----------------|
| **Application Repository** | Stores application source code, Dockerfiles, tests, and GitHub Actions workflows. |
| **GitOps Repository** | Stores Kubernetes manifests, Kustomize overlays, ArgoCD Applications, and deployment configuration. |
| **Infrastructure Repository** | Stores Terraform modules for provisioning cloud infrastructure and platform components. |

---
## Security & Compliance

Security is embedded throughout the platform following **DevSecOps** principles. Security controls are integrated into the infrastructure, CI/CD pipeline, Kubernetes platform, and runtime environment to protect workloads, enforce organizational policies, and strengthen the software supply chain.

### Security Controls

| Category | Technologies | Purpose |
|----------|--------------|---------|
| **Identity & Access Management** | IAM, Workload Identity Federation, Kubernetes RBAC | Secure authentication and least-privilege access to cloud and Kubernetes resources. |
| **Policy Enforcement** | Kyverno | Enforce Kubernetes security policies, resource standards, and deployment best practices. |
| **Secrets Management** | External Secrets Operator, Google Secret Manager, Vault | Securely manage application secrets without storing sensitive information in Git repositories. |
| **Container Security** | Trivy | Scan container images for vulnerabilities before deployment. |
| **Software Supply Chain** | SBOM, Cosign | Generate Software Bill of Materials (SBOM) and cryptographically sign container images to verify authenticity and integrity. |
| **Runtime Security** | Falco | Monitor Kubernetes workloads for suspicious or unauthorized runtime activity. |
| **Network Security** | Private VPC, Firewall Rules, Gateway API, Network Policies | Protect workloads using controlled network access and secure traffic routing. |
| **Transport Security** | Cert-Manager, Let's Encrypt | Automate TLS certificate provisioning and renewal for encrypted communication. |

### Security Practices

The platform implements the following security best practices:

- Infrastructure as Code with version-controlled Terraform modules
- Least-privilege access using IAM and Kubernetes RBAC
- Workload Identity Federation for secure authentication without long-lived service account keys
- Policy-as-Code enforcement using Kyverno
- Container image vulnerability scanning during CI
- Software Bill of Materials (SBOM) generation for supply chain transparency
- Keyless container image signing using Cosign
- Runtime threat detection with Falco
- Centralized secrets management using External Secrets Operator
- Automated TLS certificate lifecycle management
- Private networking for critical cloud resources
- GitOps-based deployments with a fully auditable change history

### Compliance Alignment

The platform incorporates security controls commonly associated with modern cloud security and compliance frameworks, including:

- Least Privilege Access
- Defense in Depth
- Zero Trust Principles
- Infrastructure as Code (IaC)
- Policy as Code
- GitOps
- Secure Software Supply Chain
- Continuous Vulnerability Management
- Encryption in Transit
- Auditability and Change Tracking

> **Note:** This project demonstrates security practices aligned with industry standards and production-grade platform engineering. It is intended as a technical implementation and is not presented as a certified or audited compliance environment.

---
## Observability & Monitoring

The platform provides centralized observability through a comprehensive monitoring stack that collects metrics, visualizes system health, and delivers proactive alerting across infrastructure and application workloads.

Monitoring components are deployed as shared platform services, enabling consistent visibility into Kubernetes resources, application performance, and platform operations.

### Observability Stack

| Component | Purpose |
|-----------|---------|
| **Prometheus** | Collects and stores metrics from Kubernetes, applications, and platform services. |
| **Grafana** | Visualizes metrics through interactive dashboards for infrastructure and application monitoring. |
| **Alertmanager** | Processes Prometheus alerts and routes notifications based on configured alerting rules. |
| **ServiceMonitors** | Automatically discovers and scrapes metrics from Kubernetes workloads. |
| **Redis Exporter** | Exposes Redis performance and health metrics to Prometheus. |
| **PostgreSQL Exporter** | Exposes PostgreSQL database metrics for monitoring and capacity planning. |

### Monitoring Coverage

The platform continuously monitors:

- Kubernetes cluster health
- Node resource utilization
- Pod health and availability
- Application performance metrics
- HTTP request rates and response times
- CPU and memory utilization
- Persistent storage usage
- PostgreSQL performance metrics
- Redis performance metrics
- Kubernetes workload status
- Platform service availability

### Alerting Capabilities

Prometheus and Alertmanager provide proactive alerting for operational events, including:

- Pod failures and restarts
- High CPU utilization
- High memory utilization
- Application availability issues
- Database connectivity failures
- Storage capacity thresholds
- Kubernetes node health
- Service endpoint availability

### Key Capabilities

- Centralized metrics collection
- Real-time infrastructure monitoring
- Application performance monitoring
- Database and cache monitoring
- Interactive Grafana dashboards
- Automated alert generation
- Service discovery using ServiceMonitors
- Historical metrics for troubleshooting and capacity planning
- Scalable monitoring architecture for Kubernetes workloads

### Design Principles

The observability platform is designed to provide:

- **Visibility** – Comprehensive insights into infrastructure and application health.
- **Reliability** – Early detection of operational issues through automated alerting.
- **Scalability** – Automatic monitoring of newly deployed workloads.
- **Operational Efficiency** – Centralized dashboards and metrics simplify troubleshooting and performance analysis.

---
## Progressive Delivery

The platform implements **Progressive Delivery** using **Argo Rollouts**, enabling application updates to be released gradually with minimal risk. Instead of replacing all application instances at once, new versions are introduced in controlled stages, allowing validation before full production rollout.

Progressive delivery is fully integrated with the GitOps workflow, ensuring deployments remain declarative, automated, and version-controlled.

### Deployment Strategies

| Strategy | Purpose |
|----------|---------|
| **Canary Deployment** | Gradually shifts production traffic to a new application version while monitoring application health and performance. |
| **Blue-Green Deployment** | Deploys a new application version alongside the existing version and switches traffic only after successful validation. |

### Deployment Workflow

```text
Developer Push
        │
        ▼
GitHub Actions CI Pipeline
        │
        ▼
Container Image Published
        │
        ▼
GitOps Repository Updated
        │
        ▼
ArgoCD Synchronization
        │
        ▼
Argo Rollouts
        │
        ├── Deploy New Version
        ├── Shift Traffic Gradually
        ├── Validate Rollout
        └── Promote or Roll Back
        │
        ▼
Production Workload
```

### Rollout Capabilities

- Canary deployments with incremental traffic shifting
- Blue-Green deployments for zero-downtime releases
- Automated rollout progression
- Controlled production releases
- Rapid rollback to the previous stable version
- Integration with GitOps workflows
- Version-controlled deployment configuration
- Declarative rollout definitions using Kubernetes custom resources

### Benefits

- Minimized deployment risk
- Reduced application downtime
- Safer production releases
- Faster recovery from failed deployments
- Improved deployment confidence
- Consistent and repeatable release process
- Fully automated deployment lifecycle

---
## Disaster Recovery

The platform includes **backup and disaster recovery** capabilities using **Velero**, enabling Kubernetes resources and persistent data to be backed up and restored when required. This helps protect critical workloads from accidental deletion, infrastructure failures, and operational errors.

### Backup Components

| Component | Purpose |
|-----------|---------|
| **Velero** | Backs up and restores Kubernetes resources and persistent volumes. |
| **Cloud Storage** | Stores backup archives in a durable and scalable object storage bucket. |
| **Persistent Volumes** | Preserves application data for stateful workloads such as PostgreSQL and Redis. |

### Backup Scope

The backup solution protects:

- Kubernetes resources
- Namespaces
- Deployments
- Services
- ConfigMaps
- Secrets
- Persistent Volume Claims (PVCs)
- PostgreSQL data
- Redis data
- Platform configuration

### Recovery Workflow

```text
Platform Failure
        │
        ▼
Identify Recovery Point
        │
        ▼
Retrieve Backup
        │
        ▼
Restore Kubernetes Resources
        │
        ▼
Restore Persistent Data
        │
        ▼
Validate Platform Health
        │
        ▼
Resume Application Services
```
---
### Recovery Capabilities
- Scheduled platform backups
- On-demand backup creation
- Kubernetes resource restoration
- Persistent volume recovery
- Namespace-level recovery
- Application-level recovery
- Disaster recovery testing
- Version-controlled infrastructure reconstruction using Terraform

---
### Design Principles

The disaster recovery strategy is based on:

- **Automation** – Backup and restore operations are managed through Velero.
- **Reliability** – Platform resources and persistent data can be recovered from backup.
- **Repeatability** – Infrastructure can be recreated using Terraform, while Kubernetes workloads are restored using GitOps and Velero.
- **Resilience** – Stateless workloads are redeployed automatically, while stateful workloads are recovered from persistent backups.

---
## Cost Optimization

The platform incorporates cost optimization practices to improve resource efficiency while maintaining application performance and availability. By combining Kubernetes autoscaling, resource governance, and cost visibility, the platform helps reduce unnecessary cloud resource consumption.

---
### Cost Optimization Components

| Component | Purpose |
|-----------|---------|
| **Kubecost** | Provides visibility into Kubernetes resource utilization and estimated infrastructure costs. |
| **KEDA** | Scales workloads based on application demand and external events, reducing idle resource consumption. |
| **Horizontal Pod Autoscaler (HPA)** | Automatically adjusts the number of application replicas based on resource utilization. |
| **Cluster Autoscaler** | Dynamically scales Kubernetes node pools to match workload demand. |
| **Resource Requests & Limits** | Ensures efficient CPU and memory allocation while preventing resource contention. |

---
### Cost Optimization Strategies

The platform implements the following optimization techniques:

- Dynamic application scaling using KEDA
- Automatic pod scaling with Horizontal Pod Autoscaler (HPA)
- Automatic node scaling using Cluster Autoscaler
- Resource requests and limits for efficient scheduling
- Dedicated node pools for system, application, and data workloads
- Continuous cost monitoring with Kubecost
- Capacity planning using Prometheus and Grafana metrics
- Efficient scheduling of workloads based on resource requirements

---
### Cost Visibility

Kubecost provides insights into:

- CPU utilization
- Memory utilization
- Namespace-level resource consumption
- Workload-level resource consumption
- Estimated Kubernetes infrastructure costs
- Resource allocation trends
- Cost optimization opportunities

---
### Key Benefits

- Improved resource utilization
- Reduced over-provisioning
- Automatic scaling based on demand
- Better infrastructure capacity planning
- Increased workload efficiency
- Enhanced visibility into Kubernetes resource usage
- Data-driven cost optimization decisions

---
### Design Principles

The platform follows these cost optimization principles:

- **Right-Sizing** – Allocate appropriate CPU and memory resources to workloads.
- **Elasticity** – Scale applications and infrastructure based on real-time demand.
- **Visibility** – Monitor resource consumption and identify optimization opportunities.
- **Efficiency** – Maximize utilization while maintaining application performance and reliability.

---
## Platform Automation

The platform includes Python-based automation services that streamline routine operational tasks, reduce manual intervention, and improve platform reliability. These automation workflows support day-to-day platform operations by validating cluster health, generating operational reports, and executing scheduled maintenance activities.

Automation services are designed to integrate with the Kubernetes platform and cloud infrastructure, enabling consistent and repeatable operational processes.

---
### Automation Capabilities

| Automation Service | Purpose |
|--------------------|---------|
| **Cluster Health Validation** | Verifies the health of Kubernetes clusters, nodes, and workloads. |

---
### Automation Workflow

```text
Scheduled Trigger
        │
        ▼
Python Automation Service
        │
        ├── Validate Cluster Health
        ├── Check Platform Services
        ├── Verify Infrastructure Status
        ├── Collect Metrics
        ├── Generate Reports
        └── Publish Results
```
---
### Key Capabilities

- Automated platform health validation
- Kubernetes cluster status verification
- Infrastructure health checks
- Scheduled operational tasks
- Automated reporting
- Consistent operational workflows
- Reduced manual intervention
- Improved operational efficiency

---
### Design Principles

The platform automation services are designed around the following principles:

- **Automation First** – Routine operational activities are automated wherever practical.
- **Reliability** – Continuous validation helps detect issues before they impact workloads.
- **Consistency** – Standardized automation ensures repeatable operational processes.
- **Scalability** – Automation services can be extended to support additional operational use cases as the platform evolves.

---
## Project Walkthrough


![Project Diagram](docs/images/platform-demo.png "Platform Architecture")

This walkthrough demonstrates the complete lifecycle of the platform, from infrastructure provisioning to application deployment, monitoring, security, and operations.

### 1. Provision Infrastructure

Deploy the cloud infrastructure using Terraform.

**Demonstrates:**

- Virtual Private Cloud (VPC)
- Google Kubernetes Engine (GKE)
- Cloud SQL (PostgreSQL)
- Artifact Registry
- IAM and Workload Identity Federation
- Terraform modular architecture

---

### 2. Bootstrap the Kubernetes Platform

Install the shared Kubernetes platform services.

**Demonstrates:**

- ArgoCD
- Argo Rollouts
- Gateway API
- NGINX Gateway Fabric
- Cert-Manager
- External Secrets Operator
- Kyverno
- Falco
- Prometheus
- Grafana
- Alertmanager
- Kubecost
- KEDA
- Velero
- Reloader

---

### 3. Deploy the Application

Deploy the Vote, Result, and Worker services using GitOps.

**Demonstrates:**

- GitOps workflow
- Kustomize overlays
- ArgoCD synchronization
- Environment-specific deployments

---

### 4. Execute the CI/CD Pipeline

Commit a change to the application repository and observe the automated pipeline.

**Pipeline Stages:**

- Source code checkout
- Dependency installation
- Unit testing
- Docker image build
- Trivy vulnerability scan
- SBOM generation
- Cosign image signing
- Push image to Artifact Registry
- Automatic GitOps repository update

---

### 5. Observe Progressive Delivery

Watch Argo Rollouts deploy the new application version.

**Demonstrates:**

- Canary deployment
- Blue-Green deployment
- Progressive traffic shifting
- Automated rollout promotion
- Rollback capabilities

---

### 6. Explore Security Controls

Review the platform's built-in security features.

**Demonstrates:**

- Kyverno policy enforcement
- Workload Identity Federation
- Kubernetes RBAC
- External Secrets integration
- Container image signing
- Vulnerability scanning
- Runtime security with Falco

---

### 7. Monitor the Platform

Access the monitoring dashboards.

**Demonstrates:**

- Prometheus metrics
- Grafana dashboards
- Alertmanager alerts
- PostgreSQL exporter
- Redis exporter
- Application health metrics

---

### 8. Review Cost Optimization

Inspect Kubernetes resource utilization and cost insights.

**Demonstrates:**

- Kubecost dashboards
- Namespace cost allocation
- Resource utilization
- Capacity planning
- Optimization recommendations

---

### 9. Verify Autoscaling

Generate application load and observe automatic scaling.

**Demonstrates:**

- KEDA event-driven autoscaling
- Horizontal Pod Autoscaler (HPA)
- Cluster Autoscaler
- Dynamic workload scaling

---

### 10. Backup and Restore

Demonstrate platform resilience using Velero.

**Demonstrates:**

- Backup creation
- Resource restoration
- Persistent volume recovery
- Disaster recovery workflow

---

### 11. Platform Automation

Run the platform automation services.

**Demonstrates:**

- Cluster health validation
- Infrastructure verification
- Platform health reporting
- Scheduled operational tasks

---

## Expected Outcome

By the end of this walkthrough, the platform demonstrates:

- Automated infrastructure provisioning
- Production-ready Kubernetes platform
- GitOps-based application delivery
- Progressive deployment strategies
- Integrated DevSecOps practices
- Centralized observability
- Event-driven autoscaling
- Cost visibility and optimization
- Backup and disaster recovery
- Python-based operational automation

---
## Future Enhancements

The platform is designed with a modular architecture, allowing new capabilities to be integrated as operational and business requirements evolve. Planned enhancements include:

### Platform

- Multi-cluster Kubernetes management
- Multi-region deployment for high availability
- Private GKE clusters with enhanced network isolation
- Cluster fleet management and centralized governance

### GitOps & Delivery

- Automated promotion between Development, Staging, and Production environments
- Progressive delivery with automated metric-based analysis
- Preview environments for pull requests
- Automated rollback based on deployment health

### Security

- Policy validation within CI pipelines
- Container image admission verification
- Secret rotation automation
- Enhanced software supply chain security and artifact verification

### Observability

- Centralized log aggregation
- Distributed tracing for microservices
- Service Level Objectives (SLOs) and Service Level Indicators (SLIs)
- Enhanced operational dashboards and reporting

### Platform Automation

- Automated Terraform drift detection
- Platform compliance reporting
- Certificate expiration monitoring
- Backup verification and recovery validation
- Automated platform health assessments and notifications

### Reliability

- Automated disaster recovery testing
- Scheduled backup validation
- High-availability database architecture
- Chaos engineering for resilience testing

### Developer Experience

- Self-service application onboarding
- Standardized application templates
- Internal developer portal
- Automated environment provisioning

### Cost Optimization

- Intelligent resource right-sizing recommendations
- Automated idle resource cleanup
- Budget monitoring and cost alerts
- Enhanced capacity planning and forecasting
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

## Technical Expertise Developed

### Infrastructure as Code

* Modular Terraform architecture
* Remote state management
* Environment-specific deployments
* Infrastructure automation

### Kubernetes Platform Engineering

* Google Kubernetes Engine (GKE)
* Platform bootstrapping
* Shared platform services
* Production-grade cluster operations

### GitOps

* ArgoCD
* Kustomize
* Argo Rollouts
* Declarative deployments

### CI/CD

* GitHub Actions
* Docker
* Artifact Registry
* Automated deployment pipelines

### DevSecOps

* Trivy
* Cosign
* SBOM
* Kyverno
* Falco
* External Secrets
* Workload Identity Federation

### Observability

* Prometheus
* Grafana
* Alertmanager
* PostgreSQL Exporter
* Redis Exporter

### Reliability

* Velero
* KEDA
* Horizontal Pod Autoscaler (HPA)
* Cluster Autoscaler
* Kubecost

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