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

Those principles set simple rules to be followed by developers working with Dasolve. The framework will do its best to enforce those principles, but it is up to the developer to follow them and keep the codebase aligned with them. If developers don't follow those principles, the framework will not be able to help them in the long run of the development process.

The principles listed here are not exhaustive. More principles will be added over time as the framework evolves and new best practices are discovered. The goal is to keep the principles simple and easy to follow, while still providing a solid foundation for building data-driven solutions.

## 1. Development Environment

1.1. The primary programming language for Dasolve is TypeScript. It will be used in all parts of the framework.

1.2. For data-related tasks (Jobs and Machine Learning functions), Python will be used as the primary programming language.

1.3. The package manager for Javascript/Typescript packages is Bun.

1.4. The package manager for Python packages is uv

1.5. The primary runtime for Typescript is Bun.

1.5.1. Node.JS may be used for tools that don't support Bun yet, like Storybook or Docusaurus.

1.6. The supported Operating Systems are MacOS and Linux. Windows developers must use WSL for development.

## 2. Developer Experience

2.1. VSCode is the IDE for Dasolve development.

2.2. Moonrepo is the monorepo tool for Dasolve development.

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

3.11.1. Connected components must have Connected in its component name.

3.11.2. Stateless components must not have any hooks.

3.11. Helper functions must be unit tested.

3.12. Frontends must support end-to-end type safety with the backend.

## 4. Backend

4.1. Backends will follow the Backend for Frontend (BFF) architecture.

4.2. Backends will use Hono as the framework.

4.3. Backends must have end-to-end type safety with the frontend.

4.4. Backends must support CORS.

4.5. Backends must be fully documented with OpenAPI specs.

4.6. Backends must support authentication and authorization with Azure AD.

4.6.1. Backends must be able to handle the tokens forwarded from the frontend and validate them.

4.6.2. Backends must support authorization based on role claims in the validated token.
