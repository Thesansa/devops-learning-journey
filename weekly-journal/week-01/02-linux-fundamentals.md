# 🐧 Linux Fundamentals

---

# What is Linux?

Linux is an open-source operating system (OS) that manages computer hardware and software resources while providing a stable environment for applications to run.

Unlike Windows or macOS, Linux is open-source, meaning anyone can view, modify, and distribute its source code.

---

# Why Do DevOps Engineers Need Linux?

We are not learning Linux simply because it is "part of DevOps."

We learn Linux because most modern software infrastructure runs on Linux.

Linux is the operating system behind:

- Cloud servers (Microsoft Azure, AWS, Google Cloud)
- Docker containers
- Kubernetes clusters
- CI/CD servers
- Web servers
- Databases

Understanding Linux allows DevOps engineers to deploy, manage, troubleshoot, and automate applications in production environments.

---

# Linux Distributions

A Linux distribution (distro) is a version of Linux packaged with different software and tools.

Some popular distributions include:

- Ubuntu
- Debian
- Fedora
- CentOS
- Red Hat Enterprise Linux (RHEL)

For this learning journey, Ubuntu is used through Windows Subsystem for Linux (WSL).

---

# Linux File System

Linux organizes files in a hierarchical structure starting from the **Root Directory**.

```
/
├── home
│   └── semali_perera
├── etc
├── var
├── usr
└── tmp
```

Unlike Windows, Linux does not use drive letters such as **C:** or **D:**.

Everything starts from the root directory (`/`).

---

# Home Directory

Each Linux user has a personal home directory.

Example:

```
/home/semali_perera
```

The shortcut for the home directory is:

```
~
```

Both represent the same location.

---

# Terminal

The terminal is a command-line interface (CLI) used to communicate directly with the operating system.

Instead of clicking buttons, users type commands to perform tasks.

Most DevOps work is performed through the terminal because production servers often do not have a graphical interface.

---

# Bash

Bash (Bourne Again SHell) is the default shell used by many Linux distributions.

A shell acts as an interpreter between the user and the operating system.

It receives commands from the user and instructs the operating system to perform them.

Example:

```bash
pwd
```

Bash interprets the command and returns the current working directory.

---

# Understanding Paths

## Absolute Path

An absolute path starts from the root directory (`/`).

Example:

```bash
/home/semali_perera/Documents/LinuxPractice
```

Absolute paths always point to the same location regardless of the current directory.

---

## Relative Path

A relative path starts from the current working directory.

Example:

```bash
cd Documents
```

Relative paths depend on your current location.

---

# Navigation Concepts

## Current Directory

Your current location in the Linux file system.

Use:

```bash
pwd
```

to display it.

---

## Parent Directory

The directory immediately above the current directory.

Move to it using:

```bash
cd ..
```

---

## Root Directory

The highest level of the Linux file system.

Represented by:

```
/
```

Navigate to it using:

```bash
cd /
```

---

# Practical Commands Learned

Today's commands:

- pwd
- ls
- mkdir
- cd
- touch
- cd ..
- cd ~
- cd /
- explorer.exe .

---

# DevOps Connection

Everything practiced today directly applies to managing Linux servers used in DevOps.

These commands are commonly used when:

- Connecting to cloud servers
- Deploying applications
- Managing Docker containers
- Navigating project directories
- Editing configuration files
- Troubleshooting production systems

---

# Key Takeaways

- Linux powers most modern cloud infrastructure.
- DevOps engineers primarily interact with Linux through the terminal.
- Understanding the Linux file system is essential before learning Docker, Kubernetes, and cloud deployment.
- Navigation commands form the foundation for all future Linux administration tasks.

# 🔗 Applied to My SOS Project

Learning Linux provides the foundation for managing the environment where my Personal Safety Emergency Alert System (SOS) will eventually run.

As the project progresses, Linux will be used to:

- Host the application on a cloud-based Linux server.
- Navigate project files and manage the application through the terminal.
- Configure the runtime environment required by the backend and frontend.
- Execute build and deployment commands.
- Run Docker containers that package the application.
- Monitor logs and troubleshoot issues when the application is deployed.
- Manage files, directories, and server configurations without relying on a graphical interface.

Although the application is currently in the planning and early development stages, understanding Linux prepares me for the deployment, automation, and operational phases of the DevOps lifecycle.

Linux is not used to develop the application's features directly. Instead, it provides the operating environment where the application will be built, deployed, monitored, and maintained.
