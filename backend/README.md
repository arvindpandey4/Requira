# Requira Backend

Express.js backend API for the Requira platform.

## Setup

```bash
npm install
cp .env.example .env
npm run dev
```

## Health Check

```
GET /health
```

Returns `200 OK` with service status.

## Structure

```
src/
├── config/        # Configuration (db, env, etc.)
├── controllers/   # Route handlers
├── middleware/    # Express middleware
├── models/        # Data models
├── routes/        # Route definitions
├── services/      # Business logic
├── utils/         # Shared utilities
├── app.js         # Express app setup
└── server.js      # Server entry point
```
