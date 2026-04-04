# Configuration

This repository keeps checked-in configuration safe by using placeholder values instead of real credentials.

## Backend

The backend reads the main SQL Server connection string from `ConnectionStrings:OlibDb`.

Example local setup:

```bash
export ConnectionStrings__OlibDb="Server=localhost;Database=olihdb;User Id=<set-me>;Password=<set-me>;TrustServerCertificate=True"
```

You can also keep a local-only override in `api/Olih.Api/appsettings.Development.json`, but real secrets should not be committed.

## Frontend

The current frontend setup does not require a checked-in secret file. Keep environment-specific overrides local to your machine or CI environment.

## Repository Rule

- Do not commit real passwords, tokens, or private connection strings
- Use environment variables for machine-specific values
- Keep checked-in `appsettings*.json` files safe to publish
