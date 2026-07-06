## Project Overview

This Platform Engineering Portfolio demonstrates the design, provisioning, deployment, security, and operation of a production-ready cloud-native application platform on Google Cloud Platform (GCP). The project follows modern Platform Engineering principles by separating infrastructure provisioning, platform services, application delivery, and operational automation into dedicated repositories.

The platform is built using Infrastructure as Code (Terraform) to provision cloud resources such as Virtual Private Cloud (VPC), Google Kubernetes Engine (GKE), Cloud SQL, Artifact Registry, Identity and Access Management (IAM), and Cloud Storage. Shared Kubernetes platform services including ArgoCD, External Secrets, Kyverno, Cert-Manager, Prometheus, Grafana, Kubecost, Falco, KEDA, Velero, and Gateway API are deployed as reusable platform components.

Application delivery follows a GitOps workflow using ArgoCD and Kustomize, enabling declarative, version-controlled deployments across multiple environments. CI pipelines are implemented with GitHub Actions to automate source code validation, testing, container image builds, vulnerability scanning, SBOM generation, image signing, and deployment updates.

Security is integrated throughout the platform using policy enforcement, runtime security, secrets management, network segmentation, and container image verification. Observability is provided through centralized monitoring, metrics collection, alerting, and cost visibility.

The portfolio demonstrates a complete Platform Engineering lifecycle, covering infrastructure provisioning, platform management, application deployment, security, observability, automation, and progressive delivery using production-oriented engineering practices.

---
## Solution Architecture

The following architecture illustrates the complete platform deployment on GCP.
![Architecture Diagram](docs/images/platform_engineering_architecture.png "Platform Architecture")


This platform is built on a layered architecture that cleanly separates infrastructure provisioning, platform services, application delivery, and operations. Each layer owns a single responsibility, which keeps the system modular, independently scalable, and easier to secure and maintain as it grows.

The entire stack runs on Google Cloud Platform (GCP) and is built around modern Platform Engineering and GitOps principles — infrastructure, Kubernetes platform services, application deployments, security, and observability are all automated rather than manually operated.

Architecture at a glance

| Layer | Responsibility | Key Technologies |
|-------|----------------|------------------|
| **Infrastructure** | Cloud foundation and networking | Terraform, Google Cloud Platform (GCP), VPC, GKE, Cloud SQL, Artifact Registry |
| **Platform** | Shared Kubernetes platform services | ArgoCD, Argo Rollouts, Gateway API, Kyverno, Falco |
| **GitOps** | Declarative, version-controlled application delivery | ArgoCD, Kustomize |
| **Application** | Cloud-native microservices | Vote Service, Result Service, Worker Service, PostgreSQL, Redis |
| **CI/CD** | Build, test, secure, and deploy applications | GitHub Actions, Trivy, Cosign, SBOM, Artifact Registry |
| **Security** | Defense-in-depth and policy enforcement | Kyverno, Kubernetes RBAC, Workload Identity, Falco |
| **Observability** | Monitoring, dashboards, and alerting | Prometheus, Grafana, Alertmanager |
| **Platform Automation** | Operational automation and self-healing | Python-based automation services |


1. Infrastructure Layer

Provisioned entirely with Terraform, this layer lays the cloud foundation the platform runs on: a VPC with private subnets, Cloud Router and Cloud NAT for controlled egress, firewall rules, IAM and Workload Identity Federation, the GKE cluster itself, Cloud SQL (PostgreSQL), Artifact Registry, Cloud Storage, and the service accounts that tie it all together.

Infrastructure is organized into reusable Terraform modules and deployed consistently across Development and Production environments — the same modules, different variables.

2. Platform Layer

Once the cluster exists, this layer installs the shared Kubernetes services every application team relies on: ArgoCD and Argo Rollouts for delivery, Gateway API and NGINX Gateway for traffic management, Cert-Manager and External Secrets Operator for certificates and secrets, Kyverno and Falco for policy and runtime security, Prometheus/Grafana/Alertmanager for monitoring, Kubecost for cost visibility, KEDA for autoscaling, Velero for backup and disaster recovery, and Reloader for automatic config reloads.

These components turn a bare Kubernetes cluster into a genuine internal developer platform.

3. GitOps Layer

Application deployment follows a strict GitOps model — no one deploys directly to the cluster. Application changes are committed to the GitOps repository, and ArgoCD continuously reconciles the live cluster state against what's declared in Git.

This delivers:

- Declarative, version-controlled deployments
- Automatic synchronization and drift detection
- One-command rollback
- Environment promotion via Kustomize overlays

4. Application Layer

The reference workload is a small cloud-native microservices application — a Vote, Result, and Worker service backed by PostgreSQL and Redis. Manifests are managed with Kustomize using separate overlays per environment, and Argo Rollouts drives progressive delivery through Canary and Blue-Green strategies.

5. CI/CD Layer

GitHub Actions runs the CI pipeline on every commit: checkout, dependency install, unit tests, Docker image build, Trivy vulnerability scanning, SBOM generation, Cosign image signing, and an image push to Artifact Registry — followed by an automated update to the GitOps manifests. From there, ArgoCD takes over and deploys the new version.

6. Security Layer

Security is applied as a DevSecOps concern woven through every layer rather than bolted on at the end: Kyverno policy enforcement, Pod Security Standards, network policies, RBAC, externally managed secrets, Workload Identity Federation, image vulnerability scanning, SBOM generation, Cosign signing, and Falco for runtime threat detection. Together, these controls ensure nothing reaches production without meeting policy.

7. Observability Layer

Prometheus, Grafana, and Alertmanager provide centralized monitoring, backed by ServiceMonitors and dedicated Redis/PostgreSQL exporters, covering both application and infrastructure metrics. This gives the platform proactive alerting, capacity planning, and performance visibility out of the box.

8. Platform Automation Layer

A set of Python-based automation services handles the operational grind: daily platform health reports, cluster health validation, infrastructure reporting, and scheduled maintenance — reducing manual toil and improving reliability over time.


Architectural principles

- Infrastructure as Code (Terraform)
- GitOps-driven continuous delivery
- Immutable infrastructure
- Declarative Kubernetes configuration
- Platform self-service
- Security by default & policy as code
- Progressive delivery
- Infrastructure reusability across environments
- Production-grade observability
- Automated platform operations
---
