# Olih API

Backend API for the Olih solution.

## Stack

- ASP.NET Core
- Entity Framework Core
- SQL Server
- xUnit

## Working Directory

Run all backend commands from the `api` directory.

## Build and Run

```bash
dotnet restore
dotnet build olih.sln
dotnet run --project Olih.Api/Olih.Api.csproj
```

Swagger is enabled in the Development environment.

## Configuration

The checked-in connection string uses placeholder credentials.

Set the local database connection string before starting the API:

```bash
export ConnectionStrings__OlibDb="Server=localhost;Database=olihdb;User Id=<set-me>;Password=<set-me>;TrustServerCertificate=True"
```

Additional repository docs:

- [`../docs/architecture.md`](../docs/architecture.md)
- [`../docs/configuration.md`](../docs/configuration.md)

## Test

```bash
dotnet test olih.sln
```

## Project Layout

- `Olih.Api`: API host and controllers
- `Olih.Domain`: domain contracts, DTOs, request models, and response models
- `Olih.Infrastructure`: repositories, services, EF Core setup, and migrations
- `Olih.Common`: shared base types and utilities
- `Olih.XUnit`: backend tests

## Migrations

Create a migration:

```bash
dotnet ef -s Olih.Api/Olih.Api.csproj migrations add -c OlihDbContext Init -p Olih.Infrastructure/Olih.Infrastructure.csproj
```

Apply database changes:

```bash
dotnet ef database update -s Olih.Api/Olih.Api.csproj -c OlihDbContext -p Olih.Infrastructure/Olih.Infrastructure.csproj
```

## Notes

- The solution still uses the historical `Olih` naming convention.
- The API currently uses SQL Server through `OlihDbContext`.
- Real credentials should not be committed. Use environment variables or local-only overrides for development secrets.
