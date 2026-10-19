# Product scope and acceptance criteria

> This document describes a **hypothetical learning project** and does not assert actual Air Cargo Logistics business requirements. All names and shipments are fictitious.

## Goal

Build a small internal web application where an operator can create, find and follow shipments and later view history, issues and integrations. Demonstrate end-to-end data flow and sound engineering decisions.

## Users (assumptions)

- **Operator:** records and updates shipments and operational events.
- **Viewer:** reads shipment information; cannot change it.
- **Admin:** manages permitted accounts/settings (later milestone).

Validate or refine these personas as the prototype evolves; they are not employer-provided roles.

## First vertical slice (P0)

1. A fictitious customer exists in the database.
2. An operator creates a shipment with a unique reference, customer, origin, destination, planned dates and positive weight.
3. API validates and persists the shipment through EF Core + PostgreSQL.
4. The operator sees the new shipment in a list and can open its details.
5. Data remains after refreshing the page and restarting the application containers (with persistent volume).

### Acceptance criteria (P0)

- [ ] Shipment creation succeeds with valid fields; UI gives a clear success state.
- [ ] Invalid input is rejected by backend with useful errors; frontend displays them.
- [ ] Shipment reference must be unique; missing customer and invalid weight are rejected.
- [ ] List and detail views handle loading, empty, not-found and server-error states.
- [ ] Database schema comes from a versioned EF Core migration.
- [ ] The end-to-end flow is manually verified and documented; automated integration, UI and E2E tests are added in the next quality milestone (P1).

## Next milestones (P1)

- Shipment status and audit/event history with valid transitions and timestamps.
- Issue/exception tracking, separate from shipment status.
- Role-based server-side authorization and mock external integration.
- CI, automated test layers, staging then isolated production demo.

## Out of scope until justified

- Real business/customer data or external production services.
- Full freight-booking processes, accounting, invoicing and regulatory declarations.
- Microservices, distributed messaging, Kubernetes and advanced real-time location tracking.

## Explicit open questions

- Which actual workflow would a real freight-forwarding operator prioritize?
- Which fields and status transitions are essential? Define them before implementing business rules.
- What deployment provider, identity solution and database hosting are suitable for this demo?
- Which staging/prod costs, access restrictions and rollback requirements are acceptable?

## Change discipline

For each feature: clarify user goal → acceptance criteria → API/data impact → tests → demonstration. Mark facts, assumptions and choices separately. Do not silently expand scope.
