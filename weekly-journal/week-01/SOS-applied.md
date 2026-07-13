# Week 1 – Applying DevOps Learning to the SOS Project

## Objective

Apply the Linux, Git, and GitHub concepts learned during Week 1 to establish a professional development environment and prepare the Personal Safety Emergency Alert System (SOS) project for a DevOps-oriented workflow.

---

# Tasks Performed

## 1. Cloned the Repository into Ubuntu (WSL)

### Commands

```bash
cd ~
mkdir Projects
cd Projects
git clone https://github.com/Thesansa/personal-safety-emergency-alert-system.git
cd personal-safety-emergency-alert-system
```

### Outcome

- Set up the SOS project inside the Ubuntu (WSL) environment.
- Established Linux as the primary development environment.
- Prepared the project for command-line based development.

---

## 2. Explored the Repository Structure

### Commands

```bash
pwd
ls
ls -l
cd docs
cd ..
```

### Outcome

- Navigated the repository using Linux terminal commands.
- Became familiar with the project structure without relying on a graphical interface.
- Reinforced Linux navigation skills.

---

## 3. Created the Initial Project Structure

### Commands

```bash
mkdir frontend backend database docker scripts

cd docs
mkdir api deployment sprints

cd sprints
mkdir sprint-00
cd sprint-00
touch goals.md progress.md retrospective.md
```

### Outcome

- Created the initial directory structure for the application.
- Organized the repository for frontend, backend, database, Docker configuration, automation scripts, and project documentation.
- Established a clean foundation for future development.

---

## 4. Practiced Linux File Management

### Commands

```bash
cat README.md
rm goals.md
rmdir
```

### Concepts Applied

- File creation
- File deletion
- Directory management
- Reading file contents
- Terminal navigation

### Outcome

- Applied Linux file management commands within a real project.
- Improved confidence working entirely through the terminal.
- Understood that Linux is case-sensitive and provides informative error messages for troubleshooting.

---

## 5. Prepared Git to Track the Project Structure

Git does not track empty directories, so placeholder files were added.

### Commands

```bash
touch frontend/.gitkeep
touch backend/.gitkeep
touch database/.gitkeep
touch docker/.gitkeep
touch scripts/.gitkeep
```

### Outcome

- Enabled Git to track the intended project structure.
- Learned why placeholder files are commonly used in Git repositories.

---

## 6. Committed the Initial Project Structure

### Commands

```bash
git status
git add .
git commit -m "Initialize project structure"
git log --oneline
```

### Outcome

- Reviewed repository status.
- Staged project files.
- Created the first structural commit.
- Verified commit history.

---

## 7. Configured GitHub SSH Authentication

Initially, the repository used HTTPS authentication, which required authentication during push operations.

To establish a more secure and efficient workflow, the repository was migrated from HTTPS to SSH authentication.

### Commands

```bash
ls -la ~/.ssh

ssh-keygen -t ed25519 -C "thesansasemali@gmail.com"

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

cat ~/.ssh/id_ed25519.pub

git remote -v
git remote set-url origin git@github.com:Thesansa/personal-safety-emergency-alert-system.git
git remote -v

ssh -T git@github.com

git push
```

### Outcome

- Generated an SSH key pair.
- Connected GitHub using SSH authentication.
- Updated the Git remote from HTTPS to SSH.
- Successfully authenticated with GitHub.
- Enabled secure password-free Git operations for future development.

---

# DevOps Concepts Applied

During this week, the following DevOps concepts were applied directly to the SOS project:

- Linux terminal navigation
- Linux file management
- Repository organization
- Version control using Git
- Git commit workflow
- GitHub repository management
- SSH-based authentication
- Professional project structure organization

---

# Challenges Encountered

### HTTPS Authentication

Initially, GitHub required authentication when pushing changes through HTTPS.

After researching the issue, SSH key authentication was configured and the repository remote URL was updated to use SSH instead of HTTPS.

This resulted in a smoother and more secure Git workflow.

---

# Weekly Outcome

By the end of Week 1:

- ✅ Ubuntu (WSL) configured as the development environment.
- ✅ SOS repository cloned locally.
- ✅ Professional project directory structure established.
- ✅ Sprint documentation initialized.
- ✅ Linux terminal used for repository management.
- ✅ Initial Git commit completed.
- ✅ GitHub authentication migrated from HTTPS to SSH.
- ✅ Repository successfully synchronized with GitHub.

---

# Reflection

This week marked the transition from learning DevOps concepts to applying them in a real software project.

Instead of using Linux only for practice exercises, I managed the SOS repository directly through Ubuntu (WSL), organized the project structure using terminal commands, and integrated Git version control into my development workflow.

Configuring SSH authentication also introduced me to a more secure and professional way of interacting with GitHub, laying the foundation for future topics such as Docker, cloud deployment, and CI/CD.

Week 1 demonstrated that DevOps is not only about learning individual tools—it is about using those tools together to create an efficient, secure, and repeatable software development workflow.
