# Package Rules

This document outlines the conventions, rules, and guidelines for adding and maintaining packages in the [`packages/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages) directory of the `tax-ai` monorepo.

---

## Core Principles

The [`packages/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages) directory is reserved **exclusively** for shared, reusable libraries. It acts as the backbone of our monorepo architecture, helping avoid code duplication across deployable applications.

All code placed within `packages/` must strictly adhere to the following rules:

### 1. No Application-Specific Business Logic
Shared packages must remain generic and domain-agnostic. 
* **Do not** write code that is coupled to a specific application flow (e.g., how the backend API formats a specific endpoint response for the worker).
* **Instead:** Design packages to expose primitive structures, utility helpers, and components that applications can compose to form business logic.

### 2. No Environment-Specific Configuration
Packages must never hardcode environment-specific config values (such as database URLs, specific API hostnames, API keys, or operational environment switches like `dev` / `prod`).
* **Do not** import `.env` variables directly in packages.
* **Instead:** Design packages to accept configuration at initialization time (e.g., via config builders, environment providers, or runtime arguments).

### 3. Reusability Requirement
A library should only reside in `packages/` if it is intended to be consumed by **two or more** apps, or if it provides global infrastructure configuration (such as workspace build tools or compiler configs).
* **Rule of Thumb:** If a component is only used by `apps/web/`, keep it inside `apps/web/src/components/`. Once it is needed by another app (e.g., a documentation portal or mobile client), promote it to `packages/ui/`.

---

## Workspace Package Layout

The monorepo contains (or will eventually contain) the following core packages:

| Package | Purpose | Consumer Scope | Examples |
| :--- | :--- | :--- | :--- |
| [`packages/ui/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/ui) | Shared UI design system and components | Frontend Apps (`web`, mobile, etc.) | Buttons, Input fields, Modal wrappers, Theme providers |
| [`packages/shared-types/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/shared-types) | Common interfaces, API contracts, and schema validators | All Apps (`web`, `api`, `worker`) | API request payloads, DB models, event schemas |
| [`packages/config/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/config) | Shared tooling, compiler setups, and linter rules | All Workspace Projects | ESLint config, Prettier config, TSConfig, Tailwind config |
| `packages/sdk/` | Client SDKs for interacting with internal or third-party APIs | Integrations / Client Apps | HTTP SDK client wrapper, authentication SDK clients |

---

## Compliance Checklist for Creating a New Package

When creating a new package under `packages/`:

* [ ] **kebab-case directory naming**: Ensure the folder uses `kebab-case` naming conventions (e.g., `packages/database-client/`).
* [ ] **Declutter dependencies**: Ensure dependencies in the package's `package.json` are minimal. Peer dependencies should be used for UI frameworks to avoid runtime duplicate instances (e.g., `react`).
* [ ] **Strict isolation**: Verify that the package does not import from any directory under `apps/`.
* [ ] **Stateless/Injection-based**: Ensure configurations (like API urls) are injected at runtime by the consuming app, not read from global files.
