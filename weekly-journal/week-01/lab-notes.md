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
