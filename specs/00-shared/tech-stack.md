# TECH-STACK.md

**Project:** Requira
**Version:** 1.0
**Status:** Approved
**Owner:** Engineering
**Document Type:** Shared Technology Stack & Engineering Decisions

---

# 1. Purpose

This document defines the technology stack used to build Requira and explains the reasoning behind each major technical decision.

The chosen technologies should support the product vision while keeping the MVP realistic, maintainable, and scalable. Technology should always serve the product rather than drive it.

---

# 2. Engineering Philosophy

The technology stack has been selected based on the following principles:

* Keep the architecture simple and modular.
* Use widely adopted technologies with strong community support.
* Favor maintainability over unnecessary complexity.
* Design for future scalability without over-engineering the MVP.
* Ensure the project demonstrates practical Full Stack and AI Engineering skills.

---

# 3. Frontend

### Framework

* React

### Language

* JavaScript (ES6+) *(TypeScript may be adopted in future iterations.)*

### Styling

* Tailwind CSS

### Routing

* React Router

### HTTP Client

* Axios

### State Management

* React Context API (MVP)

The frontend is responsible for:

* User authentication
* Project management
* Document upload
* Audit visualization
* Dashboard
* Report viewing

The frontend should remain a presentation layer, with business logic handled by backend services.

---

# 4. Backend

### Runtime

* Node.js

### Framework

* Express.js

The backend is responsible for:

* Authentication
* Project management
* File management
* AI workflow orchestration
* API services
* Report generation
* Database interactions

Business logic should reside in service layers rather than controllers.

---

# 5. Database

### Primary Database

* MongoDB

MongoDB stores:

* Users
* Workspaces
* Projects
* Documents
* Audit results
* Findings
* Reports
* Metadata

MongoDB is selected because the application primarily works with document-oriented data and evolving AI-generated structures.

---

# 6. Artificial Intelligence

### Large Language Model

* Groq (LLM Provider)

Responsibilities:

* Requirement extraction
* Requirement classification
* Gap analysis
* Risk analysis
* Clarification question generation
* Test scenario generation
* Recommendation generation

The LLM should never make autonomous project decisions. It provides structured recommendations that support human review.

---

# 7. Workflow Orchestration

### Framework

* LangGraph

Purpose:

LangGraph orchestrates the complete audit workflow as a stateful sequence of processing nodes.

Responsibilities include:

* Managing workflow execution
* Maintaining shared audit state
* Coordinating analysis stages
* Supporting retries and future workflow extensions

LangGraph is used for orchestration, not for building autonomous multi-agent systems.

---

# 8. Retrieval-Augmented Generation (RAG)

### Vector Store

* FAISS

The RAG pipeline is responsible for:

* Storing embedded knowledge
* Retrieving relevant audit frameworks
* Providing contextual information to the LLM
* Improving explainability
* Reducing hallucinations

The knowledge base contains curated requirement engineering guidance rather than project-specific data.

---

# 9. Document Processing

Supported formats:

* PDF
* DOCX

Document processing pipeline:

1. Upload document
2. Extract text
3. Clean and normalize content
4. Chunk document
5. Generate embeddings
6. Store vectors
7. Begin audit workflow

Future support for additional formats may be added without changing the core architecture.

---

# 10. Authentication

Authentication responsibilities include:

* User registration
* Login
* Secure sessions
* Protected routes
* Role-based access (future)

Authentication should remain independent of the AI workflow.

---

# 11. Folder Structure

The project follows a modular, feature-oriented structure.

High-level organization includes:

Frontend

* Components
* Pages
* Features
* Services
* Context
* Utilities

Backend

* Routes
* Controllers
* Services
* Middleware
* Models
* AI
* RAG
* LangGraph
* Reports

Specifications

* Shared documentation
* Phase-based SDD documents

This separation improves maintainability and scalability.

---

# 12. External Services

The MVP may integrate with:

* Groq API
* FAISS Vector Index
* PDF/DOCX parsing libraries

Future integrations such as Jira, Azure DevOps, and cloud storage are outside the MVP scope.

---

# 13. Environment Configuration

Sensitive configuration values should be stored using environment variables.

Examples include:

* Database connection strings
* LLM API keys
* Authentication secrets
* Application configuration
* File storage settings

Secrets should never be committed to version control.

---

# 14. Future Evolution

The current technology stack is intentionally optimized for the MVP.

Future versions may introduce:

* TypeScript
* NestJS
* PostgreSQL (if relational requirements emerge)
* Redis
* Background job queues
* Cloud object storage
* Containerization
* CI/CD pipelines
* Monitoring and observability tools

These enhancements should build upon the existing modular architecture without requiring major redesign.

---

# 15. Technology Principles

Every future technology decision should satisfy the following principles:

* Support the product vision.
* Keep the architecture modular.
* Avoid unnecessary complexity.
* Prefer mature and maintainable technologies.
* Preserve explainability within AI workflows.
* Ensure the system remains easy to extend and refactor.

The technology stack is an implementation choice, not the product's identity. Requira should be recognized for solving a real software engineering problem rather than for the technologies used to build it.
