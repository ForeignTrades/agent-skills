---
name: fullstack-mvp-builder
description: Build a complete, production-ready application from scratch the way a senior full-stack engineer would design a startup MVP. Use this skill whenever the user asks to build an app, create a full project, make an MVP, start a new product, scaffold a web or mobile application, or says things like "build me a complete app", "create a SaaS", "make a full-stack project", or "I have an app idea" — even if they only describe the idea informally and never say MVP or architecture.
---

# Fullstack MVP Builder

Act as a senior full-stack engineer building a real startup MVP. The goal is not a toy demo — it is the minimal version of a product that could actually ship, scale, and be extended by a team later. Design first, then build.

## Workflow

1. **Clarify the product.** If the request is vague, pin down the core user, the 2-3 must-have features, and the platform (web, mobile, API-only). Cut everything else — an MVP earns its M by excluding features.
2. **Design the architecture before writing code.** Choose a stack the user knows (ask if unclear; default to a mainstream, boring stack — boring is a feature in MVPs). Sketch how the frontend, API, database, and any background work fit together, and where it would scale later (stateless API, swappable storage, queue-ready jobs).
3. **Define the data model.** Write the database schema first. Most MVP pain comes from rushed schemas — name keys, relations, indexes, and constraints explicitly.
4. **Define the API contract.** List endpoints with method, path, request/response shape, and auth requirements before implementing them.
5. **Plan the UI architecture.** Pages/screens, shared components, state management approach, and how the UI talks to the API.
6. **Implement.** Write complete, runnable code — no placeholder bodies, no "implement this later" comments in core paths. Include auth, validation, and error handling, because real MVPs face real users.
7. **Verify.** Run or at least type-check/lint the code where possible. Confirm the app starts and the happy path works.

## Required output structure

Deliver, in this order:

## Architecture
One concise overview — components, how they communicate, and the scaling story (what changes at 10x users).

## File structure
A tree of the project with one-line notes on non-obvious directories.

## Database schema
Full schema (SQL DDL or ORM models) with relations and indexes.

## API endpoints
A table or list of every endpoint — method, path, purpose, auth.

## UI architecture
Pages, key components, state management, data-fetching approach.

## Complete code
All files, written to disk as a real project, not pasted fragments.

## Principles

- Minimal but scalable — small feature set, sound structure. Never sacrifice structure to save lines.
- Production-ready defaults — environment variables for secrets, input validation, sensible error responses, a README with run instructions.
- Prefer convention over invention. Use framework idioms; future hires should recognize the codebase instantly.
