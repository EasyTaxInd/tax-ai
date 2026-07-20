# Engineering Documentation (`docs/`)

This directory is the central repository for technical, architectural, operational, and onboarding documentation for the `tax-ai` project.

---

## Purpose

The `docs/` folder aims to serve as the "Single Source of Truth" (SSOT) for developers, systems engineers, and operations personnel. Keeping documentation alongside the source code ensures it remains close to execution and is version-controlled with system updates.

---

## Contents

* [`docs/adr/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/adr): Architecture Decision Records (ADRs) explaining major design pivots and choices.
* [`docs/api/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/api): REST API documentation and OpenAPI/Swagger specification definitions.
* [`docs/architecture/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/architecture): Higher-level system architecture diagrams and flow descriptions.
* [`docs/development/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development): Onboarding guides, coding standards, naming conventions, and repo rules (e.g. this set of standards).
* [`docs/runbooks/`](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/runbooks): Troubleshooting walkthroughs and step-by-step guides for operational issues.

---

## Guidelines for Adding New Documentation

1. **Format Standards**: Document everything in clear GitHub Flavored Markdown (`.md`).
2. **Relative Links**: When linking files or code references, use relative paths or click-safe file URIs to keep documentation interactive.
3. **Updating Process**: When code or architecture changes, update the associated documentation in the same pull request.
4. **Writing ADRs**: Follow the standard ADR template (Context, Decision, Consequences) when introducing new structural tools, databases, or conventions.
