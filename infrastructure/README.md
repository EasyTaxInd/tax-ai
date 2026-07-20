# Infrastructure as Code (`infrastructure/`)

This directory houses all cloud configurations, environment settings, deployment manifests, and containerization instructions for provisioning and running the `tax-ai` system.

---

## Purpose

The `infrastructure/` directory centralizes all systems engineering and DevOps operations. It ensures that infrastructure is version-controlled, auditable, and reproducible across local development workstations, staging clusters, and production networks.

---

## Contents

* [`infrastructure/terraform/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure/terraform): Cloud resource provisioning configurations (environments `dev/`, `staging/`, `prod/` and reusable `modules/`).
* `infrastructure/docker/`: Generic/base container files and multi-service compose descriptors.
* `infrastructure/helm/`: Helm package manager templates for application deployments to Kubernetes.
* `infrastructure/kubernetes/`: Declarative YAML configurations and raw manifests for cluster resources.

---

## Guidelines for Adding New Infrastructure/Files

1. **Keep Secrets Secret**: Never commit plain text passwords, private API keys, or security certificates. Use KMS or Secret Managers.
2. **Never Mix Execution Schemas**: Do not mingle Docker image descriptors (`Dockerfile`s) with operational execution parameters (Kubernetes YAMLs). Keep them isolated in their respective folders.
3. **Partition Environments**: Always segregate development environments from production definitions to prevent accidental overrides.
4. **Reference Documentation**: For a full list of rules, guidelines, and tool patterns, refer to [Infrastructure Standards](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/infrastructure-standards.md).
