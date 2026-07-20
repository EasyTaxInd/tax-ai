# Naming Conventions

This document establishes the official naming conventions for directories and files across the `tax-ai` monorepo. Consistent naming increases codebase readability, searchability, and tooling compatibility.

---

## Directories

All directory names must be **lowercase** and use **kebab-case** (words separated by hyphens). This applies to all folders under `apps/`, `packages/`, `infra/`, and custom subdirectories.

| Correct Example (kebab-case) | Incorrect Example | Rationale |
| :--- | :--- | :--- |
| `user-service` | `UserService` | PascalCase is reserved for React/UI components and classes |
| `auth-api` | `User_Service` | snake_case is avoided for directories to remain web-friendly |
| `shared-types` | `userservice` | Lack of separation reduces readability |

---

## Files

File naming conventions are based on the language, framework context, and purpose of the file.

### 1. Python Files
Python source files must be **lowercase** and use **snake_case** (words separated by underscores). This aligns with standard Python conventions ([PEP 8](https://peps.python.org/pep-0008/)).

* **Convention:** `lowercase_with_underscores.py`
* **Examples:**
  * `user_service.py`
  * `auth_router.py`
  * `db_connection.py`

### 2. React Components
React component files must use **PascalCase** to signify that they export React components (which must also be named in PascalCase in JSX).

* **Convention:** `PascalCase.tsx` / `PascalCase.jsx`
* **Examples:**
  * `SearchBar.tsx`
  * `ChatWindow.tsx`
  * `UserProfileCard.tsx`

### 3. React / Custom Hooks
React hooks must be **camelCase** and must always start with the prefix `use` (aligning with React's Rules of Hooks).

* **Convention:** `useCamelCase.ts` / `useCamelCase.js`
* **Examples:**
  * `useAuth.ts`
  * `useSearch.ts`
  * `useLocalStorage.ts`

### 4. General TypeScript / JavaScript Files
General helper files, utility libraries, and configuration files that do not export React components or hooks should use **kebab-case** or **camelCase**.

* **Convention:** `kebab-case.ts` or `camelCase.ts`
* **Examples:**
  * `date-utils.ts`
  * `apiClient.ts`

---

## Summary Reference Table

| Target | Convention | Examples |
| :--- | :--- | :--- |
| **Directories** | `kebab-case` | `user-service/`, `shared-types/` |
| **Python Files** | `snake_case` | `user_service.py`, `auth_router.py` |
| **React Components** | `PascalCase` | `SearchBar.tsx`, `ChatWindow.tsx` |
| **React Hooks** | `camelCase` (starts with `use`) | `useAuth.ts`, `useSearch.ts` |
| **General Utilities** | `kebab-case` or `camelCase` | `date-formatter.ts`, `apiClient.ts` |
