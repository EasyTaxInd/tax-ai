# Repository Structure and Ownership

This document defines the folder structure, purpose, and ownership model for the `tax-ai` monorepo. It outlines where code, configuration, documentation, and infrastructure definitions should reside.

---

## High-Level Directory Layout

The repository is organized as a monorepo containing application services, shared libraries, infrastructure-as-code configuration, and tooling.

| Folder | Purpose | Ownership/Maintainers |
| :--- | :--- | :--- |
| [`.devcontainer/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/.devcontainer) | VS Code Dev Container configurations | Platform / Dev Experience Team |
| [`.github/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/.github) | GitHub Actions, templates, and issue definitions | DevOps / Platform Team |
| [`apps/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps) | Deployable applications and services | Product / Feature Teams |
| [`docs/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs) | Engineering documentation, ADRs, and runbooks | All Engineering |
| [`infra/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infra) | Global / Root Terraform configurations | DevOps / Platform Team |
| [`infrastructure/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure) | Environment-specific IaC configurations and modules | DevOps / Platform Team |
| [`packages/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages) | Shared libraries and reusable package dependencies | Shared Architecture Team / All |
| [`scripts/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/scripts) | Repository automation and utility scripts | Tooling / Platform Team |

---

## Detailed Directory Breakdown

### 1. [`.devcontainer/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/.devcontainer)
Contains configurations for VS Code Development Containers. This allows developers to spin up a fully configured containerized environment with all required system dependencies pre-installed.
* **Key Contents:** `devcontainer.json`, `Dockerfile` (when populated).
* **Rule:** Any changes to tools required for local development should be reflected here.

### 2. [`.github/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/.github)
Houses repository-wide configuration for GitHub, primarily CI/CD workflows, pull request/issue templates, and integration files.
* **Key Contents:**
  * [`workflows/ci.yml`](file:///c:/Users/navne/EasyTaxInd/tax-ai/.github/workflows/ci.yml): Continual Integration (CI) configuration for testing and linting code on push and PRs.
  * Templates for issue reporting and pull request descriptions.
  * Dependabot and codeowners definitions.

### 3. [`apps/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps)
Stores distinct, buildable, and deployable applications. Files inside these directories should not be imported directly by other applications; shared code must go into the `packages/` directory instead.
* **Subfolders:**
  * [`apps/api/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps/api): Backend API services (e.g., Express, NestJS, FastAPI).
  * [`apps/web/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps/web): User-facing web frontend application (e.g., React, Next.js).
  * [`apps/worker/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps/worker): Background worker processes for processing jobs, message queues, and async tasks.

### 4. [`docs/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs)
Engineering and operational documentation repository.
* **Subfolders:**
  * [`docs/adr/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/adr): Architecture Decision Records documenting key architectural choices.
  * [`docs/api/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/api): API specifications (e.g., OpenAPI schemas) and documentation.
  * [`docs/architecture/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/architecture): Higher-level architecture design, diagrams, and system flow charts.
  * [`docs/development/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development): Guides on local environment setup, standards, and guidelines (e.g., this file).
  * [`docs/runbooks/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/runbooks): Troubleshooting, deployment, and operational runbooks for on-call engineers.

### 5. [`infra/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infra)
Houses root-level/global Terraform configurations. This is used for managing the overarching configurations that don't vary significantly between environments or setup bootstrapping.
* **Key Contents:** `variables.tf`, `locals.tf`, `providers.tf`, `outputs.tf`.

### 6. [`infrastructure/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/infrastructure)
Contains environment-specific Infrastructure as Code (IaC) files and reusable custom modules.
* **Subfolders:**
  * `backend/`: Configuration for remote backend state storage (e.g., S3 / GCS buckets).
  * `environments/`: Parameter values and orchestrations partitioned by deployment targets:
    * `dev/`: Development environment settings.
    * `staging/`: Pre-production staging environment settings.
    * `prod/`: Production environment settings.
  * `modules/`: Internal reusable Terraform modules for managing cloud resources such as:
    * `dns/`: DNS zone and record management.
    * `eks/`: Kubernetes cluster configuration.
    * `kafka/`: Managed message broker configuration.
    * `networking/`: VPC, subnets, and routing table setups.
    * `postgres/`: Managed relational database configuration.
    * `qdrant/`: Vector database configuration.
    * `redis/`: Caching and session store configurations.
    * `s3/`: Object storage bucket definitions.
    * `secrets/`: Secret manager / vault resource setup.

### 7. [`packages/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages)
Contains shared libraries and reusable internal packages. These are local package dependencies that are imported and shared across the apps in the `apps/` directory.
* **Subfolders:**
  * [`packages/config/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/config): Shared configuration setups (such as ESLint, Prettier, Tailwind configurations).
  * [`packages/shared-types/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/shared-types): Common type definitions and interface schemas shared between frontend and backend.
  * [`packages/ui/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/ui): Reusable UI components library.

### 8. [`scripts/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/scripts)
Utility, deployment, automation, and tooling scripts.
* **Rule:** Any multi-step terminal workflows or task automation helpers should be placed here and documented.

---

## Root-Level Files

* [`docker-compose.yml`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docker-compose.yml): Used to orchestrate and run local support services (like Postgres, Redis, Kafka) inside Docker containers for local development.
* [`Makefile`](file:///c:/Users/navne/EasyTaxInd/tax-ai/Makefile): Provides a standard command wrapper interface to build, test, format, and run the monorepo workspace components.
* [`README.md`](file:///c:/Users/navne/EasyTaxInd/tax-ai/README.md): High-level introduction, quickstart guide, and build prerequisites.
* [`.gitignore`](file:///c:/Users/navne/EasyTaxInd/tax-ai/.gitignore): Specifies files and folders that Git should ignore (e.g., node_modules, .env files, build artifacts).
