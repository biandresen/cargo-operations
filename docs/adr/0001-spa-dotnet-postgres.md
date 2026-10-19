# ADR 0001 — React SPA + ASP.NET Core API + PostgreSQL

- **Status:** Proposed; confirm once bootstrapped
- **Date:** 2026-10-20

## Context

The concept project models internal, authenticated cargo operations with interactive forms, tables and status updates. Search engine visibility is not a requirement. The learner knows JavaScript/TypeScript and PostgreSQL and wants hands-on C#/.NET experience, containerization and deployment practices.

## Decision

Start with a **React + TypeScript + Vite SPA**, a separately deployable **ASP.NET Core Web API (.NET 10)** and **PostgreSQL with Entity Framework Core/Npgsql**. Organize the API as a modular monolith, not multiple independent services. Use Docker Compose locally.

## Alternatives considered

- **Next.js / TanStack Start:** capable, but their server capabilities may duplicate a separately planned .NET backend; revisit if requirements justify them.
- **Express backend:** fastest path with existing skills, but provides less .NET learning value for this specific project.
- **SQL Server:** natural option in the .NET ecosystem, but PostgreSQL is suitable and already familiar.
- **Microservices:** extra deployment, network and consistency complexity without a demonstrated need.

## Consequences

- Frontend and backend need a documented API contract and coordinated compatibility changes.
- Choose routing, server-state and form libraries explicitly rather than assuming framework defaults.
- Server-side authentication, authorization, validation and migration management remain essential.
- Three environments can use the same architecture while maintaining separate secrets and databases.

## Review trigger

Revisit if actual business requirements demand SEO/SSR, different client platforms, a pre-existing integration standard, multi-team scalability or constrained hosting.
