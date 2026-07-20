# Commit Standards

This document establishes the guidelines for formatting commit messages in the `tax-ai` repository. We adhere strictly to the [Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/), which helps maintain a structured, machine-readable git history.

---

## Commit Message Format

Commit messages must follow the structure below:

```text
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

* **Type**: Categorizes the change (e.g., `feat`, `fix`).
* **Scope** (Optional but highly recommended): Specifies the affected area of the monorepo (e.g., `api`, `web`, `worker`).
* **Description**: A short, imperative-mood summary of the change (e.g., "add authentication middleware" instead of "added authentication middleware").

---

## Types and Examples

| Type | Description | Example |
| :--- | :--- | :--- |
| `feat` | A new feature | `feat(api): add authentication middleware`<br>`feat(rag): implement hybrid retrieval` |
| `fix` | A bug fix | `fix(worker): retry failed Kafka messages` |
| `docs` | Documentation only changes | `docs: add repository guide` |
| `refactor` | A code change that neither fixes a bug nor adds a feature | `refactor(api): simplify dependency injection` |
| `test` | Adding missing tests or correcting existing tests | `test(api): add auth integration tests` |
| `ci` | Changes to CI configuration files and scripts | `ci: add GitHub Actions workflow` |
| `build` | Changes that affect the build system or external dependencies | `build(docker): optimize Dockerfile` |
| `perf` | A code change that improves performance | `perf(rag): cache embeddings vectors` |
| `style` | Formatting, white-space, semicolon additions (no logic changes) | `style(ui): format login button padding` |

---

## Key Benefits

Adhering to these standards provides significant benefits as the codebase grows:

* **Clear and Readable History**: Developers can scan the git log to quickly understand what changes were introduced and what applications they impacted.
* **Automatic Changelog Generation**: Automated tooling can parse the conventional commit tags to generate precise releases and changelogs automatically.
* **Easier Release Management**: Simplifies semantic versioning (Major/Minor/Patch determinations) based on commit types (e.g., `feat` indicates a minor version bump, `fix` indicates a patch bump, and `BREAKING CHANGE` footer indicates a major bump).
