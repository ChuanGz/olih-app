# Architecture

Olih App is a simple two-part application:

- `api`: a .NET backend that exposes application endpoints, domain models, and persistence logic
- `web`: a React client that consumes the backend and provides the user-facing workflow

## Backend Shape

The backend is split into a few clear projects:

- `Olih.Api`: the ASP.NET Core host, controllers, and startup configuration
- `Olih.Domain`: DTOs, request models, response models, and domain contracts
- `Olih.Infrastructure`: repositories, data access, services, and EF Core migrations
- `Olih.Common`: shared primitives and common helpers
- `Olih.XUnit`: backend tests

## Frontend Shape

The frontend is a React application with TypeScript and Ant Design. It currently keeps the historical package name `olih-demo`, but it is maintained as the `web` application inside this repository.

## Current Boundaries

- Backend code and database concerns stay under `api`
- Browser UI and local client-side behavior stay under `web`
- Shared repository documentation stays under `docs`

This structure is intentionally flat so the repository is easy to scan and maintain.
