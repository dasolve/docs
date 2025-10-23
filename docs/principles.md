---
sidebar_position: 2
---

# Principles

The framework principles will be split in some sections to make it easier to read and understand:

- Development Environment
- Developer Experience
- Frontend
- Backend
- Data
- Infrastructure

Those principles set simple rules to be followed by developers and LLMs working with the Dasolve Framework. The framework will do its best to enforce those principles, but it is up to the developer to follow them and keep the codebase aligned with them. If developers don't follow those principles, the framework will not be able to help them in the long run of the development process.

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

2.2. Moonrepo is the monorepo tool (task runner and orchestrator) for Dasolve solutions development.

2.3. Linting will be enforced in the repository.

2.3.1. Typescript code will be linted with oxlint and ESLint.

2.3.2. Python code will be linted with ruff.

2.4. Formatting will be enforced in the repository.

2.4.1. Typescript code will be formatted with Prettier.

2.4.2. Python code will be formatted with ruff.

## 3. Frontend

3.1. Frontends will follow the SPA (Single Page Application) architecture.

3.2. Frontends must use React.JS as the framework.

3.3. Frontends will be built with Vite.

3.4. Frontends will use TanStack Router as the routing library.

3.4.1. File routing in a folder tree structure will be used to define the routes in the application.

3.5. Frontends will use TanStack Query for data fetching and caching.

3.6. Frontends will use MUI as the base UI library. The look and feel of it will be customizeable.

3.7. Frontends will use Jotai for internal global state management.

3.8. Frontends will use CSS modules for any extra styling required.

3.9. Frontends will support Azure AD authentication.

3.10. Frontend components will be developed and tested in isolation by using Storybook.

3.11. Stateful (connected) components and stateless (presentational) components must be separated

3.11.1. Connected components must have "Connected" in its component name.

3.11.2. Stateless components must not have any hooks.

3.11. Helper functions must be unit tested.

3.12. Frontends must support end-to-end type safety with the backend.

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
