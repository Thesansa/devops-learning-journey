## Day 2 - started Linux fundamentals

- Installed WSL.
- Installed Ubuntu.
- Created first Linux directory.
- Navigated directories using the terminal.
- Created first file.

## Linux File Management

### Objective

Practice Linux file management and navigation using the command line.

---

### Activities Performed

- Created directories and files.
- Navigated between directories.
- Copied files using `cp`.
- Renamed files using `mv`.
- Moved files into another directory.
- Deleted files using `rm`.
- Removed an empty directory using `rmdir`.
- Displayed file contents using `cat`.
- Printed text into a file using `echo`.
- Cleared the terminal using `clear`.

---

### Commands Executed

```bash
cd ~/DevOpsPractice
pwd
ls
cp notes.txt backup.txt
mv backup.txt backup_notes.txt
mkdir backups
mv backup_notes.txt backups/
ls backups
rm backups/backup_notes.txt
rmdir backups
echo "Hello DevOps!" > hello.txt
cat hello.txt
clear
```

---

### Outcome

Successfully performed Linux file management operations using the terminal and gained practical experience navigating, creating, copying, moving, renaming, deleting, and viewing files and directories.

### Skills Acquired

- Linux terminal navigation
- Linux file management
- Understanding the Linux filesystem
- Basic command-line workflow
- Connecting Linux concepts to DevOps practices

  

# Day 3 – Linux Command Pipelines & Log Analysis(Additional Linux Exploration)

## Objective

Learn how Linux commands can be combined using pipelines to search, filter, analyze, and process files efficiently. These techniques are commonly used by DevOps engineers when troubleshooting servers and analyzing application logs.

---

## New Commands Learned

### 1. List Files Recursively

```bash
ls -R
```

Displays all files and directories recursively from the current directory.

Useful for viewing an entire project structure.

---

### 2. Find Directories

```bash
find . -type d
```

Searches for all directories starting from the current directory (`.`).

- `.` → Current directory
- `-type d` → Search only for directories

---

### 3. Find Files

```bash
find . -type f
```

Searches for all files from the current directory.

---

### 4. Find Files by Extension

```bash
find . -type f -name "*.txt"
```

Finds every file ending with the `.txt` extension.

Unlike `ls`, this command returns the full file path.

---

### 5. Find a Specific File

```bash
find . -type f -name "app.txt"
```

Searches for a file named `app.txt`.

---

## Pipelines (`|`)

The pipe operator (`|`) sends the output of one command as the input to another command.

General syntax:

```bash
command1 | command2
```

Example:

```bash
ls -R | grep "app.txt"
```

- `ls -R` lists all files recursively.
- `grep` filters the output and displays only lines containing `app.txt`.

---

## Reading File Contents

```bash
find . -type f -name "app.txt" | xargs cat
```

Explanation:

1. Find every file named `app.txt`.
2. Pass the file names to `xargs`.
3. `cat` prints the contents of each file.

This is useful when multiple files share the same name in different directories.

---

## Searching Log Files

```bash
find . -type f -name "*.txt" | xargs cat | grep "ERROR"
```

Workflow:

1. Find all `.txt` files.
2. Print their contents.
3. Display only lines containing the word `ERROR`.

This simulates searching application log files for error messages.

---

## Sorting Results

```bash
find . -type f -name "*.txt" | xargs cat | grep "ERROR" | sort -k4
```

Sorts the filtered output using the fourth column.

> **Note:** The column number depends on the log format.

Example log:

```
2026-07-15 10:20:05 ERROR Database connection failed
```

Column 4 is:

```
Database
```

---

## Remove Duplicate Records

```bash
find . -type f -name "*.txt" | xargs cat | grep "ERROR" | sort -k4 | uniq -f3
```

`uniq -f3`

ignores the first three fields before comparing lines.

Useful when timestamps are different but the actual error message is identical.

---

## Output Redirection

Write output into a file.

```bash
find . -type f -name "*.txt" | xargs cat | grep "ERROR" > errors.log
```

If `errors.log` does not exist, Linux creates it.

If it already exists, its contents are overwritten.

---

## Append Output

```bash
find . -type f -name "*.txt" | xargs cat | grep "ERROR" >> errors.log
```

`>>`

Appends new output to the end of the file instead of replacing existing content.

---

## Difference Between `|` and `>`

### Pipe (`|`)

Passes the output of one command directly into another command.

```
Command A
        │
        ▼
Command B
```

---

### Redirection (`>`)

Writes the output into a file.

```
Command

↓

output.txt
```

---

## Execute a Command for Each File

```bash
find . -type f -name "*.txt" -exec rsync -R {} /backup \;
```

Explanation:

- `find` searches for matching files.
- `-exec` executes another command for each result.
- `{}` represents the current file found.
- `rsync -R` preserves the relative directory structure while copying.
- `\;` tells `find` where the command ends.

This is commonly used for backing up files while preserving their folder hierarchy.

---

## Practical DevOps Application

These commands are useful when:

- Searching server log files.
- Monitoring application errors.
- Finding configuration files.
- Creating backups.
- Automating repetitive Linux tasks.
- Investigating production issues.

---

## Resource

YouTube:
<[tutorial link](https://youtu.be/fwP2JW_VnZI?si=e9jPo2QSZjQQ9jIJ)>


# Day 3 – Linux Permissions & Process Monitoring

## Objective

Learn how Linux manages user permissions and understand basic process monitoring using the terminal.

---

## Activities Performed

### Linux Permissions

- Identified the current Linux user using `whoami`.
- Viewed user groups using `groups`.
- Inspected file permissions with `ls -l`.
- Created a shell script (`hello.sh`).
- Added content to the script using `echo`.
- Attempted to execute the script and received a **Permission denied** error.
- Granted execute permission using `chmod +x`.
- Successfully executed the script.
- Removed execute permission using `chmod -x`.
- Learned how to assign permissions to specific users using `u`, `g`, `o`, and `a`.

---

### Process Monitoring

- Displayed running processes using `ps`.
- Monitored system resource usage using `top`.
- Viewed previously executed commands using `history`.

---

## Commands Executed

```bash
whoami
groups
ls -l

touch hello.sh

echo '#!/bin/bash' > hello.sh
echo 'echo "Hello DevOps!"' >> hello.sh

cat hello.sh

./hello.sh

chmod +x hello.sh

ls -l

./hello.sh

chmod -x hello.sh

ps
top
history
```

---

## Observations

- Linux prevents scripts from executing without execute (`x`) permission.
- `chmod` modifies file permissions.
- `sudo` provides temporary administrator privileges for system-level tasks.
- Every command executed in the terminal runs as a separate process.
- The `top` command provides real-time monitoring of CPU, memory, and running processes.

---

## Learning Outcome

Successfully understood Linux permission management, shell basics, and process monitoring.

These concepts provide the foundation for working with Docker containers, deployment scripts, cloud servers, and CI/CD pipelines.
