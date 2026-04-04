# Olih App

Olih App is a unified workspace for the Olih backend API and React web client.

## Repository Layout

- `api`: .NET backend solution, application code, infrastructure, and tests
- `web`: React web client and local mock data
- `docs`: project notes and supporting documentation

## Run the API

```bash
cd api
dotnet build olih.sln
dotnet run --project Olih.Api/Olih.Api.csproj
```

## Run the Web App

```bash
cd web
npm install
npm start
```

## Notes

- The codebase still uses the `Olih` prefix internally.
- This repository replaces the previous split setup of `qna-app-api` and `qna-app-reactjs`.
