```markdown
# BSS Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development patterns and conventions used in the BSS JavaScript codebase. You'll learn how to structure files, write imports and exports, follow commit message practices, and set up and run tests. The repository uses plain JavaScript without a framework, emphasizing clarity and consistency in file organization and code style.

## Coding Conventions

### File Naming
- Use **kebab-case** for all file names.
  - Example:  
    ```
    user-profile.js
    data-fetcher.test.js
    ```

### Imports
- Use **relative import paths**.
  - Example:
    ```javascript
    import { fetchData } from './data-fetcher.js';
    ```

### Exports
- Use **named exports**.
  - Example:
    ```javascript
    // In user-profile.js
    export function getUserProfile(id) { ... }
    ```

### Commit Messages
- Commit messages are **freeform** (no enforced prefix), with an average length of 64 characters.
  - Example:
    ```
    Fix issue with user profile loading on slow connections
    ```

## Workflows

### Adding a New Module
**Trigger:** When you need to add new functionality as a module  
**Command:** `/add-module`

1. Create a new file using kebab-case (e.g., `new-feature.js`).
2. Implement your logic using named exports.
    ```javascript
    // new-feature.js
    export function doSomething() { ... }
    ```
3. Import your module where needed using a relative path.
    ```javascript
    import { doSomething } from './new-feature.js';
    ```
4. Add a corresponding test file named `new-feature.test.js`.

### Writing and Running Tests
**Trigger:** When you add or update code that needs testing  
**Command:** `/run-tests`

1. Create a test file named using the pattern `*.test.js` (e.g., `data-fetcher.test.js`).
2. Write your test cases (testing framework is unknown; follow existing patterns).
3. Run the tests using the project's preferred method (consult project docs or package.json scripts).

### Committing Changes
**Trigger:** When you have made code changes  
**Command:** `/commit-changes`

1. Stage your changes.
2. Write a clear, descriptive commit message (no strict prefix required).
    ```
    Update data fetching logic for improved performance
    ```
3. Commit your changes.

## Testing Patterns

- Test files follow the pattern `*.test.js`.
- The testing framework is not specified; check existing test files for structure.
- Place test files alongside or near the modules they test.

Example:
```
data-fetcher.js
data-fetcher.test.js
```

## Commands
| Command         | Purpose                                    |
|-----------------|--------------------------------------------|
| /add-module     | Scaffold and integrate a new module        |
| /run-tests      | Run all test files in the codebase         |
| /commit-changes | Commit staged changes with a message       |
```
