# 🏛️ Architecture Decision Records (ADR)

## 📖 Overview

This document captures the major architectural decisions made during the design and implementation of the **Production-Inspired Platform Engineering on Google Kubernetes Engine (GKE)** project.

Each decision records the problem being addressed, the selected solution, and the reasoning behind that choice.

Documenting architectural decisions improves maintainability, provides implementation context, and demonstrates the trade-offs considered during platform design.

---
<p align="left">
  <img src="images/architecture_decision.png" width="550" alt="Architectuure Decision">
</p>

---
## 📑 Table of Contents

* [📖 Overview](#-overview)
* [ADR-001: Google Kubernetes Engine](#adr-001-google-kubernetes-engine)
* [ADR-002: Infrastructure as Code with Terraform](#adr-002-infrastructure-as-code-with-terraform)
* [ADR-003: GitOps with Argo CD](#adr-003-gitops-with-argo-cd)
* [ADR-004: Kustomize for Environment Management](#adr-004-kustomize-for-environment-management)
* [ADR-005: Gateway API over Ingress](#adr-005-gateway-api-over-ingress)
* [ADR-006: Argo Rollouts for Progressive Delivery](#adr-006-argo-rollouts-for-progressive-delivery)
* [ADR-007: External Secrets Operator](#adr-007-external-secrets-operator)
* [ADR-008: Workload Identity](#adr-008-workload-identity)
* [ADR-009: Kyverno for Policy Enforcement](#adr-009-kyverno-for-policy-enforcement)
* [ADR-010: kube-prometheus-stack](#adr-010-kube-prometheus-stack)
* [ADR-011: KEDA with Redis Queue Length](#adr-011-keda-with-redis-queue-length)
* [ADR-012: Dedicated Node Pools](#adr-012-dedicated-node-pools)
* [📝 Summary](#-summary)

---
## ADR-001: Google Kubernetes Engine

### Decision

Use **Google Kubernetes Engine (GKE)** as the Kubernetes platform.

### Rationale

* Managed control plane
* Automatic upgrades
* Native Google Cloud integration
* Workload Identity support
* Production-grade Kubernetes

### Trade-offs

* Platform-specific features
* Cloud provider dependency

---
## ADR-002: Infrastructure as Code with Terraform

### Decision

Provision all cloud infrastructure using Terraform.

### Rationale

* Declarative infrastructure
* Version control
* Reproducible deployments
* Modular design
* Easier automation

### Trade-offs

* Additional learning curve
* Terraform state management

---
## ADR-003: GitOps with Argo CD

### Decision

Separate Continuous Integration from Continuous Delivery by adopting GitOps.

### Rationale

* Git as the single source of truth
* Continuous reconciliation
* Drift detection
* Automated synchronization
* Easier rollback

### Trade-offs

* Additional Git repository
* Argo CD operational overhead

---
## ADR-004: Kustomize for Environment Management

### Decision

Use Kustomize Base and Overlay architecture.

### Rationale

* Environment-specific configuration
* Minimal duplication
* Native Kubernetes support
* Declarative customization

### Trade-offs

* Overlay complexity for large environments

---
## ADR-005: Gateway API over Ingress

### Decision

Use Gateway API with NGINX Gateway Fabric.

### Rationale

* Modern Kubernetes networking
* Flexible routing model
* Better traffic management
* Future-focused architecture

### Trade-offs

* Smaller ecosystem compared to Ingress
* Additional Gateway controller

---
## ADR-006: Argo Rollouts for Progressive Delivery

### Decision

Replace standard Deployments with Argo Rollouts.

### Rationale

* Canary deployments
* Blue-Green deployments
* Automatic rollback
* Safer production releases

### Trade-offs

* Additional Custom Resources
* Increased deployment complexity

---
## ADR-007: External Secrets Operator

### Decision

Store secrets outside Kubernetes.

### Rationale

* No secrets in Git
* Centralized secret management
* Automatic synchronization
* Improved security

### Trade-offs

* Dependency on external secret providers

---
## ADR-008: Workload Identity

### Decision

Authenticate workloads using Workload Identity.

### Rationale

* No long-lived service account keys
* Native Google Cloud authentication
* Improved security
* Reduced credential management

### Trade-offs

* Initial IAM configuration complexity

---
## ADR-009: Kyverno for Policy Enforcement

### Decision

Implement Kubernetes admission policies using Kyverno.

### Rationale

* Kubernetes-native policy engine
* No custom admission webhooks
* Declarative policies
* Easy maintenance

### Trade-offs

* Policy testing and tuning required

---
## ADR-010: kube-prometheus-stack

### Decision

Use kube-prometheus-stack for observability.

### Rationale

* CNCF ecosystem
* Integrated monitoring stack
* Community maintained
* Rich dashboards and alerting

### Trade-offs

* Higher resource consumption

---
## ADR-011: KEDA with Redis Queue Length

### Decision

Use Redis queue length as the autoscaling trigger for Worker services.

### Rationale

The Worker service processes asynchronous jobs stored in Redis.

Queue length is a better indicator of workload than CPU utilization because it directly represents the amount of pending work.

Using KEDA enables event-driven autoscaling that reacts to actual demand instead of infrastructure utilization.

### Trade-offs

* Requires Redis availability
* Trigger thresholds require tuning

---
## ADR-012: Dedicated Node Pools

### Decision

Separate platform, application, and data workloads into dedicated node pools.

### Rationale

* Better workload isolation
* Independent scaling
* Improved scheduling
* Resource optimization
* Operational separation

### Trade-offs

* Additional node management
* Slightly higher infrastructure cost

---
## 📝 Summary

The platform was designed around a series of deliberate architectural decisions that prioritize automation, security, scalability, and operational simplicity. By adopting Infrastructure as Code, GitOps, policy-driven governance, progressive delivery, event-driven autoscaling, and centralized observability, the platform reflects production-inspired engineering practices commonly used in modern Kubernetes environments.

These Architecture Decision Records provide the rationale behind key implementation choices and document the trade-offs considered during the platform's design and evolution.

---