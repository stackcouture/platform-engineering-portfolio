## Security

### Overview

This document describes the security architecture implemented for the **Cloud-Native on Google Kubernetes Engine (GKE)** project.

Security is integrated throughout the platform lifecycle—from infrastructure provisioning and identity management to software supply chain protection, Kubernetes policy enforcement, secret management, networking, and runtime security.

The platform follows a **defense-in-depth** approach by applying multiple complementary security controls rather than relying on a single mechanism.

---
## Table of Contents

* [Overview](#overview)
* [Security Principles](#security-principles)
* [Identity and Access Management](#identity-and-access-management)

  * [Google Cloud IAM](#google-cloud-iam)
  * [Workload Identity](#workload-identity)
  * [RBAC](#rbac)
  * [Service Accounts](#service-accounts)
* [Secret Management](#secret-management)
* [Policy Enforcement](#policy-enforcement)
* [Container Image Security](#container-image-security)

  * [Trivy](#trivy)
* [Software Supply Chain Security](#software-supply-chain-security)

  * [SBOM](#sbom)
  * [Cosign](#cosign)
* [Kubernetes Runtime Security](#kubernetes-runtime-security)
* [Runtime Threat Detection](#runtime-threat-detection)

  * [Runtime Detection Capabilities](#runtime-detection-capabilities)
  * [Alert Workflow](#alert-workflow)
  * [Defense-in-Depth Security Architecture](#defense-in-depth-security-architecture)
  * [End-to-End Security Lifecycle](#end-to-end-security-lifecycle)
* [Network Security](#network-security)
* [Certificate Management](#certificate-management)
* [Deployment Security](#deployment-security)
* [Security Monitoring](#security-monitoring)
* [Challenges Encountered](#challenges-encountered)
* [Key Learnings](#key-learnings)
* [Summary](#summary)

---
## Security Principles

The platform is designed around the following principles:

* Least privilege access
* Identity-based authentication
* Secret externalization
* Policy-driven governance
* Immutable deployments
* Secure software supply chain
* Zero hardcoded credentials
* Defense in depth

---
## Identity and Access Management

### Google Cloud IAM

Google Cloud IAM controls access to cloud resources using predefined roles and service accounts.

Responsibilities include:

* Artifact Registry access
* Google Secret Manager access
* GKE API access
* Cloud Storage permissions

---
### Workload Identity

Workload Identity securely connects Kubernetes Service Accounts with Google Service Accounts.

Benefits include:

* No long-lived service account keys
* Short-lived credentials
* Native Google Cloud authentication
* Reduced credential management

Applications authenticate to Google Cloud services without storing credentials inside the cluster.

---
### RBAC

Role-Based Access Control limits Kubernetes API permissions.

RBAC is used to:

* Restrict namespace access
* Limit service account permissions
* Prevent unnecessary cluster-wide privileges

---
### Service Accounts

Dedicated Kubernetes Service Accounts are created for application workloads.

This improves workload isolation and follows the principle of least privilege.

---
## Secret Management

Sensitive configuration is stored outside Git.

The platform uses:

* Google Secret Manager
* HashiCorp Vault
* External Secrets Operator

Secret flow:

```text
Google Secret Manager / Vault
            │
External Secrets Operator
            │
Kubernetes Secret
            │
Application Pods
```

Benefits include:

* No secrets in Git
* Centralized secret management
* Automatic synchronization
* Kubernetes-native secret consumption

---
## Policy Enforcement

Kyverno provides Kubernetes-native admission control.

Policies validate resources before deployment.

Examples include:

* Required labels
* Resource requests and limits
* Liveness probes
* Readiness probes
* Non-root containers
* Approved container registries
* Image tag validation

These policies help maintain platform-wide governance and consistency.

---
## Container Image Security

Container images are validated before deployment.

### Trivy

Every image is scanned during the CI pipeline.

Checks include:

* Operating system vulnerabilities
* Application dependencies
* High and critical CVEs

Only scanned images are promoted through the deployment pipeline.

---
## Software Supply Chain Security

The platform protects the software supply chain using:

### SBOM

A Software Bill of Materials is generated during every build.

Benefits include:

* Dependency visibility
* Package inventory
* Supply chain transparency

---
### Cosign

Container images are digitally signed before publication.

Benefits include:

* Image authenticity
* Integrity verification
* Trusted deployments

---
## Kubernetes Runtime Security

Application workloads follow Kubernetes security best practices.

Examples include:

* Non-root containers
* Resource requests and limits
* Liveness probes
* Readiness probes
* Namespace isolation

Dedicated node pools further isolate:

* Platform workloads
* Application workloads
* Stateful services

---
## Runtime Threat Detection

The platform implements Falco to provide real-time runtime security monitoring for Kubernetes workloads.

While Kyverno validates Kubernetes resources before deployment through admission control policies, Falco continuously monitors running containers, Kubernetes events, and Linux system calls to detect suspicious activity after workloads have been deployed.

Together, Kyverno and Falco provide both preventive and detective security controls, strengthening the overall security posture of the platform.

Falco Architecture

<p align="left"> <img src="images/falco-architecture.jpg" width="650" alt="Falco Runtime Security"> </p>

Falco continuously monitors runtime activity across the Kubernetes cluster and evaluates events against predefined security rules. When suspicious behavior is detected, Falco generates alerts that can be integrated with the platform's monitoring and notification systems.

### Runtime Detection Capabilities

Falco is configured to detect runtime security events including:

- Interactive shell execution inside containers
- Privilege escalation attempts
- Unauthorized process execution
- Access to sensitive host files
- Container escape attempts
- Suspicious Kubernetes API activity
- Unexpected outbound network connections
- Modification of critical system binaries
- Execution of unauthorized binaries
- Anomalous container behavior

These detections provide continuous visibility into workload activity after deployment.

### Alert Workflow

```text
                 Application Pods
                        │
        Linux System Calls & Kubernetes Audit Events
                        │
                        ▼
                     Falco
                        │
                Rule Evaluation
                        │
                        ▼
                  Runtime Alerts
                        │
        ┌───────────────┼────────────────┐
        ▼               ▼                ▼
 Alertmanager   Slack Notifications   Grafana Dashboards
```

Falco evaluates runtime events in real time and forwards alerts to the platform's observability stack for visualization and incident response.

Benefits

Falco enhances the platform by providing:

- Continuous runtime monitoring
- Real-time threat detection
- Kubernetes behavioral analysis
- Early attack detection
- Security event visibility
- Faster incident response
- Compliance monitoring
- Runtime policy enforcement
- Reduced Mean Time to Detect (MTTD)
- Improved operational security

### Defense-in-Depth Security Architecture

The platform implements multiple layers of security throughout the software delivery lifecycle.

| Security Layer | Technology |
|----------------|------------|
| Identity & Access | Google Cloud IAM, Workload Identity, RBAC, Service Accounts |
| Secret Management | External Secrets Operator, Google Secret Manager, HashiCorp Vault |
| Policy Enforcement | Kyverno |
| Container Image Security | Trivy |
| Software Supply Chain | SBOM, Cosign |
| Runtime Threat Detection | Falco |
| Network Security | Gateway API, Cloudflare, TLS |
| Certificate Management | cert-manager |
| Progressive Delivery | Argo Rollouts |
| Security Monitoring | Prometheus, Grafana, Alertmanager |

#### End-to-End Security Lifecycle

```text
                 Developer
                     │
                     ▼
      Trivy Vulnerability Scan
                     │
                     ▼
          SBOM Generation
                     │
                     ▼
        Cosign Image Signing
                     │
                     ▼
          Artifact Registry
                     │
                     ▼
                 Argo CD
                     │
                     ▼
      Kyverno Policy Validation
                     │
                     ▼
    Google Kubernetes Engine (GKE)
                     │
                     ▼
      Falco Runtime Monitoring
                     │
                     ▼
      Alertmanager • Grafana • Slack
```

The platform follows a layered security approach that protects workloads throughout their lifecycle. Trivy, SBOM, and Cosign secure the software supply chain before deployment. Kyverno enforces Kubernetes admission policies to validate resources before they are created. Once workloads are running, Falco continuously monitors runtime behavior and detects suspicious activity. Combined with Workload Identity, External Secrets Operator, Google Secret Manager, HashiCorp Vault, cert-manager, and centralized monitoring through Prometheus, Grafana, and Alertmanager, these controls provide a comprehensive defense-in-depth security architecture for the platform.

---
## Network Security

External traffic enters the cluster through:

* Cloudflare DNS
* Gateway API
* NGINX Gateway Fabric

Traffic is protected using HTTPS and routed through declarative Gateway API resources.

---
## Certificate Management

TLS certificates are managed automatically using cert-manager.

Features include:

* Automatic certificate issuance
* Automatic renewal
* Cloudflare DNS validation
* Cluster-wide certificate management

This removes manual certificate management from platform operations.

---
## Deployment Security

Application deployments are managed using Argo Rollouts.

Deployment strategies include:

* Canary deployments
* Blue-Green deployments

Progressive delivery minimizes deployment risk by validating application health before full rollout.

---
## Security Monitoring

Security-related visibility is provided through:

* Prometheus
* Grafana
* Alertmanager

Monitoring includes:

* Application health
* Kubernetes metrics
* Infrastructure metrics
* Alert notifications

---
## Challenges Encountered

Key security challenges included:

* Configuring Workload Identity
* External Secrets synchronization
* Kyverno policy validation
* Cloudflare DNS validation
* IAM permission management
* cert-manager configuration

These were resolved through iterative testing, IAM policy refinement, Kubernetes event analysis, and controller log inspection.

---
## Key Learnings

This project provided practical experience with:

* Kubernetes security
* Google Cloud IAM
* Workload Identity
* RBAC
* Secret management
* Policy enforcement
* Secure software supply chains
* TLS automation
* Progressive deployment security
* Defense-in-depth architecture

---
## Summary

The platform integrates security across every stage of the application lifecycle. Identity management, secret externalization, policy enforcement, secure software supply chains, automated certificate management, runtime hardening, and deployment safeguards work together to create a production-inspired Kubernetes platform aligned with modern Platform Engineering and DevSecOps practices.

---