# PLATFORM-STANDARDS.md

**Project:** Requira
**Version:** 1.0
**Status:** Approved
**Owner:** Engineering
**Document Type:** Shared Platform Standards

---

# 1. Purpose

This document defines the platform-wide standards for APIs, database design, data consistency, and application behavior across Requira.

These standards ensure that every module follows a consistent approach when exposing APIs, storing data, handling responses, and managing resources. Phase-specific specifications may extend these standards but should not contradict them.

---

# 2. API Standards

All backend services should expose RESTful APIs with consistent naming, request handling, and response structures.

### API Design Principles

* Resource-oriented endpoints
* Predictable URL structure
* Stateless requests
* JSON request and response bodies
* Consistent validation
* Consistent error handling

---

### Endpoint Naming

Use plural nouns for resources.

Examples:

```text
/api/auth
/api/projects
/api/documents
/api/audits
/api/reports
/api/users
```

Avoid action-based URLs such as:

```text
/createProject
/uploadFile
/runAudit
```

Actions should be represented using appropriate HTTP methods.

---

### HTTP Methods

| Method | Purpose                                |
| ------ | -------------------------------------- |
| GET    | Retrieve data                          |
| POST   | Create resources                       |
| PUT    | Replace existing resources             |
| PATCH  | Partial updates                        |
| DELETE | Soft delete resources where applicable |

---

# 3. Standard API Response Format

Every successful response should follow a consistent structure.

```json
{
    "success": true,
    "message": "Project created successfully.",
    "data": {}
}
```

Every failed response should follow the same structure.

```json
{
    "success": false,
    "message": "Validation failed.",
    "errors": []
}
```

This consistency simplifies frontend development and improves maintainability.

---

# 4. HTTP Status Codes

Use standard HTTP status codes.

| Status Code | Meaning                 |
| ----------- | ----------------------- |
| 200         | Successful request      |
| 201         | Resource created        |
| 400         | Invalid request         |
| 401         | Authentication required |
| 403         | Permission denied       |
| 404         | Resource not found      |
| 409         | Conflict                |
| 422         | Validation failed       |
| 500         | Internal server error   |

Avoid using `200 OK` for failed operations.

---

# 5. Validation Standards

Every API should validate incoming requests before processing.

Validation should include:

* Required fields
* Data types
* Allowed values
* File types
* Maximum file size
* Business rule validation

Invalid requests should return clear and meaningful validation errors.

---

# 6. Pagination & Filtering

Endpoints returning collections should support pagination.

Recommended query parameters:

```text
?page=1
&limit=10
&search=
&sortBy=
&order=
```

Filtering and searching should follow a consistent structure across all modules.

---

# 7. Database Standards

Database design should prioritize flexibility, consistency, and maintainability.

Collections should represent business entities rather than implementation details.

Examples include:

* Users
* Workspaces
* Projects
* Documents
* Audits
* Findings
* Reports

Collection names should remain lowercase and plural.

---

# 8. Common Database Fields

Every major entity should include common metadata fields where applicable.

Examples:

```text
id
createdAt
updatedAt
createdBy
updatedBy
status
```

These fields support auditing, debugging, and future scalability.

---

# 9. Soft Delete Policy

Business data should not be permanently removed unless explicitly required.

Deleted resources should instead be marked as inactive or archived.

Benefits include:

* Recovery
* Audit history
* Data integrity

Permanent deletion should be reserved for administrative operations.

---

# 10. Data Consistency

Platform-wide naming conventions should remain consistent.

Examples:

Use:

* projectId
* documentId
* auditId
* reportId

Avoid inconsistent identifiers such as:

* pid
* projID
* documentID
* audit_identifier

Consistency improves readability and simplifies maintenance.

---

# 11. Status Values

Application states should use predefined values instead of arbitrary strings.

Examples:

Project Status

```text
Draft
Active
Completed
Archived
```

Document Status

```text
Uploaded
Processing
Processed
Failed
```

Audit Status

```text
Pending
Running
Completed
Failed
```

Using standardized enums prevents inconsistent application behavior.

---

# 12. File Standards

Uploaded files should include metadata such as:

* Original filename
* File type
* File size
* Upload timestamp
* Processing status
* Associated project

Original files should remain unchanged after upload.

Processed content should be stored separately from source files.

---

# 13. Versioning Principles

Resources that evolve over time should support versioning where appropriate.

Examples include:

* Requirement documents
* Audit reports
* Generated findings

Version history should preserve previous records rather than overwrite them.

---

# 14. Platform Consistency Principles

Every feature developed for Requira should follow these platform principles:

* Consistent APIs
* Predictable database structure
* Uniform response formats
* Standardized status values
* Stable naming conventions
* Reusable design patterns
* Clear data ownership
* Maintainable resource organization

These principles ensure that new modules integrate seamlessly with the existing platform.

---

# 15. Platform Philosophy

Requira should feel like a single, cohesive product rather than a collection of independent features.

Every new API, database entity, and business module should follow the same platform conventions established in this document.

Consistency is considered a core architectural principle and should be preserved as the application grows beyond the MVP.
