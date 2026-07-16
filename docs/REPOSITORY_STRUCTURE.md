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
## Repository Relationships

The Platform Engineering Portfolio follows a GitOps-driven software delivery workflow where each repository is responsible for a specific stage of the platform lifecycle. Infrastructure is provisioned using Terraform, application source code is continuously integrated through GitHub Actions, Kubernetes deployments are managed through GitOps with Argo CD, and operational tasks are automated using dedicated platform automation.

The overall workflow is illustrated below.

```text
                           Developer
                               │
                               ▼
                     voting-app Repository
                               │
                  GitHub Actions CI Pipeline
                               │
              Build • Test • Scan • Publish
                               │
                               ▼
                Google Artifact Registry
                               │
                               ▼
         gitops-microservices-platform Repository
                               │
                   Update Image Tags & Manifests
                               │
                               ▼
                        Argo CD (GitOps)
                               │
                    Continuous Synchronization
                               │
                               ▼
                Google Kubernetes Engine (GKE)
                               ▲
                               │
              Provisioned and Managed by Terraform
                               │
                               ▼
                 platform-infra Repository
      (Infrastructure & Shared Platform Services)
                               │
                               ▼
             platform-automation Repository
        (Health Checks, Reports & Day-2 Operations)
```

### Repository Interaction Flow

The repositories work together to deliver applications to the Kubernetes platform while maintaining a clear separation of responsibilities.

1. Developers implement application features in the **voting-app** repository.
2. GitHub Actions automatically builds, tests, scans, and publishes container images to **Google Artifact Registry**.
3. The **gitops-microservices-platform** repository stores the desired Kubernetes cluster state, including application manifests, platform resources, and environment-specific Kustomize overlays.
4. **Argo CD** continuously monitors the GitOps repository and synchronizes changes to the Kubernetes cluster.
5. The **platform-infra** repository provisions and manages the Google Cloud infrastructure, Kubernetes cluster, and shared platform services using Terraform.
6. The **platform-automation** repository performs day-2 operational tasks such as health validation, platform reporting, diagnostics, and scheduled maintenance.

### End-to-End Delivery Workflow

The complete delivery process follows these stages:

1. Infrastructure is provisioned using Terraform.
2. Shared platform services are installed on the Kubernetes cluster.
3. Applications are developed and committed to the application repository.
4. GitHub Actions builds, tests, scans, and publishes container images.
5. GitOps manifests are updated with the new image versions.
6. Argo CD synchronizes the desired state with the Kubernetes cluster.
7. Applications are deployed and continuously reconciled.
8. Platform automation validates platform health and performs operational tasks.

This repository relationship model establishes a clear separation between infrastructure provisioning, continuous integration, GitOps-based continuous delivery, application development, and operational automation. The result is a modular, maintainable, and production-inspired Platform Engineering architecture that supports independent evolution of each repository while ensuring consistent and reliable platform operations.

---
## Layer Responsibilities

The platform is organized into logical layers, with each layer responsible for a specific aspect of the cloud-native platform. This layered architecture separates infrastructure provisioning, shared platform capabilities, and application workloads, resulting in a modular, scalable, and maintainable Platform Engineering implementation.

| Layer              | Purpose                                                                                                                                                      | Core Components                                                                                                                                                                                          |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Infrastructure** | Establishes the cloud foundation by provisioning networking, compute, storage, identity, and managed cloud services required to run the Kubernetes platform. | Terraform, Google Cloud Platform (GCP), VPC, GKE, Cloud SQL, Artifact Registry, Cloud Storage, IAM, Workload Identity Federation                                                                         |
| **Platform**       | Provides shared Kubernetes services that enable secure, reliable, observable, and scalable application delivery across the cluster.                          | Argo CD, Argo Rollouts, Gateway API, NGINX Gateway Fabric, cert-manager, External Secrets Operator, HashiCorp Vault, Kyverno, Falco, Prometheus, Grafana, Alertmanager, KEDA, Kubecost, Velero, Reloader |
| **Application**    | Hosts the cloud-native business workloads and supporting data services that run on the Kubernetes platform.                                                  | Vote Service, Result Service, Worker Service, PostgreSQL, Redis                                                                                                                                          |
---
### Infrastructure Layer

The Infrastructure layer provides the foundational cloud resources required to operate the platform. It is provisioned using reusable Terraform modules and environment-specific configurations, ensuring consistent and repeatable infrastructure deployments.

**Responsibilities include:**

* Provisioning Google Cloud infrastructure
* Creating Virtual Private Cloud (VPC) networking
* Managing Google Kubernetes Engine (GKE) clusters and node pools
* Provisioning Cloud SQL databases
* Creating Artifact Registry repositories
* Managing Cloud Storage resources
* Configuring IAM roles and permissions
* Implementing Workload Identity Federation
* Managing reusable Terraform modules

