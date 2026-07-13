# Week 1 – Applying DevOps Learning to the SOS Project

## Objective
Applied Linux, Git, and GitHub concepts to prepare the Personal Safety Emergency Alert System (SOS) project for a professional DevOps workflow.

---

## 1. Clone Repository into Ubuntu (WSL)

**Commands**
```bash
cd ~
mkdir Projects && cd Projects
git clone https://github.com/Thesansa/personal-safety-emergency-alert-system.git
cd personal-safety-emergency-alert-system
```

**Skills:** `cd`, `mkdir`, `ls`, `pwd`, `git clone`

**Outcome**
- Cloned the GitHub repository into the Linux environment.
- Created a local working copy for development.

---

## 2. Explore Repository Structure

**Commands**
```bash
pwd
ls
ls -l
cd docs
cd ..
```

**Skills:** `pwd`, `ls`, `ls -l`, `cd`

**Outcome**
- Navigated the project using Linux terminal.
- Understood the repository structure.

---

## 3. Create Initial Project Structure

**Commands**
```bash
mkdir frontend backend database docker scripts

cd docs
mkdir api deployment sprints

cd sprints
mkdir sprint-00
cd sprint-00
touch goals.md progress.md retrospective.md
```

**Skills:** `mkdir`, `touch`, `cd`

**Outcome**
- Created folders for frontend, backend, database, Docker, scripts, and sprint documentation.

---

## 4. Practice Linux File Management

**Commands**
```bash
cat README.md
rm goals.md
rmdir
```

**Concepts Learned**
- `cat` reads files.
- `rm` removes files.
- `rmdir` removes empty directories.
- Linux is case-sensitive.
- Terminal errors help identify and correct mistakes.

---

## 5. Learn How Git Tracks Files

Git does not track empty directories, so placeholder files were added.

**Commands**
```bash
touch frontend/.gitkeep
touch backend/.gitkeep
touch database/.gitkeep
touch docker/.gitkeep
touch scripts/.gitkeep
```

**Outcome**
- Enabled Git to track the project folder structure.

---

## 6. Commit Initial Project Structure

**Commands**
```bash
git status
git add .
git commit -m "Initialize project structure"
git log --oneline
```

**Skills**
- Check repository status
- Stage changes
- Create commits
- View commit history

---

## 7. Configure GitHub SSH Authentication

Migrated from HTTPS to SSH for secure authentication.

**Commands**
```bash
ls -la ~/.ssh

ssh-keygen -t ed25519 -C "thesansasemali@gmail.com"

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519"

cat ~/.ssh/id_ed25519.pub

git remote -v
git remote set-url origin git@github.com:Thesansa/personal-safety-emergency-alert-system.git
git remote -v

ssh -T git@github.com

git push
```

**Outcome**
- Configured SSH authentication.
- Enabled secure, password-free Git operations.
- Successfully pushed changes to GitHub.

---

## Overall Outcome

The SOS project is now ready for iterative development using a DevOps-oriented workflow.

### Skills Applied
- Linux terminal navigation
- Linux file management
- Project structure organization
- Git version control
- Commit history management
- GitHub SSH authentication
- Secure code synchronization

### Repository Status
- ✅ Ubuntu (WSL) environment configured
- ✅ Repository cloned locally
- ✅ Initial project structure created
- ✅ Sprint documentation initialized
- ✅ Initial commit completed
- ✅ GitHub authentication migrated to SSH
- ✅ Project successfully pushed to GitHub
