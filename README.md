## Project Overview

This Platform Engineering Portfolio demonstrates the design, provisioning, deployment, security, and operation of a production-ready cloud-native application platform on Google Cloud Platform (GCP). The project follows modern Platform Engineering principles by separating infrastructure provisioning, platform services, application delivery, and operational automation into dedicated repositories.

The platform is built using Infrastructure as Code (Terraform) to provision cloud resources such as Virtual Private Cloud (VPC), Google Kubernetes Engine (GKE), Cloud SQL, Artifact Registry, Identity and Access Management (IAM), and Cloud Storage. Shared Kubernetes platform services including ArgoCD, External Secrets, Kyverno, Cert-Manager, Prometheus, Grafana, Kubecost, Falco, KEDA, Velero, and Gateway API are deployed as reusable platform components.

Application delivery follows a GitOps workflow using ArgoCD and Kustomize, enabling declarative, version-controlled deployments across multiple environments. CI pipelines are implemented with GitHub Actions to automate source code validation, testing, container image builds, vulnerability scanning, SBOM generation, image signing, and deployment updates.

Security is integrated throughout the platform using policy enforcement, runtime security, secrets management, network segmentation, and container image verification. Observability is provided through centralized monitoring, metrics collection, alerting, and cost visibility.

The portfolio demonstrates a complete Platform Engineering lifecycle, covering infrastructure provisioning, platform management, application deployment, security, observability, automation, and progressive delivery using production-oriented engineering practices.
---


# Platform Engineering Portfolio

A production-ready Platform Engineering portfolio demonstrating the design, automation, deployment, and operation of a cloud-native application platform on Google Cloud Platform (GCP).

This portfolio showcases modern Platform Engineering practices including Infrastructure as Code, GitOps, Kubernetes, Continuous Integration and Delivery (CI/CD), DevSecOps, observability, policy enforcement, and cost optimization.

## Key Capabilities

- Infrastructure provisioning with Terraform
- Google Kubernetes Engine (GKE)
- GitOps deployments using ArgoCD
- GitHub Actions CI/CD pipelines
- Google Artifact Registry
- Workload Identity Federation (OIDC)
- Cloud SQL for PostgreSQL
- Redis
- Kyverno policy enforcement
- Cert-manager with Let's Encrypt
- External Secrets Operator
- Gateway API
- Prometheus & Grafana
- Kubecost
- Trivy vulnerability scanning
- Cosign image signing
- SBOM generation and attestation
- Kustomize
- Blue-Green and Canary deployments with Argo Rollouts 
- Production-grade Kubernetes architecture

This repository serves as the entry point for the complete Platform Engineering ecosystem and links to the individual repositories that implement each layer of the platform.

---
### Recommended Repository Structure


A production-grade **Platform Engineering Portfolio** demonstrating Infrastructure as Code, GitOps, Kubernetes Platform Engineering, Security, Observability, Progressive Delivery, and CI/CD automation on Google Cloud Platform.

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

---

| Repository | Description |
|------------|-------------|
| **platform-infra** | Infrastructure as Code (Terraform) repository that provisions Google Cloud infrastructure (VPC, GKE, Cloud SQL, IAM, Storage) and installs platform components such as ArgoCD, Kyverno, Prometheus, KEDA, Cert-Manager, External Secrets, Falco, Kubecost, and Velero. |
| **gitops-microservices-platform** | GitOps repository containing Kubernetes manifests, Kustomize overlays, ArgoCD ApplicationSets, platform services, security policies, governance, and application deployments for different environments. |
| **voting-app** | Microservices application source code consisting of Vote, Result, and Worker services, along with CI pipelines for building, testing, scanning, and publishing container images. |
| **platform-automation** | Platform automation repository containing Python-based automation tools, scheduled jobs, operational reports, health checks, and day-to-day platform maintenance scripts. |

---