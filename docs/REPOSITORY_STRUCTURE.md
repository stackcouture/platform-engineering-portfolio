## Platform Overview

This Platform Engineering Portfolio demonstrates a **production-inspired cloud-native platform** built on **Google Kubernetes Engine (GKE)** using modern **Platform Engineering**, **GitOps**, and **Infrastructure as Code (IaC)** practices.

Rather than focusing solely on deploying an application, the portfolio showcases how a reusable Kubernetes platform can be designed, provisioned, secured, operated, and maintained using a modular **multi-repository architecture**. Each repository has a well-defined responsibility, enabling independent development, versioning, and lifecycle management while reflecting practices commonly adopted by engineering teams managing production Kubernetes environments.

---
### Repository Organization

The platform is organized into four repositories:

| Repository                        | Description                                                                                                                                                                 |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **platform-infra**                | Provisions Google Cloud infrastructure and Kubernetes platform services using Terraform.                                                                                    |
| **gitops-microservices-platform** | GitOps repository containing Kubernetes manifests, Kustomize overlays, Argo CD Applications, platform services, security policies, and environment-specific configurations. |
| **voting-app**                    | Microservices application source code, Dockerfiles, automated testing, and GitHub Actions CI pipelines.                                                                     |
| **platform-automation**           | Python-based automation for platform validation, health reporting, scheduled maintenance, and day-2 operational tasks.                                                      |

This separation of responsibilities establishes clear ownership boundaries between infrastructure provisioning, platform configuration, application development, and operational automation. It enables infrastructure changes, application releases, and platform operations to evolve independently while maintaining a consistent GitOps workflow.

---
### Platform Capabilities

The portfolio demonstrates the following Platform Engineering capabilities:

* Infrastructure provisioning with **Terraform**
* Google Kubernetes Engine (**GKE**) cluster management
* GitOps continuous delivery using **Argo CD**
* Kubernetes application management with **Kustomize**
* Progressive delivery using **Argo Rollouts**
* Platform security with **Kyverno** and **Falco**
* Secret management using **External Secrets Operator** and **HashiCorp Vault**
* Traffic management using **Gateway API** and **NGINX Gateway Fabric**
* Monitoring and observability with **Prometheus**, **Grafana**, and **Alertmanager**
* Event-driven autoscaling using **KEDA**
* Automated TLS management with **cert-manager**
* Backup and disaster recovery using **Velero**
* Cost monitoring using **Kubecost**
* Continuous Integration using **GitHub Actions**
* Day-2 platform operations using **Python-based automation**

The overall repository organization reflects production-oriented Platform Engineering principles by separating infrastructure, platform services, GitOps configuration, application source code, and operational tooling into dedicated repositories. This modular approach improves maintainability, promotes reusability, simplifies collaboration, and provides a scalable foundation for managing cloud-native platforms across multiple environments.


---
## Repository Organization

The platform follows a **multi-repository architecture** that separates infrastructure provisioning, GitOps configuration, application development, and operational automation into independent repositories. This separation enables each repository to have a clear ownership boundary, independent versioning, dedicated CI/CD workflows, and a well-defined lifecycle while supporting collaboration across platform and application teams.

| Repository                        | Purpose                                                                                                                                                                                                         |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **platform-infra**                | Provisions Google Cloud infrastructure and Kubernetes platform services using Terraform, including networking, GKE, IAM, Cloud SQL, Artifact Registry, and shared platform components.                          |
| **gitops-microservices-platform** | Serves as the GitOps repository containing Kubernetes manifests, Kustomize overlays, Argo CD Applications, platform services, security policies, governance resources, and environment-specific configurations. |
| **voting-app**                    | Contains the source code for the Vote, Result, and Worker microservices, along with Dockerfiles, unit tests, and GitHub Actions CI pipelines for building, testing, scanning, and publishing container images.  |
| **platform-automation**           | Provides Python-based automation for day-2 platform operations, including health validation, operational reporting, scheduled maintenance, and infrastructure validation tasks.                                 |

This repository organization promotes modularity, improves maintainability, simplifies change management, and aligns with production Platform Engineering practices where infrastructure, platform services, application code, and operational tooling evolve independently while remaining integrated through GitOps workflows.

