# Olih App

Olih App is a monorepo for a .NET backend API and a React web client. The repository combines the previously split API and frontend projects into a single workspace with a flatter, easier-to-navigate structure.

## Highlights

- Single repository for the backend API and web client
- .NET solution organized around API, domain, infrastructure, and tests
- React frontend with TypeScript and Ant Design
- EF Core migrations included in the backend project

## Tech Stack

- Backend: ASP.NET Core, Entity Framework Core, SQL Server
- Frontend: React, TypeScript, Ant Design, Create React App
- Testing: xUnit for backend tests

## Repository Layout

- `api`: .NET solution, domain model, infrastructure, and tests
- `web`: React web client and local mock data
- `docs`: project notes and supporting documentation

## Documentation

- [`docs/architecture.md`](docs/architecture.md)
- [`docs/configuration.md`](docs/configuration.md)

## Architecture Snapshot

```text
.
├── api
│   ├── Olih.Api
│   ├── Olih.Domain
│   ├── Olih.Infrastructure
│   ├── Olih.Common
│   └── Olih.XUnit
├── web
│   ├── src
│   ├── public
│   └── package.json
└── docs
```

## Prerequisites

- .NET 8 SDK
- Node.js and npm
- SQL Server for local API development

## Configuration

The backend connection string in `api/Olih.Api/appsettings*.json` is intentionally checked in with placeholder credentials.

Set a real local connection string before starting the API:

```bash
export ConnectionStrings__OlibDb="Server=localhost;Database=olihdb;User Id=<set-me>;Password=<set-me>;TrustServerCertificate=True"
```

You can also update your local `appsettings.Development.json` if that better matches your development workflow.

## Quick Start

### Run the API

```bash
cd api
dotnet restore
dotnet build olih.sln
dotnet run --project Olih.Api/Olih.Api.csproj
```

The API enables Swagger in the Development environment.

### Run the Web App

```bash
cd web
npm install
npm start
```

## Development Workflow

1. Start the API from `api`.
2. Start the web client from `web`.
3. Apply EF Core migrations when the database model changes.
4. Run backend tests before pushing changes.

## Backend Development

The backend solution is organized into the following projects:

- `Olih.Api`: API host and controllers
- `Olih.Domain`: domain contracts, DTOs, request models, and response models
- `Olih.Infrastructure`: data access, services, repositories, and EF Core migrations
- `Olih.Common`: shared base types and utilities
- `Olih.XUnit`: backend tests

## Database Migrations

Create a migration from the `api` directory:

```bash
dotnet ef -s Olih.Api/Olih.Api.csproj migrations add -c OlihDbContext Init -p Olih.Infrastructure/Olih.Infrastructure.csproj
```

Apply database changes:

```bash
dotnet ef database update -s Olih.Api/Olih.Api.csproj -c OlihDbContext -p Olih.Infrastructure/Olih.Infrastructure.csproj
```

Run backend tests:

```bash
cd api
dotnet test olih.sln
```

## Frontend Development

The frontend lives in `web` and uses a standard React setup with TypeScript. The current project still uses the historical package name `olih-demo`, but it is now maintained as part of this unified repository.

## Notes

- The codebase still uses the `Olih` prefix internally.
- This repository replaces the previous split setup of `qna-app-api` and `qna-app-reactjs`.
- Checked-in configuration files use placeholder credentials only. Real secrets should be provided through local environment variables or local-only config overrides.

## Usage Policy

- This repository is shared for learning, technical review, and knowledge sharing.
- No permission is granted to copy, reuse, modify, redistribute, sublicense, sell, deploy, or use this code in another repository, product, service, or internal system without prior written approval from the repository owner.
- See [LICENSE](LICENSE), [NOTICE.md](NOTICE.md), [DISCLAIMER.md](DISCLAIMER.md), [CONTRIBUTING.md](CONTRIBUTING.md), and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
