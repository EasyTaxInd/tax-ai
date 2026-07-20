# Shared Packages (`packages/`)

This directory houses the internal shared libraries and configurations used across the applications in the `tax-ai` monorepo.

---

## Purpose

The `packages/` directory is designed to promote code reusability, modular design, and standard configuration sharing. Code here is published locally within the monorepo workspace and imported by applications inside the [`apps/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps) folder.

---

## Contents

* [`packages/ui/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/ui): Reusable UI component library shared across web interfaces.
* [`packages/shared-types/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/shared-types): Shared data structures, TypeScript interfaces, and API payload schemas.
* [`packages/config/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/packages/config): Shared linting configurations (ESLint), compilers (tsconfig), and styling (Tailwind).

---

## Guidelines for Adding New Packages/Files

1. **Naming Convention**: Package directories must use `kebab-case` and be lowercase (e.g., `packages/database-client/`).
2. **Strict Isolation**: Packages must never import code from [`apps/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/apps). They should represent the base layers of the dependency tree.
3. **No Business Logic or Env Secrets**: Keep packages generic and stateless. Inject configurations, environments, and secrets from the consuming applications at runtime.
4. **Reference Documentation**: For a full list of rules, checks, and architectural patterns, refer to [Package Rules](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/package-rules.md).
