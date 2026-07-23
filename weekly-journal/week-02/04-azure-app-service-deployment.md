# ☁️ Azure App Service Deployment

## What is Azure App Service?

Azure App Service is a fully managed Platform as a Service (PaaS) offering that allows developers to deploy and host web applications without managing servers or operating systems.

For containerized applications, Azure App Service can pull Docker images directly from a container registry and run them as web applications.

In this project, the Spring Boot backend is hosted using Azure App Service while the Docker image is stored in GitHub Container Registry (GHCR).

---

# Deployment Architecture

The deployed backend follows this architecture:

```
GitHub Repository
        │
        ▼
GitHub Container Registry (GHCR)
        │
        ▼
Azure App Service
        │
        ▼
Spring Boot Container
        │
        ▼
Azure Database for PostgreSQL
```

The Docker image is built locally, pushed to GHCR, and Azure App Service automatically pulls the image from the registry.

---

# Why GitHub Container Registry?

Initially, Azure Container Registry (ACR) was considered.

However:

- Azure Container Registry does not provide a free tier.
- Maintaining an ACR instance would continuously consume Azure student credits.

Instead, GitHub Container Registry (GHCR) was selected because:

- Free for this project scale.
- Integrated with the existing GitHub repository.
- Fully compatible with Azure App Service.
- Eliminates unnecessary Azure infrastructure costs.

---

# Azure Components Used

## Azure App Service Plan

The App Service Plan defines the compute resources used by the web application.

Configuration:

- Linux
- Free (F1) tier

---

## Azure Web App

A Linux Web App was created to host the backend container.

The application receives HTTP requests and runs the Spring Boot application inside the Docker container.

---

## GitHub Container Registry (GHCR)

The backend Docker image is stored securely inside GitHub Container Registry.

Azure App Service authenticates using a GitHub Personal Access Token (PAT) and pulls the private container image automatically.

---

## Azure App Settings

Application configuration is stored securely using Azure App Settings.

Configured values include:

- Database URL
- Database Username
- Database Password
- JWT Secret
- Container Port

This keeps sensitive information outside the Docker image.

---

# Deployment Workflow

The deployment process followed these stages:

```
Build Docker Image
        │
        ▼
Push Image to GitHub Container Registry
        │
        ▼
Create Azure App Service Plan
        │
        ▼
Create Azure Web App
        │
        ▼
Configure Container Registry Authentication
        │
        ▼
Configure Environment Variables
        │
        ▼
Azure Pulls Docker Image
        │
        ▼
Spring Boot Starts
        │
        ▼
Application Available on the Internet
```

---

# Authentication Between Azure and GHCR

Since the Docker image is private, Azure App Service requires authentication.

Authentication is performed using:

- GitHub Username
- GitHub Personal Access Token (PAT)

Azure uses these credentials to pull the latest container image directly from GitHub Container Registry.

---

# Environment Variables

Instead of storing secrets inside the Docker image, Azure App Settings injects configuration values at runtime.

Examples include:

- `SPRING_DATASOURCE_URL`
- `SPRING_DATASOURCE_USERNAME`
- `SPRING_DATASOURCE_PASSWORD`
- `JWT_SECRET`
- `WEBSITES_PORT`

Spring Boot automatically reads these values using its environment variable configuration.

---

# Challenges Encountered

## Container Registry Selection

Initially considered Azure Container Registry.

After evaluating pricing and project requirements, GitHub Container Registry was selected as a more cost-effective solution.

---

## GitHub Authentication

The first GitHub Personal Access Token did not contain the required package permissions.

A new token with the correct scopes was generated.

---

## Secret Exposure

A GitHub Personal Access Token was accidentally exposed during configuration.

The token was immediately revoked and replaced with a newly generated token before continuing deployment.

This reinforced the importance of rotating credentials immediately after accidental exposure.

---

## Container Port

Azure App Service assumes applications listen on port 80 by default.

Since the Spring Boot container exposes port 8080, the `WEBSITES_PORT` application setting was configured accordingly.

---

# Deployment Verification

Deployment was verified by:

- Registering a user through the deployed backend.
- Receiving valid JWT access and refresh tokens.
- Confirming the user record was successfully stored in Azure PostgreSQL.

This verified that:

- Azure App Service
- Spring Boot
- Azure PostgreSQL

were communicating successfully.

---

# Cost Management

To minimize Azure credit usage:

- Azure PostgreSQL Flexible Server was stopped after testing.
- Azure App Service remained running because the Free (F1) tier does not incur additional charges.

---

# Key Takeaways

- Azure App Service can host Docker containers directly.
- GitHub Container Registry can replace Azure Container Registry for small projects.
- Private container registries require authentication.
- Environment variables should be managed through Azure App Settings rather than hardcoded into Docker images.
- Cloud deployment consists of multiple independent services working together.
- Proper secret management is essential during deployment.

---

# Applied to My SOS Project

The SOS authentication backend was successfully deployed to Azure App Service using a Docker image stored in GitHub Container Registry.

The deployed application communicates with Azure Database for PostgreSQL using environment variables managed through Azure App Settings.

The complete authentication workflow (Register, Login, Refresh Token, Logout) is now accessible through a publicly hosted backend, representing the project's first successful cloud deployment of a containerized application.
