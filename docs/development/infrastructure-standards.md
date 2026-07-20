# Infrastructure Standards

This document establishes the standards, rules, and layout conventions for all infrastructure-related code and configuration in the `tax-ai` repository. 

All infrastructure definitions—including containers, cloud resources, cluster orchestrations, and deployment configurations—must reside under the [`infrastructure/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure) directory.

---

## Directory Layout

Infrastructure code is organized by toolchain under the [`infrastructure/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure) directory. The standard subdirectories are:

| Subdirectory | Purpose | Configured Tools |
| :--- | :--- | :--- |
| `infrastructure/docker/` | Dockerfiles and container configurations for custom images and multi-container runtimes | Docker, Docker Compose |
| [`infrastructure/terraform/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure/terraform) | Infrastructure as Code (IaC) for cloud resource provisioning | Terraform, OpenTofu |
| `infrastructure/helm/` | Helm charts for packaging, configuring, and deploying apps to Kubernetes | Helm |
| `infrastructure/kubernetes/` | Raw Kubernetes manifests and resource configurations | kubectl |

---

## Core Rules

All infrastructure configurations must adhere strictly to these three core rules:

### 1. Never Place Terraform Inside Application Folders
To maintain clean separation between software logic and infrastructure orchestration:
* **Rule:** All Terraform modules and state definitions must remain under [`infrastructure/terraform/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure/terraform).
* **Avoid:** Adding `.tf` files inside app folders like `apps/api/` or `apps/web/`.
* **Rationale:** Cloud infrastructure lifecycle (provisioning resources) is independent of the application code compile/build pipeline.

### 2. Never Mix Dockerfiles with Kubernetes Manifests
Keep container definitions separate from execution orchestrations.
* **Rule:** 
  * Dockerfiles (defining *how to build* container images) belong in application packages or under `infrastructure/docker/` (for generic/base configurations).
  * Kubernetes manifests (defining *how to run* containers on a cluster) belong in `infrastructure/kubernetes/` or `infrastructure/helm/`.
* **Avoid:** Creating mixed deployment folders that interlace Docker files and YAML manifests in the same workspace directory.

### 3. Separate Local Development from Production Infrastructure
Local tools and sandbox scripts must remain separate from staging and production declarations to prevent accidental production impact.
* **Rule:** 
  * Use `docker-compose.yml` at the root and associated local configurations for developer environments.
  * Staging and production infrastructure must be provisioned and managed via partitioned Terraform modules (`infrastructure/terraform/terraform/environments/prod`, `staging`) and deployed through secure pipelines.
* **Avoid:** Importing production secrets or values into local dev configuration setups.
