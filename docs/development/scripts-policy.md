# Scripts Policy

This document outlines the policy, directory structure, and runtime expectations for files residing in the [`scripts/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/scripts) directory of the `tax-ai` monorepo.

---

## Core Purpose

The [`scripts/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/scripts) directory is reserved **exclusively** for task automation, CI/CD helper tasks, utility orchestration, and environment setup scripts.

Any file placed under `scripts/` must be an executable script (or utility module supporting one) designed to replace or simplify command-line tasks for developers or pipelines.

---

## Directory & File Examples

Here are standard examples of scripts that belong in this folder:

| Script Name | Purpose | Language / Tooling |
| :--- | :--- | :--- |
| `bootstrap.sh` | Sets up developer environment prerequisites, installs SDK/package manager dependencies, and validates system tools. | Bash / shell |
| `seed.py` | Populates local or staging databases with fake/mock seed data for testing purposes. | Python |
| `wait-for-db.sh` | Blocks execution/CI pipelines until the target database service is fully up, responsive, and accepting TCP connections. | Bash / netcat |
| `deploy.sh` | Packages build assets and interacts with deployment interfaces or Helm charts. | Bash / AWS CLI |

---

## Scripting Rules & Best Practices

To maintain reliable and reproducible workspaces, scripts must adhere to the following guidelines:

### 1. Write Idempotent Scripts
Scripts should be written such that running them multiple times consecutively results in the same system state as running them once, without throwing errors or duplicating database records.
* **Database Seeding:** Ensure database seed scripts perform upsert operations (or truncate table contents beforehand) instead of blindly appending records.
* **Environment Setup:** Checking if a tool is already installed before attempting to re-download or reinstall it.
* **File Manipulations:** Appending lines to configurations (like `.env`) only if the entry does not already exist.

### 2. Avoid Manual Steps
Whenever a developer workflow or pipeline requires manual command execution, attempt to script it.
* **Rule:** If a process requires more than two CLI commands or has complex parameters, encapsulate it in a script.
* **Rationale:** Reduces cognitive load, limits human error in deployments, and makes onboarding new engineers frictionless.

### 3. Standards & Portability
* **Portability:** Write scripts to be cross-platform where possible (e.g. support both macOS/Linux, or provide alternative PowerShell/Python scripts for Windows if Shell scripts are not portable).
* **Shebang & Permissions:** Ensure Shell/Python scripts have the correct shebang lines (e.g., `#!/usr/bin/env bash` or `#!/usr/bin/env python3`) and are marked as executable (`chmod +x`).
* **Clean Exits:** Always return appropriate exit status codes (e.g., `0` for success, non-zero for failure) to ensure CI/CD engines (like GitHub Actions) fail-fast when a script breaks.
