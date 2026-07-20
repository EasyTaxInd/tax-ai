# Deployable Applications (`apps/`)

This directory contains the standalone, buildable, and deployable applications of the `tax-ai` monorepo.

---

## Purpose

The `apps/` directory is the home for end-user applications and service entry points. Each subdirectory here represents an independent application that is separately built, containerized, and deployed to our infrastructure environments.

---

## Contents

* [`apps/web/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps/web): The React/Next.js frontend user interface.
* [`apps/api/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps/api): The primary backend REST/WebSocket service.
* [`apps/worker/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps/worker): A headless queue consumer for running background workflows.

---

## Guidelines for Adding New Applications/Files

1. **Naming Convention**: Application directories must use `kebab-case` and be lowercase (e.g., `apps/admin-dashboard/`).
2. **Boundary Restrictions**: Applications must never directly import source code files from each other. If you need to share code, extract it to a shared module in the [`packages/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages) directory.
3. **Independent Configurations**: Each new application must have its own dependencies management configuration (e.g., `package.json` or `pyproject.toml`) and be runnable independently.
4. **Reference Documentation**: For details on architectural constraints, refer to [Application Boundaries](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/application-boundaries.md).
