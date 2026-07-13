# 💻 Week 01 Command Cheat Sheet

---

# 🐧 Linux Commands

## Navigation

| Command | Description |
|---------|-------------|
| `pwd` | Print the current working directory. |
| `ls` | List files and folders in the current directory. |
| `cd <directory>` | Change the current directory. |
| `cd ..` | Move to the parent directory (one level up). |
| `cd ~` | Return to the user's home directory. |
| `cd /` | Move directly to the root directory. |

---

## Directory Management

| Command | Description |
|---------|-------------|
| `mkdir <directory>` | Create a new directory (folder). |

Example:

```bash
mkdir DevOpsPractice
```

Create a directory using an absolute path:

```bash
mkdir /home/semali_perera/Documents/LinuxPractice
```

---

## File Management

| Command | Description |
|---------|-------------|
| `touch <file>` | Create an empty file. |

Example:

```bash
touch hello.txt
```

Create multiple files:

```bash
touch notes.txt commands.txt practice.txt
```

---

## Windows Integration (WSL)

| Command | Description |
|---------|-------------|
| `explorer.exe .` | Open the current Linux directory in Windows File Explorer. |

---

## Helpful Tips

| Symbol | Meaning |
|--------|---------|
| `.` | Current directory |
| `..` | Parent directory |
| `~` | Home directory |
| `/` | Root directory |

---

## Frequently Used Commands

```bash
pwd
ls
cd
mkdir
touch
```

Whenever you feel lost in the terminal, run:

```bash
pwd
ls
```

These commands answer:

- 📍 Where am I?
- 📂 What files and folders are here?


## File Management

| Command | Description |
|---------|-------------|
| `cp <source> <destination>` | Copy a file |
| `mv <source> <destination>` | Move or rename a file |
| `rm <file>` | Delete a file |
| `rmdir <directory>` | Delete an empty directory |
| `rm -r <directory>` | Delete a directory and everything inside it |
| `cat <file>` | Display the contents of a file |
| `clear` | Clear the terminal screen |

---

## Output Redirection

```bash
echo "Hello DevOps!" > hello.txt
```

- `echo` → Prints text.
- `>` → Redirects the output into a file.
