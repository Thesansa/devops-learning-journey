# Week 2 – Applying Docker to the SOS Project

## Objective

Apply Docker concepts to containerize the SOS Authentication module and create a consistent development environment using Docker Compose.

---

# Tasks Performed

## 1. Completed the Authentication Module

Implemented the first functional component of the SOS backend.

### Features

- User Registration
- User Login
- User Logout
- JWT Authentication
- Refresh Token Authentication
- Refresh Token Rotation

---

## 2. Containerized the Spring Boot Backend

Created a Dockerfile for the backend application.

The Dockerfile performs a multi-stage build:

- Uses Maven to compile the Spring Boot project.
- Packages the application into a JAR file.
- Creates a lightweight runtime image using JRE.
- Starts the application automatically when the container launches.

### Outcome

Successfully built a reusable Docker image for the SOS backend.

---

## 3. Containerized PostgreSQL

Docker Compose was configured to pull the official PostgreSQL image from Docker Hub.

### Outcome

- PostgreSQL now runs inside its own isolated container.
- No manual database installation is required.
- Database setup is reproducible on any machine.

---

## 4. Orchestrated Multiple Containers

A `docker-compose.yml` file was created to orchestrate both services.

### Services

- Backend
- PostgreSQL

Docker Compose automatically:

- Built the backend image from the Dockerfile.
- Pulled the PostgreSQL image from Docker Hub.
- Created a shared Docker network.
- Started the PostgreSQL container.
- Waited until PostgreSQL became healthy.
- Started the backend container.
- Injected environment variables into both containers.
- Connected both containers using Docker's internal networking.

### Communication Between Containers

The backend does **not** connect to:

```
localhost
```

Instead, it connects to

```
postgres:5432
```

where **postgres** is the service name defined in `docker-compose.yml`.

Docker automatically creates an internal DNS service that resolves the service name to the correct container.

This allows both containers to communicate without manually configuring IP addresses.

---

## 5. Persistent Database Storage

A named Docker volume was configured for PostgreSQL.

### Outcome

Database data remains available even if containers are stopped or recreated.

---

## Authentication Request Flow

```
User Login
        │
        ▼
Spring Boot Backend
        │
        ▼
Validate Credentials
        │
        ▼
Generate Access Token
Generate Refresh Token
        │
        ▼
Store Refresh Token (hashed) in PostgreSQL
        │
        ▼
Send Tokens to React
        │
        ▼
Access Token Expires
        │
        ▼
React receives 401 Unauthorized
        │
        ▼
Axios Interceptor automatically calls
POST /refresh
        │
        ▼
Backend validates Refresh Token
        │
        ▼
Issue New Access + Refresh Tokens
        │
        ▼
Retry Original Request
```

---

# DevOps Concepts Applied

This week's work applied several DevOps concepts directly to the SOS project.

- Docker image creation
- Multi-stage Docker builds
- Containerization
- Docker networking
- Docker Compose orchestration
- Persistent Docker volumes
- Environment variable injection
- Service dependency management
- Health checks
- Containerized database

---

# Challenges Encountered

### Java Version Mismatch

The project initially failed because the local machine was using JDK 25 while the project required JDK 21.

Using Docker ensured the application always runs with the correct Java version regardless of the host machine.

---

### Backend–Database Communication

The backend originally relied on localhost for database connectivity.

When containerized, localhost no longer referred to the PostgreSQL container.

The issue was resolved by using Docker Compose networking and connecting to:

```
jdbc:postgresql://postgres:5432/sos_db
```

where `postgres` is the Docker Compose service name.

---

# Weekly Outcome

By the end of Week 2:

- ✅ Authentication module completed.
- ✅ JWT authentication implemented.
- ✅ Refresh token workflow completed.
- ✅ Backend successfully containerized.
- ✅ PostgreSQL successfully containerized.
- ✅ Docker Compose orchestration configured.
- ✅ Backend and database communicating successfully inside Docker.
- ✅ Changes pushed to the GitHub repository.

---

# Reflection

This week was my first experience applying containerization to a real application.

Instead of running the backend and database separately on my local machine, Docker allowed both services to run in isolated containers while Docker Compose automatically managed how they were built, connected, configured, and started.

The biggest realization was understanding that Docker is not only about packaging an application—it is also about creating a consistent execution environment where multiple services can work together reliably.

Containerizing the authentication module also prepares the project for future Azure deployment because the same Docker image tested locally can be deployed without rebuilding or changing the application configuration.
