# Identity - .NET Web API

## Introduction

Identity is an ASP.NET Core Web API developed as part of a Multi-Repository architecture.

The project represents an independent application repository responsible for identity-related services and demonstrates how multiple .NET applications can share reusable components through NuGet package management.

Identity consumes the Shared class library distributed through Azure DevOps Artifacts, demonstrating centralized dependency management across independent repositories.

## Project Architecture

Identity is one of three independent application repositories in this project:

| Repository | Responsibility |
|---|---|
| Shared | Reusable .NET Class Library |
| Basket | Basket Web API |
| Identity | Identity Web API |
| Order | Order Web API |

Each repository maintains its own solution, project structure, source code, Git history, and CI/CD pipeline.

## Technologies Used

- C#
- .NET 10
- ASP.NET Core Web API
- NuGet Package Management
- Azure DevOps Artifacts
- Azure DevOps Classic Pipelines
- Git and GitHub

## Repository Structure

```text
Identity/
│
├── src/
│   └── Identity/
│       ├── Controllers/
│       ├── Properties/
│       ├── Identity.csproj
│       ├── Identity.http
│       ├── Program.cs
│       ├── WeatherForecast.cs
│       ├── appsettings.json
│       └── appsettings.Development.json
│
├── .gitignore
├── Identity.slnx
└── README.md
```

## Shared NuGet Package Integration

Identity consumes the Shared library as a NuGet package instead of directly referencing its source project.

This approach provides:

- Reusable components across independent applications.
- Centralized package distribution.
- Independent version management.
- Reduced code duplication.
- Simplified dependency management.

The Shared package is published and distributed through the Azure DevOps Artifacts feed named `Shared-Feed`.

## Build and Run

Restore dependencies:

```bash
dotnet restore Identity.slnx
```

Build the solution:

```bash
dotnet build Identity.slnx
```

Run the application:

```bash
dotnet run --project src/Identity/Identity.csproj
```

## CI/CD Pipeline

The Identity repository is integrated with Azure DevOps Classic Pipelines.

The pipeline includes the following stages:

1. NuGet Restore
2. Build
3. Test
4. Pack
5. Push NuGet Package (where applicable)
6. Publish Build Artifact

These stages automate dependency restoration, application validation, and build artifact generation.

## Project Objectives

- Demonstrate independent repository management.
- Implement a multi-repository software architecture.
- Consume reusable NuGet packages from Azure DevOps Artifacts.
- Integrate GitHub with Azure DevOps workflows.
- Implement automated CI/CD pipelines.
- Maintain independent application development and version control.

---

**Note:** This repository is part of a personal learning and demonstration project using sample configurations and data.