---
## Repository Structure

The Platform Engineering Portfolio is organized into multiple repositories, each responsible for a specific aspect of the platform. This modular structure separates infrastructure provisioning, GitOps configuration, application development, and operational automation, making the platform easier to maintain, scale, and evolve.

```text
Platform Engineering Portfolio
│
├── platform-infra/                    # Infrastructure as Code (Terraform)
│   │
│   ├── .github/
│   │   ├── actions/
│   │   │   └── gcp-auth/
│   │   └── workflows/
│   │
│   └── terraform/
│       ├── environments/
│       │   ├── dev/
│       │   │   ├── networking/
│       │   │   ├── iam/
│       │   │   ├── gke/
│       │   │   ├── cloud-sql/
│       │   │   ├── storage/
│       │   │   │   ├── artifact-registry/
│       │   │   │   └── cloud-storage/
│       │   │   └── platform/
│       │   │       ├── argocd/
│       │   │       ├── argo-rollouts/
│       │   │       ├── cert-manager/
│       │   │       ├── external-secrets/
│       │   │       ├── falco/
│       │   │       ├── ingress/
│       │   │       ├── keda/
│       │   │       ├── kubecost/
│       │   │       ├── kyverno/
│       │   │       ├── monitoring/
│       │   │       ├── nginx-gateway/
│       │   │       ├── reloader/
│       │   │       ├── storage-classes/
│       │   │       ├── vault/
│       │   │       └── velero/
│       │   │
│       │   └── prod/
│       │
│       └── modules/
│           ├── networking/
│           ├── iam/
│           ├── gke/
│           ├── cloud-sql/
│           ├── storage/
│           │   ├── artifact-registry/
│           │   └── cloud-storage/
│           └── platform/
│               ├── argocd/
│               ├── argo-rollouts/
│               ├── cert-manager/
│               ├── external-secrets/
│               ├── falco/
│               ├── ingress/
│               ├── istio/
│               ├── keda/
│               ├── kubecost/
│               ├── kyverno/
│               ├── monitoring/
│               ├── nginx-gateway/
│               ├── reloader/
│               ├── storage-classes/
│               ├── vault/
│               └── velero/
│
├── gitops-microservices-platform/     # GitOps Repository
│   │
│   ├── apps/
│   │   ├── vote/
│   │   │   ├── base/
│   │   │   └── overlays/
│   │   │       ├── dev/
│   │   │       └── prod/
│   │   │
│   │   ├── result/
│   │   │   ├── base/
│   │   │   └── overlays/
│   │   │       ├── dev/
│   │   │       └── prod/
│   │   │
│   │   └── worker/
│   │       ├── base/
│   │       └── overlays/
│   │           ├── dev/
│   │           └── prod/
│   │
│   ├── infrastructure/
│   │   ├── postgres/
│   │   ├── redis/
│   │   ├── pgadmin/
│   │   └── external-secrets-sa/
│   │
│   ├── platform/
│   │   ├── namespaces/
│   │   ├── gateway-api/
│   │   ├── ingress/
│   │   ├── clusterissuer/
│   │   ├── cluster-secrets/
│   │   ├── monitoring/
│   │   │   ├── postgres-exporter/
│   │   │   └── redis-exporter/
│   │   └── velero/
│   │
│   ├── security/
│   │   ├── kyverno/
│   │   ├── falco/
│   │   └── network-policies/
│   │
│   ├── governance/
│   │   ├── argocd/
│   │   ├── cert-manager/
│   │   ├── monitoring/
│   │   ├── postgres/
│   │   ├── redis/
│   │   └── vote/
│   │
│   ├── automation/
│   │   ├── common/
│   │   └── daily-platform-report/
│   │
│   └── argocd/
│       ├── applicationsets/
│       └── projects/
│
├── voting-app/                        # Application Source Code
│   ├── vote/
│   ├── result/
│   ├── worker/
│   └── .github/
│       └── workflows/
│
└── platform-automation/               # Platform Automation
    └── daily-platform-report/
```

### Repository Layout Summary

