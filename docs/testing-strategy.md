# Testing strategy

**Goal:** confidence in behavior and safe changes, not a headline coverage percentage. This is a plan, not evidence that tests already exist.

## Testing layers

| Layer                   | Proposed tools                                    | Focus                                                                 | Trigger                   |
| ----------------------- | ------------------------------------------------- | --------------------------------------------------------------------- | ------------------------- |
| Backend unit            | xUnit                                             | Pure business rules, status transitions, validation rules             | Every relevant PR         |
| Backend integration     | WebApplicationFactory + Testcontainers PostgreSQL | Real HTTP + API + EF Core + DB behavior                               | Every relevant PR         |
| Frontend unit/component | Vitest + React Testing Library                    | Components, accessibility, form behavior                              | Every relevant PR         |
| Frontend integration    | React Testing Library + MSW                       | Loading/error/success and request/response handling                   | Every relevant PR         |
| Browser E2E             | Playwright                                        | Small set of critical user journeys through real frontend and backend | CI, staging               |
| Post-deploy smoke       | HTTP checks + narrow Playwright flow              | Deployment is reachable, primary workflow works                       | After staging/prod deploy |

## Prioritized cases

### P0: first vertical slice

- [ ] Backend integration: create valid shipment → persisted row → GET returns it.
- [ ] Backend integration: duplicate reference / missing customer / non-positive weight rejected.
- [ ] Frontend: form validation, success message, loading/empty/error states.
- [ ] Playwright: create shipment → list → details, using an isolated test database.

### P1: business and operational risk

- [ ] Unit: allowed and forbidden status transitions.
- [ ] Integration: status change and event record commit atomically.
- [ ] Integration: duplicate external event doesn't duplicate history.
- [ ] Integration: unauthorized 401 and forbidden 403 where applicable.
- [ ] Integration: migrations apply to a clean PostgreSQL instance.
- [ ] E2E: issue displayed on dashboard; user permissions checked.
- [ ] CI: build/lint/typecheck/tests and test reports; staging E2E gates release.

## Rules

- Test real PostgreSQL behavior for database-integrated paths; do not substitute EF Core InMemory as proof of compatibility.
- No destructive tests against a production or shared database. Reset/seed only isolated test resources.
- Use deterministic fixtures and avoid brittle sleeps; Playwright waits for meaningful UI conditions.
- Mock **third-party systems**; keep the application's own API real in API integration and E2E tests.
- Treat accessibility and keyboard navigation as testable behavior for core UI.
- On a bug fix, write a regression test that would have caught the defect.

## Definition of done (risk-adjusted)

- [ ] Acceptance criteria satisfied and demonstrated.
- [ ] Code is focused, reviewed against existing conventions and documented where needed.
- [ ] Relevant tests added/updated and executed successfully (or unrun checks clearly identified).
- [ ] No sensitive data/secrets included.
- [ ] Database migration/release implications documented when applicable.
- [ ] Learning/progress log updated after meaningful milestones, not every tiny edit.

## Commands

**Do not assume these exist yet.** Once the repo is bootstrapped, record the actual working commands in `README.md` and let Codex use those, rather than guessing scripts or solution names.
