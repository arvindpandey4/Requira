# Requira

> AI-powered Requirements Intelligence Platform that transforms unstructured business information into structured, traceable project requirements and deliverables.

## Overview

Requira acts as an intelligent business analysis copilot for Business Analysts, Product Managers, and Project Managers. It ingests unstructured inputs — meeting transcripts, discovery notes, emails, recordings, and documents — and automatically produces structured, reviewable, and traceable project requirements.

## Key Capabilities

- **Requirement Extraction** — Automatically identifies functional requirements, non-functional requirements, business rules, assumptions, constraints, dependencies, risks, stakeholders, and open questions from uploaded artifacts.
- **Artifact Generation** — Produces BRDs, SRS documents, user stories, acceptance criteria, epics, features, development tasks, and test scenarios.
- **Quality Analysis** — Continuously detects ambiguities, missing information, risks, edge cases, and generates intelligent follow-up questions.
- **Collaborative Workspace** — Teams can review, edit, discuss, approve, version, and manage requirements throughout the project lifecycle.
- **Traceability** — Maintains complete traceability between original source material and final deliverables.

## Tech Stack

| Layer     | Technology                        |
|-----------|-----------------------------------|
| Frontend  | React 19, Vite, ESLint            |
| Backend   | Node.js, Express.js               |
| AI/ML     | LLM integration (planned)         |
| Database  | TBD                               |

## Project Structure

```
Requira/
├── frontend/          # React + Vite frontend application
│   ├── src/
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
├── backend/           # Node.js + Express backend API
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── utils/
│   │   ├── app.js
│   │   └── server.js
│   ├── .env.example
│   └── package.json
└── specs/             # Project specifications and shared standards
    └── 00-shared/     # Architecture, design system, coding standards
```

## Getting Started

### Prerequisites

- Node.js >= 18
- npm >= 9

### Frontend

```bash
cd frontend
npm install
npm run dev
```

### Backend

```bash
cd backend
npm install
npm run dev
```

The backend exposes a health check at `GET /health`.

## Specs

Shared specification documents are in `specs/00-shared/` covering:

- Architecture principles
- Coding standards
- Design system
- Tech stack decisions
- Engineering standards
- Glossary
- Product vision

## License

ISC © Arvind Pandey
