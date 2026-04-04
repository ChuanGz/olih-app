# Olih API

Backend API for the Olih solution.

## Working Directory

Run all backend commands from the `api` directory.

## Migrations

### Create a migration

```bash
dotnet ef -s Olih.Api/Olih.Api.csproj migrations add -c OlihDbContext Init -p Olih.Infrastructure/Olih.Infrastructure.csproj
```

- `-s`: startup project
- `-p`: persistence project
- `-c`: database context name

### Apply database changes

```bash
dotnet ef database update -s Olih.Api/Olih.Api.csproj -c OlihDbContext -p Olih.Infrastructure/Olih.Infrastructure.csproj
```
