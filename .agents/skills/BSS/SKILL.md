```markdown
# BSS Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns and workflows used in the BSS TypeScript codebase. You will learn the project's coding conventions, including file naming, import/export styles, commit patterns, and how to contribute new features or polish the user experience. The guide also covers testing patterns and provides handy commands for common workflows.

## Coding Conventions

**File Naming:**  
- Use PascalCase for all file names.
  - Example: `UserProfile.ts`, `MainComponent.ts`

**Import Style:**  
- Use relative imports for referencing other files.
  - Example:
    ```typescript
    import { UserService } from './UserService';
    ```

**Export Style:**  
- Use named exports for all modules.
  - Example:
    ```typescript
    export function calculateTotal() { ... }
    export const MAX_USERS = 10;
    ```

**Commit Patterns:**  
- Follow [Conventional Commits](https://www.conventionalcommits.org/) with the `feat` prefix for new features.
  - Example:
    ```
    feat: add user authentication to login page
    ```

## Workflows

### Feature Implementation and README Update
**Trigger:** When adding a new feature or UX improvement that requires documentation.  
**Command:** `/feature-readme-update`

1. Implement the new feature or UX change in `index.html`.
2. Update `README.md` to document the new feature or change.
3. Commit your changes using a conventional commit message, e.g.:
    ```
    feat: add dark mode toggle and document usage in README
    ```
4. Open a pull request for review.

**Example:**
```html
<!-- index.html -->
<button id="darkModeToggle">Toggle Dark Mode</button>
```
```markdown
<!-- README.md -->
## Dark Mode
Click the "Toggle Dark Mode" button to switch themes.
```

---

### UX Polish (Single File)
**Trigger:** When making small UX improvements or micro-interaction tweaks.  
**Command:** `/ux-polish`

1. Edit `index.html` to adjust UI/UX details.
2. Commit your changes with a descriptive message, e.g.:
    ```
    feat: improve button hover effect for better accessibility
    ```
3. Open a pull request for review.

**Example:**
```html
<!-- index.html -->
<style>
  button:hover {
    background-color: #f0f0f0;
  }
</style>
```

---

## Testing Patterns

- Test files follow the pattern `*.test.*` (e.g., `UserService.test.ts`).
- The specific testing framework is not detected, but tests are likely colocated with source files or in a dedicated test directory.
- To write a test:
    ```typescript
    // UserService.test.ts
    import { getUser } from './UserService';

    test('should return user by ID', () => {
      expect(getUser(1)).toEqual({ id: 1, name: 'Alice' });
    });
    ```

## Commands

| Command                 | Purpose                                                        |
|-------------------------|----------------------------------------------------------------|
| /feature-readme-update  | Add a new feature and update documentation                     |
| /ux-polish              | Make minor UX or UI improvements in the main UI file           |

```