# Contributing to tax-ai

Thank you for your interest in contributing to `tax-ai`! This document outlines the standards, workflows, and conventions to follow when contributing code, writing documentation, or configuring infrastructure in this repository.

---

## 1. Branch Naming Conventions

All feature, fix, or patch branches must follow the standard prefixing and kebab-case naming model:
* **Features:** `feature/<kebab-case-description>` (e.g., `feature/user-authentication`)
* **Bug Fixes:** `bugfix/<kebab-case-description>` (e.g., `bugfix/login-timeout`)
* **Hot Fixes:** `hotfix/<kebab-case-description>` (e.g., `hotfix/openai-api-error`)

For a detailed explanation, examples, and lifecycle rules, see the [Branching Strategy](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/branch-strategy.md).

---

## 2. Commit Message Format

We enforce the **Conventional Commits** specification. Commit messages must be structured as:
```text
<type>(<scope>): <description>
```
* **Types:** `feat`, `fix`, `docs`, `refactor`, `test`, `ci`, `build`, `perf`, `style`.
* **Scopes:** Optional but highly recommended (e.g., `api`, `web`, `worker`, `docker`).
* **Example:** `feat(api): add authentication middleware`

For a full list of types, examples, and benefits, see the [Commit Standards](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/commit-standards.md).

---

## 3. Pull Request Process

To submit code changes:
1. Create a feature or bugfix branch off the latest `main`.
2. Commit your code and push it to GitHub.
3. Open a Pull Request (PR) to the `main` branch.
4. Fill out the [Pull Request Template](file:///c:/Users/navne/EasyTaxInd/tax-ai/.github/PULL_REQUEST_TEMPLATE.md) completely.
5. Ensure all automated GitHub Actions checks pass.
6. Once approved, merge the PR using **Squash and Merge**, and delete your feature branch.

For a detailed visual guide and code snippets, see the [Development Workflow](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/development-workflow.md).

---

## 4. Coding & Architecture Standards

Please familiarize yourself with our repository standards before making changes:
* **Repository Layout:** Understand where folders belong by reading the [Repository Structure and Ownership Guide](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/repository-structure.md).
* **Code Naming:** Follow standard naming conventions (directories vs. Python files vs. React files) in the [Naming Conventions Guide](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/naming-conventions.md).
* **Application Boundaries:** Respect the separation of frontend, backend, and workers detailed in the [Application Boundaries Guide](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/application-boundaries.md).
* **Shared Packages:** Follow rules for developing reusable libraries under `packages/` in the [Package Rules Guide](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/package-rules.md).
* **Import Restrictions:** Adhere to the strict unidirectional dependency graph in the [Import Rules Guide](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/import-rules.md).
* **Infrastructure Rules:** Organize cloud configurations according to the [Infrastructure Standards](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/infrastructure-standards.md).
* **Automation Scripts:** Keep scripts idempotent and automated by following the [Scripts Policy](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/scripts-policy.md).

---

## 5. How to Run the Project Locally

For instructions on setting up your local environment, managing dependencies, and launching the application stack locally, please refer to:
* **Root Entrypoint:** Read the root [README.md](file:///c:/Users/navne/EasyTaxInd/tax-ai/README.md) for quick-start commands and system prerequisites.
* **Local Run workflows:** Refer to the [Development Workflow](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/development-workflow.md) for the active command steps used to initialize, code, test, and push your changes.
