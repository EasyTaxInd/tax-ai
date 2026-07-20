# Automation Scripts (`scripts/`)

This directory houses command-line scripts, environment setup files, automation helpers, and deployment drivers for the `tax-ai` monorepo.

---

## Purpose

The `scripts/` directory is dedicated to replacing manual tasks with automated, reproducible code. It reduces onboarding setup time, limits human error in environments, and standardizes build/deploy operations.

---

## Contents

* `bootstrap.sh`: Interactive or automated setup script for fresh development machines.
* `seed.py`: Python database seeder for inserting local mock data.
* `wait-for-db.sh`: Block script utility ensuring databases are live before application startups.

---

## Guidelines for Adding New Scripts

1. **Idempotency**: Scripts must be idempotent. Running them multiple times in succession should never duplicate records, break systems, or leave file setups in corrupt states.
2. **Standard Headers**: Always start with the appropriate shebang (e.g., `#!/usr/bin/env bash` or `#!/usr/bin/env python3`).
3. **Executable Permission**: Ensure scripts are marked as executable by running `chmod +x <filename>` before pushing to Git.
4. **Exit Codes**: Always return an appropriate exit code (`0` for success, non-zero for failures) so CI/CD execution engines can identify breaks.
5. **Reference Documentation**: For a full list of coding standards and guidelines, refer to the [Scripts Policy](file:///c:/Users/navne/EasyTaxInd/tax-ai/docs/development/scripts-policy.md).
