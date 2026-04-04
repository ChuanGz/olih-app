# Olih App

Olih App is a monorepo for a .NET backend API and a React web client. The repository combines the previously split API and frontend projects into a single workspace with a flatter, easier-to-navigate structure.

## Tech Stack

- Backend: ASP.NET Core, Entity Framework Core, SQL Server
- Frontend: React, TypeScript, Ant Design, Create React App
- Testing: xUnit for backend tests

## Repository Layout

- `api`: .NET solution, domain model, infrastructure, and tests
- `web`: React web client and local mock data
- `docs`: project notes and supporting documentation

## Prerequisites

- .NET 8 SDK
- Node.js and npm
- SQL Server for local API development

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

## Frontend Development

The frontend lives in `web` and uses a standard React setup with TypeScript. The current project still uses the historical package name `olih-demo`, but it is now maintained as part of this unified repository.

## Notes

- The codebase still uses the `Olih` prefix internally.
- This repository replaces the previous split setup of `qna-app-api` and `qna-app-reactjs`.
