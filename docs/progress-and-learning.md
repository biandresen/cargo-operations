# Progress and learning log

> Keep this compact and factual. Update after meaningful milestones or explicit requests, not on every conversation. Never mark planned features as implemented.

## Current state

- **Status:** Planning / project bootstrap (initial template; verify against repository).
- **Current milestone:** P0 — first vertical slice (React → .NET API → PostgreSQL → React).
- **Next actionable exercise:** Inspect or initialize the repository, then create and run the smallest ASP.NET Core API and PostgreSQL via Docker Compose.
- **Known blockers:** None confirmed; repository state and local setup not yet verified.

## What is working

- [ ] React frontend starts locally.
- [ ] ASP.NET Core API starts locally.
- [ ] PostgreSQL runs with persistent development storage.
- [ ] EF Core migration applies.
- [ ] Create and list shipments end to end.
- [ ] Test suite runs locally.
- [ ] CI runs on pull requests.
- [ ] Staging deployment and smoke checks work.
- [ ] Production demo deploy and rollback process work.

## Learning objectives

- Understand C# types, records, nullability and async compared with TypeScript.
- Understand ASP.NET Core DI, middleware, routing and HTTP contracts compared with Express.
- Understand EF Core models, queries and migrations compared with PostgreSQL/Prisma.
- Write effective unit, integration and Playwright E2E tests.
- Learn Docker networking/volumes, CI/CD gates and environment separation.

## Session log template

### YYYY-MM-DD — Short topic

- **Goal:**
- **I implemented/verified:**
- **Concepts understood (in my own words):**
- **Mistakes/debugging lessons:**
- **Tests/checks actually run:**
- **Open questions:**
- **Next smallest exercise:**

## Important constraints

- The person learning should own their work; Codex should not write fictitious learning outcomes.
- Record specific verified facts with relevant paths/commands; avoid copying entire chat transcripts into this document.
- Keep decisions in ADR files, not in free-floating notes.
