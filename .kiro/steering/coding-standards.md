---
inclusion: auto
---

# Coding Standards

## General Principles
- Write minimal code. Every line must earn its place.
- Clear, readable names: `snake_case` for backend, `camelCase` for frontend.
- Short functions — one function does one thing.
- Return early on errors, avoid deep nesting.
- No dead code, no unnecessary abstractions.

## API Response Format
- Use a consistent response envelope across all endpoints.
- Always include appropriate HTTP status codes.

## Database Conventions
- UUID primary keys
- `TIMESTAMPTZ` for all timestamps
- `BIGINT` for money (store in smallest currency unit, e.g., cents)

## AI Coding Pitfalls — Always Check For These

### 1. Race Conditions in Async Flows
Never write only the happy path. Always consider concurrent requests, double-clicks,
overlapping async calls, and shared mutable state. Use DB transactions or mutex where needed.

### 2. Silent Error Swallowing
Never write try/catch that catches everything and logs nothing.
Every catch must log with context or re-throw.

### 3. Naive Retry Logic
Never retry without exponential backoff and a max retry limit.
Use backoff: 1s → 2s → 4s, then give up. Max 3 retries.

### 4. State Assumptions
Never assume clean state. Production has dirty data, partial writes, null fields.
Always validate state before acting on it.

### 5. Missing Idempotency
Every payment handler, webhook, and state-changing API must be idempotent.
Use unique request IDs, `ON CONFLICT` upserts, and idempotency keys.
