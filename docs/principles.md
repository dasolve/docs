---
sidebar_position: 3
---

# Principles

The framework principles will be split in some sections to make it easier to read and understand:

- Development Environment
- Developer Experience
- Frontend
- Backend
- Data
- Infrastructure

Those principles set simple architectural decisions to be followed by developers and LLMs working with the Dasolve Framework to build their solutions. The framework will do its best to enforce those principles, but it is up to the developer to follow them and keep the codebase aligned with them. If developers don't follow those principles, the framework will not be able to help them in the long run of the development process.

The principles listed here are not exhaustive. More principles will be added over time as the framework evolves and new best practices are discovered. The goal is to keep the principles simple and easy to follow, while still providing a solid foundation for building data-driven solutions with enough guardrails to avoid several pitfalls.

## Development Environment

[ADR-001](./adrs/ADR-001.md) - The primary programming language for Dasolve is TypeScript. It will be used in all parts of the framework.

[ADR-002](./adrs/ADR-002.md) - For data-related tasks (Jobs and Machine Learning functions), Python will be used as the primary programming language.

[ADR-003](./adrs/ADR-003.md) - The package manager for Javascript/Typescript packages is Bun.

[ADR-004](./adrs/ADR-004.md) - The package manager for Python packages is uv.

[ADR-005](./adrs/ADR-005.md) - The primary runtime for Typescript is Bun.

[ADR-006](./adrs/ADR-006.md) - Node.JS may be used for tools that don't support Bun yet, like Storybook or Docusaurus.

[ADR-007](./adrs/ADR-007.md) - The supported Operating Systems are MacOS and Linux. Windows developers must use WSL for development.

[ADR-008](./adrs/ADR-008.md) - The toolchain management will be done with proto.

## Developer Experience

[ADR-009](./adrs/ADR-009.md) - VSCode and its forks is the IDE for Dasolve solution development.

[ADR-010](./adrs/ADR-010.md) - Moonrepo is the monorepo tool (task runner and orchestrator) for Dasolve solutions development.

[ADR-011](./adrs/ADR-011.md) - Linting will be enforced in the repository. Typescript code will be linted with oxlint. Python code will be linted with ruff.

[ADR-012](./adrs/ADR-012.md) - Formatting will be enforced in the repository. Typescript code will be formatted with Prettier. Python code will be formatted with ruff.

[ADR-013](./adrs/ADR-013.md) - Dasolve solutions must follow a specific folder structure

[ADR-026](./adrs/ADR-026.md) - Typescript code should not use path aliases. All imports must be relative or use package names.

## Frontend

[ADR-014](./adrs/ADR-014.md) - Frontends will follow the SPA (Single Page Application) architecture.

[ADR-015](./adrs/ADR-015.md) - Frontends must use React.JS as the framework.

[ADR-016](./adrs/ADR-016.md) - Frontends will be built with Vite.

[ADR-017](./adrs/ADR-017.md) - Frontends will use TanStack Router as the routing library.

[ADR-017](./adrs/ADR-017.md) - File routing in a folder tree structure will be used to define the routes in the application.

[ADR-018](./adrs/ADR-018.md) - Frontends will use TanStack Query for data fetching and caching.

[ADR-019](./adrs/ADR-019.md) - Frontends will use MUI as the base UI library. The look and feel of it will be customizeable.

[ADR-020](./adrs/ADR-020.md) - Frontends will use Jotai for internal global state management.

[ADR-021](./adrs/ADR-021.md) - Frontends will use CSS modules for any extra styling required.

[ADR-022](./adrs/ADR-022.md) - Frontends will support Azure AD authentication.

[ADR-023](./adrs/ADR-023.md) - Frontend components will be developed and tested in isolation by using Storybook.

[ADR-024](./adrs/ADR-024.md) - Stateful (connected) components and stateless (presentational) components must be separated. Connected components must have "Connected" in its component name. Stateless components must not have any hooks. Helper functions must be unit tested.

[ADR-025](./adrs/ADR-025.md) - Frontends must support end-to-end type safety with the backend.

3.13. Frontends should not wrangle data on the client. All data wrangling should be done on the backend or in data jobs.

## 4. Backend

4.1. Backends will follow the Backend for Frontend (BFF) architecture.

4.2. Backends will use Hono as the framework.

4.3. Backends must have end-to-end type safety with the frontend (Hono RPC).

4.4. Backends must support CORS.

4.5. Backends must be fully documented with OpenAPI specs.

4.6. Backends must support authentication and authorization with Azure AD.

4.6.1. Backends must be able to handle the tokens forwarded from the frontend and validate them.

4.6.2. Backends must support authorization based on role claims in the validated token.

4.7. Backends must support rate limiting to prevent abuse.

4.8. Backends must support error monitoring with Sentry.

## 5. Data

5.1. Data models will be defined using Dasolve DB DDL, which is a YAML-based DSL.

5.2. Changes to data models will be tracked by schema migrations.

5.3. Data models should only contain the necessary fields for the application.

5.3.1. Data models should not contain data that is not used in the application.

5.4. Data models will be deployed in PostgreSQL servers.

5.5. Each data model will have a corresponding schema in the database.

5.6. Data models will be accessed from backends using Drizzle ORM.

5.7. Data models will be accessed from data jobs and other python code using SQLModel ORM.

5.8. Data jobs for filling up or updating data on the data models shall be triggered by events coming from the frontend and its real usage.

5.8.1. Data jobs must be idempotent and able to handle retries gracefully.

5.8.2. Data jobs should not be triggered by cron jobs or scheduled tasks, but rather by user actions or events in the system.

5.9. Data jobs must be able to run in parallel and scale horizontally.

5.10. Measured values should be stored in the database in the SI (International System of Units) unit without loss of precision.

5.11. Time Series data should be stored using the right storage method in the database via using TimescaleDB.
