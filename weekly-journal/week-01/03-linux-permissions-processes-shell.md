# 🔐 Linux Permissions, Processes & Shell Basics

## Linux Permissions

### Why Linux Has Permissions

Linux is a multi-user operating system, meaning multiple users can access the same computer while protecting each user's files and system resources.

Every file and directory has permissions assigned to three categories of users.

| User Category | Description |
|--------------|-------------|
| Owner | The user who owns the file. |
| Group | A group of users who may share permissions. |
| Others | Everyone else who is neither the owner nor a member of the group. |

---

## Understanding Linux Permissions

Use:

```bash
ls -l
```

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
- rwx r-x r--
│ │   │   │
│ │   │   └── Others
│ │   └────── Group
│ └────────── Owner
└──────────── File type
```

- `-` → Regular file
- `d` → Directory

### Permission Types

| Permission | File | Directory |
|------------|------|-----------|
| Read (`r`) | Read the file contents | View files inside the directory |
| Write (`w`) | Edit the file | Create, rename, or delete files within the directory |
| Execute (`x`) | Run the file as a program or script | Enter the directory using `cd` |

---

## Changing Permissions

Linux permissions can be modified using the `chmod` command.

Examples:

```bash
chmod +x hello.sh
```

Add execute permission.

```bash
chmod -x hello.sh
```

Remove execute permission.

```bash
chmod u+x hello.sh
```

Give execute permission only to the owner.

---

## User Symbols

| Symbol | Meaning |
|--------|---------|
| `u` | User (Owner) |
| `g` | Group |
| `o` | Others |
| `a` | All users |

---

## sudo

`sudo` temporarily grants administrator (root) privileges.

It is commonly used for:

- Installing software
- Updating packages
- Restarting services
- Editing protected system files

It should not be used to bypass permissions on your own files.

---

# Processes & Shell Basics

## What is a Process?

A process is a program that is currently running.

Example:

```
VS Code
↓

Running

↓

Process
```

---

## Terminal vs Shell

### Terminal

The application where commands are entered.

Examples:

- Ubuntu Terminal
- Windows Terminal

### Shell

The command interpreter that communicates with the operating system.

In Ubuntu, the default shell is **Bash (Bourne Again Shell)**.

```
User
↓

Terminal

↓

Bash

↓

Linux Kernel

↓

Hardware
```

---

## Process Monitoring

Linux provides commands to monitor running processes.

| Command | Purpose |
|---------|---------|
| `ps` | Display processes running in the current terminal session |
| `top` | Continuously monitor CPU, memory, and running processes |
| `history` | Display previously executed commands |

---

## DevOps Connection

Linux permissions are essential in modern DevOps environments.

| Linux Concept | DevOps Application |
|-------------------------------|------------------------------------------------|
| Execute Permission (`chmod +x`) | Running deployment or startup scripts |
| File Permissions | Reading configuration files and writing logs |
| `sudo` | Installing software and restarting services |
| Users & Groups | Running applications with limited privileges |
| Permissions | Preventing unauthorized access and improving security |

---

## Applied to My SOS Project

Understanding Linux permissions prepares me to deploy my Personal Safety Emergency Alert System securely.

These concepts will later be applied when:

- Running deployment scripts.
- Executing Docker container startup scripts.
- Managing application configuration files.
- Deploying the application on Linux cloud servers.
- Securing the application using appropriate user permissions instead of running everything as the root user.