| Repository                        | Primary Responsibility                                                                                                                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **platform-infra**                | Terraform modules and environment configurations that provision Google Cloud infrastructure and install shared Kubernetes platform services.                                                                 |
| **gitops-microservices-platform** | GitOps repository that defines the desired cluster state through Kubernetes manifests, Kustomize overlays, Argo CD Applications, platform services, security policies, governance resources, and automation. |
| **voting-app**                    | Application source code for the Vote, Result, and Worker microservices, including Dockerfiles and GitHub Actions CI pipelines.                                                                               |
| **platform-automation**           | Python-based automation for day-2 platform operations, health validation, reporting, and scheduled maintenance tasks.                                                                                        |

This repository organization follows a production-oriented Platform Engineering model by clearly separating infrastructure provisioning, platform management, application development, and operational automation. Each repository has a distinct responsibility while integrating through GitOps workflows to deliver a secure, scalable, and maintainable Kubernetes platform.

---
## Repository Responsibilities

Each repository in the Platform Engineering Portfolio has a clearly defined responsibility. This separation of concerns improves maintainability, enables independent versioning, and allows infrastructure, platform services, application code, and operational tooling to evolve independently while remaining integrated through GitOps workflows.

### platform-infra

The **platform-infra** repository is responsible for provisioning and managing the underlying Google Cloud infrastructure and Kubernetes platform services using Terraform.

**Key responsibilities include:**

* Provisioning Google Cloud infrastructure
* Virtual Private Cloud (VPC) networking
* Google Kubernetes Engine (GKE) clusters and node pools
* Cloud SQL instances
* Artifact Registry repositories
* Cloud Storage buckets
* Identity and Access Management (IAM)
* Workload Identity Federation
* Reusable Terraform modules
* Environment-specific infrastructure (Development and Production)
* Installation of shared Kubernetes platform components, including:

  * Argo CD
  * Argo Rollouts
  * Cert-Manager
  * External Secrets Operator
  * Kyverno
  * Falco
  * KEDA
  * Kubecost
  * Prometheus and Grafana
  * NGINX Gateway Fabric
  * Reloader
  * Storage Classes
  * HashiCorp Vault
  * Velero

---

### gitops-microservices-platform

The **gitops-microservices-platform** repository serves as the GitOps source of truth for the Kubernetes platform. It defines the desired cluster state and manages platform resources, infrastructure workloads, application deployments, and governance through Argo CD.

**Key responsibilities include:**

* Kubernetes manifests
* Kustomize base and environment overlays
* Application deployments
* Platform services
* Infrastructure workloads
* Argo CD Applications and ApplicationSets
* Gateway API resources
* Ingress configuration
* Cluster-wide configuration
* Security policies
* Network Policies
* Environment-specific configurations
* Governance resources
* Platform automation manifests

---

### voting-app

The **voting-app** repository contains the application source code and Continuous Integration (CI) pipelines for the platform's microservices.

**Key responsibilities include:**

* Vote service
* Result service
* Worker service
* Dockerfiles
* Unit and integration tests
* GitHub Actions CI workflows
* Container image build automation
* Security scanning
* Software Bill of Materials (SBOM) generation
* Container image publishing to Artifact Registry

---

### platform-automation

The **platform-automation** repository provides automation for day-2 platform operations, reducing manual operational effort and improving platform reliability.

**Key responsibilities include:**

* Platform health validation
* Cluster health checks
* Infrastructure validation
* Scheduled operational tasks
* Automated reporting
* Operational dashboards and reports
* Maintenance automation
* Python-based automation scripts
* Platform diagnostics
* Day-2 operational tooling

---

### Responsibility Boundaries

The repository organization follows clear ownership boundaries:

| Repository                        | Primary Ownership                                                                    |
| --------------------------------- | ------------------------------------------------------------------------------------ |
| **platform-infra**                | Cloud infrastructure provisioning and shared platform installation                   |
| **gitops-microservices-platform** | Kubernetes desired state, GitOps deployments, platform configuration, and governance |
| **voting-app**                    | Application source code, testing, container image creation, and CI pipelines         |
| **platform-automation**           | Operational automation, health validation, reporting, and maintenance                |

By assigning a single responsibility to each repository, the platform remains modular, easier to maintain, and aligned with production Platform Engineering practices. Infrastructure provisioning, GitOps configuration, application development, and operational automation can be managed independently while working together through a unified GitOps workflow.


---