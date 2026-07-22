# ☁️ Azure PostgreSQL Fundamentals

## What is Azure Database for PostgreSQL?

Azure Database for PostgreSQL Flexible Server is a fully managed PostgreSQL database service provided by Microsoft Azure.

Instead of installing and maintaining PostgreSQL on a virtual machine, Azure manages the database infrastructure, including operating system updates, backups, monitoring, and high availability.

Applications simply connect to the database using its public endpoint and credentials.

---

# Why Use a Managed Database?

Compared to hosting PostgreSQL manually, Azure provides:

- Managed infrastructure
- Automatic backups
- Built-in monitoring
- Automatic patching
- High availability options
- Secure network access
- Easy scalability

This allows developers to focus on building applications rather than managing database servers.

---

# Deployment Workflow

The deployment process followed these major stages:

```
Azure Login
      │
      ▼
Create Resource Group
      │
      ▼
Verify Allowed Region
      │
      ▼
Register Required Resource Providers
      │
      ▼
Create PostgreSQL Flexible Server
      │
      ▼
Configure Firewall
      │
      ▼
Create Application Database
      │
      ▼
Verify Database Connectivity
      │
      ▼
Connect Spring Boot Application
      │
      ▼
Test Authentication APIs
      │
      ▼
Verify Data Stored in Azure
```

---

# Azure Concepts Learned

## Resource Group

A Resource Group is a logical container that holds related Azure resources.

For the SOS project, both the PostgreSQL server and future Azure resources are organized within the same resource group.

---

## Regions

Azure resources must be deployed into supported geographic regions.

Not every Azure subscription has access to every region.

Choosing an unsupported region prevents resource creation.

---

## Resource Providers

Azure services are enabled through Resource Providers.

Before creating PostgreSQL resources, the subscription had to register:

- Microsoft.DBforPostgreSQL

Additional providers registered for future use:

- Microsoft.Web
- Microsoft.ContainerRegistry

---

## Firewall Rules

Azure PostgreSQL blocks external connections by default.

A firewall rule was added to allow connections only from the current public IP address.

This secures the database while still allowing local development.

---

## Managed PostgreSQL

Unlike running PostgreSQL inside Docker, Azure hosts the database on managed infrastructure.

The application connects through:

```
Spring Boot

↓

Azure PostgreSQL Server

↓

sos_db
```

instead of

```
Spring Boot

↓

Docker PostgreSQL Container
```

---

# Connectivity Verification

Database connectivity was verified independently using the official PostgreSQL Docker image.

This confirmed that:

- Authentication credentials were correct.
- Firewall configuration was successful.
- Database server was reachable.
- SSL connection worked correctly.

---

# Connecting the Backend

The local Spring Boot application was configured using environment variables:

- Database URL
- Username
- Password

The backend then communicated directly with the Azure-hosted PostgreSQL database.

Authentication APIs were tested successfully through Postman.

---

# Lessons Learned

During deployment several common Azure issues were encountered:

### Region Restrictions

Some Azure regions were unavailable for the current subscription.

This required selecting a supported deployment region.

---

### Resource Provider Registration

Creating the PostgreSQL server initially failed because the required Azure Resource Provider had not yet been registered.

After registering the provider, resource creation succeeded.

---

### Firewall Configuration

The database remained inaccessible until the current public IP address was explicitly allowed through the Azure firewall.

---

### Cloud Connectivity

Successful API requests confirmed that the application was interacting with the Azure database rather than a local PostgreSQL instance.

---

# Cost Management

To avoid unnecessary charges, the PostgreSQL Flexible Server was stopped after testing completed.

Cloud resources should always be stopped or removed when they are no longer required during development.

---

# Key Takeaways

- Azure provides managed PostgreSQL infrastructure.
- Resource Groups organize related cloud resources.
- Resource Providers must be registered before certain Azure services can be created.
- Firewall rules control database access.
- Applications can connect to Azure PostgreSQL using standard JDBC connections.
- Cloud databases can replace locally hosted databases without changing application logic.
- Managed services reduce infrastructure management while maintaining application compatibility.

---

# Applied to My SOS Project

The SOS backend was successfully connected to Azure Database for PostgreSQL.

The complete authentication module (Register, Login, Refresh Token, Logout) was executed against the cloud-hosted database instead of the local Docker PostgreSQL container.

This represents the project's first successful migration from a fully local development environment to a cloud-hosted infrastructure component, providing the foundation for future Azure deployments and Continuous Deployment (CD).