---
### Platform Layer

The Platform layer delivers shared Kubernetes capabilities that support secure application deployment, GitOps workflows, observability, policy enforcement, autoscaling, traffic management, and operational resilience.

**Responsibilities include:**

* GitOps continuous delivery with Argo CD
* Progressive delivery using Argo Rollouts
* Kubernetes traffic management with Gateway API and NGINX Gateway Fabric
* Secret management using External Secrets Operator and HashiCorp Vault
* Policy enforcement using Kyverno
* Runtime security monitoring using Falco
* Monitoring and alerting with Prometheus, Grafana, and Alertmanager
* Event-driven autoscaling with KEDA
* Automated TLS certificate management with cert-manager
* Backup and disaster recovery with Velero
* Cost monitoring with Kubecost
* Automatic workload reloads using Reloader

---
### Application Layer

The Application layer hosts the business services deployed on the platform. These services demonstrate how cloud-native workloads are built, containerized, continuously integrated, and delivered through GitOps.

**Responsibilities include:**

* Hosting the Vote, Result, and Worker microservices
* Managing PostgreSQL and Redis workloads
* Building container images through GitHub Actions
* Running automated tests and security scans
* Publishing container images to Artifact Registry
* Deploying applications through Argo CD
* Supporting environment-specific configuration using Kustomize overlays

---
### Layered Architecture Benefits
This layered architecture provides several advantages:

* Clear separation of infrastructure, platform, and application responsibilities
* Independent lifecycle management for each layer
* Improved maintainability and scalability
* Reusable infrastructure and platform components
* Consistent GitOps-based deployments
* Enhanced security through centralized platform services
* Simplified operations using shared observability and automation
* Alignment with production Platform Engineering practices

---
## Design Principles

The Platform Engineering Portfolio is designed around a set of architectural principles that promote modularity, scalability, security, and operational excellence. These principles guide the organization of the repositories, infrastructure, platform services, and application workloads while reflecting production-inspired Platform Engineering practices.

### Separation of Concerns

Infrastructure provisioning, platform services, application source code, and operational automation are maintained in separate repositories. This separation provides clear ownership boundaries, simplifies maintenance, and allows each component to evolve independently.

### Infrastructure as Code

All cloud infrastructure and shared platform services are provisioned using Terraform. Infrastructure definitions are version-controlled, reusable, and repeatable, enabling consistent deployments across environments.

### GitOps as the Source of Truth

The desired state of the Kubernetes platform is stored in Git. Argo CD continuously reconciles the cluster with the Git repository, ensuring deployments remain declarative, auditable, and consistent.

### Modular Architecture

The platform is organized into reusable Terraform modules, Kubernetes manifests, and Kustomize overlays. This modular approach reduces duplication, promotes consistency, and simplifies the introduction of new environments or platform capabilities.

### Environment Isolation

Development and production environments are managed through dedicated Terraform configurations and Kustomize overlays. Environment-specific configuration is isolated while sharing common infrastructure and application definitions where appropriate.

### Security by Default

Security is integrated throughout the platform by combining identity management, policy enforcement, secret management, runtime security, and secure software delivery practices.

Key security capabilities include:

* Workload Identity Federation
* External Secrets Operator
* HashiCorp Vault integration
* Kyverno policy enforcement
* Falco runtime security
* Network Policies
* Container image security scanning

### Platform Standardization

Common platform services are deployed once and shared across workloads, providing consistent operational capabilities for all applications.

Shared platform services include:

* Argo CD
* Argo Rollouts
* Gateway API
* NGINX Gateway Fabric
* cert-manager
* Prometheus
* Grafana
* Alertmanager
* KEDA
* Kubecost
* Velero
* Reloader

### Automation First

Automation is applied across infrastructure provisioning, application delivery, and day-2 operations to reduce manual effort and improve reliability.

Automation includes:

* Terraform infrastructure provisioning
* GitHub Actions CI pipelines
* GitOps continuous delivery
* Automated container image publishing
* Platform health validation
* Scheduled operational tasks
* Automated reporting

### Observability by Design

Monitoring, alerting, logging, and cost visibility are treated as core platform capabilities rather than optional add-ons. Shared observability services provide consistent operational insight across the platform.

### Scalability and Maintainability

The platform is designed to support future growth by using reusable modules, declarative configuration, GitOps workflows, and independent repositories. This structure allows new services, environments, and platform capabilities to be introduced with minimal changes to the existing architecture.

### Summary

These design principles establish a consistent foundation for provisioning infrastructure, operating Kubernetes, delivering applications, and automating platform operations. By combining Infrastructure as Code, GitOps, modular architecture, standardized platform services, and automation, the portfolio demonstrates a production-inspired Platform Engineering approach that emphasizes maintainability, security, scalability, and operational consistency.

---