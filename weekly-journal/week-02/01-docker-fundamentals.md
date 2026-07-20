# 🐳 Docker Fundamentals

## What is Docker?

Docker is an open-source containerization platform that packages an application together with everything it needs to run—including the runtime, dependencies, libraries, and operating system environment—into a portable unit called a **container**.

This allows applications to run consistently across different machines without requiring manual environment setup.

---

## The Problem Docker Solves

Without Docker, every developer or deployment environment must manually install and configure:

- Correct Java version
- Maven
- PostgreSQL
- Environment variables
- Application dependencies

Even a small mismatch (such as using JDK 25 instead of JDK 21) can prevent an application from running correctly. Docker solves the classic **"Works on My Machine"** problem by ensuring every environment is identical.

---

## Core Concepts

### Image

An **image** is a read-only blueprint containing everything required to run an application.

It includes:

- Base operating system
- Runtime (JRE)
- Application
- Dependencies
- Startup command

An image does not execute by itself. 

---

### Container

A **container** is a running instance of an image.

Multiple containers can be created from the same image, each running independently. 

---

## Containerization

Containerization is the process of packaging an application together with everything it needs into a portable container.

Docker is one implementation of containerization. Other container engines also exist, but Docker is the most widely used. 

---

## Docker Workflow

```
Source Code
      │
      ▼
Dockerfile
      │
      ▼
Docker Build
      │
      ▼
Docker Image
      │
      ▼
Docker Container
      │
      ▼
Running Application
```

---

## Dockerfile

A Dockerfile contains instructions for building a single Docker image.

In the SOS project, the Dockerfile:

- Uses Maven to build the application.
- Packages the Spring Boot JAR.
- Uses a lightweight JRE image.
- Starts the application automatically when the container launches. 

---

## Docker Compose

Docker Compose orchestrates multiple containers.

For the SOS project it:

- Pulls the PostgreSQL image.
- Builds the backend image.
- Creates a shared network.
- Injects environment variables.
- Starts services in the correct order.
- Keeps database data persistent using volumes. 

---

## Why Docker Matters for DevOps

Docker provides:

- Consistent environments
- Portable deployments
- Simplified dependency management
- Faster onboarding
- Easier cloud deployment
- Better collaboration between development and operations

---

# Applied to My SOS Project

This week I containerized the Spring Boot backend and orchestrated it together with PostgreSQL using Docker Compose.

The application can now run inside isolated containers with a consistent environment, making future Azure deployment significantly easier because the same tested image can be deployed without rebuilding or reconfiguring the application. 
