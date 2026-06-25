# CODING-STANDARDS.md

**Project:** Requira
**Version:** 1.0
**Status:** Approved
**Owner:** Engineering
**Document Type:** Shared Coding Standards

---

# 1. Purpose

This document defines the engineering standards used throughout the Requira codebase.

The objective is to maintain a clean, consistent, and maintainable codebase that is easy to understand, extend, and review. These standards prioritize readability and long-term maintainability over clever or overly optimized implementations.

---

# 2. Engineering Principles

Every contribution to Requira should follow these principles:

* Write code for humans first.
* Keep modules small and focused.
* Prefer clarity over cleverness.
* Avoid premature optimization.
* Build reusable components where appropriate.
* Keep business logic independent of presentation.
* Follow the Single Responsibility Principle whenever practical.

---

# 3. Naming Conventions

### Files

Use lowercase with hyphens.

Examples:

```text
project-service.js
audit-engine.js
document-parser.js
```

---

### Components

Use PascalCase.

Examples:

```text
Dashboard.jsx
ProjectCard.jsx
UploadModal.jsx
```

---

### Variables

Use camelCase with descriptive names.

Good:

```javascript
projectId
uploadedDocument
requirementHealth
```

Avoid:

```javascript
temp
obj
x
data1
```

---

### Functions

Functions should clearly describe their behavior.

Examples:

```javascript
createProject()
extractRequirements()
generateAuditReport()
calculateRequirementHealth()
```

Avoid generic names like:

```javascript
run()
handle()
process()
```

unless their purpose is immediately obvious from context.

---

# 4. Folder Organization

Organize code by feature rather than by technical layer whenever practical.

Example:

```text
features/

authentication/

projects/

documents/

audit/

reports/
```

Shared functionality belongs in dedicated shared modules.

Avoid placing unrelated logic in common utility folders.

---

# 5. Component Guidelines

Frontend components should follow these principles:

* One responsibility per component.
* Keep components small.
* Separate UI from business logic.
* Prefer composition over deeply nested components.
* Extract reusable UI patterns into shared components.

Components should avoid directly communicating with external services whenever possible.

---

# 6. Backend Guidelines

Controllers should:

* Validate requests.
* Call services.
* Return responses.

Controllers should **not** contain business logic.

Business logic belongs inside service modules.

Database access belongs inside model or repository layers.

This separation keeps the backend modular and easier to maintain.

---

# 7. Error Handling

Errors should be handled gracefully.

Every error should:

* Be logged.
* Return meaningful messages.
* Avoid exposing internal implementation details.
* Be consistent across APIs.

Avoid silent failures.

---

# 8. Logging

Log important application events such as:

* User authentication
* Project creation
* Document uploads
* Audit execution
* Report generation
* Unexpected failures

Logs should provide useful debugging information without exposing sensitive user data.

---

# 9. Comments & Documentation

Code should be self-explanatory whenever possible.

Comments should explain:

* Why something exists.
* Business rules.
* Complex decisions.

Avoid comments that simply repeat what the code already expresses.

Example:

Good:

```javascript
// Retry extraction because OCR occasionally fails on scanned PDFs.
```

Avoid:

```javascript
// Increment count.
count++;
```

---

# 10. Git Practices

Use clear, descriptive commit messages.

Examples:

```text
Add project creation workflow

Implement requirement extraction service

Improve audit dashboard filtering

Generate development readiness recommendation
```

Avoid vague commits such as:

```text
Update

Changes

Fix stuff

Final
```

Each commit should represent one logical unit of work.

---

# 11. General Code Quality

Before code is considered complete, verify that:

* It is readable.
* Naming is meaningful.
* Responsibilities are clearly separated.
* Error handling is implemented.
* Unused code has been removed.
* Magic values are avoided.
* Duplication has been minimized.
* The implementation aligns with the relevant SDD specifications.

---

# 12. Coding Philosophy

Requira is intended to demonstrate professional software engineering practices.

Every implementation should reflect the following mindset:

* Build maintainable software rather than quick fixes.
* Let specifications drive implementation.
* Prefer simple solutions before introducing complexity.
* Refactor when necessary, but avoid unnecessary abstraction.
* Write code that another engineer can understand without additional explanation.

The goal is not simply to make the application work, but to build a codebase that remains clean, extensible, and reliable as Requira grows beyond the MVP.
