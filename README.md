# 🚀 Git vs GitHub: Complete Guide for Beginners

<p align="center">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
  <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  <img src="https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge" alt="Version">
</p>

<p align="center">
  <strong>A comprehensive guide to understanding Git and GitHub with practical commands</strong>
</p>

---

## 📋 Table of Contents
- [🎯 Introduction](#-introduction)
- [🤔 What is Git?](#-what-is-git)
- [🌐 What is GitHub?](#-what-is-github)
- [🔍 Key Differences](#-key-differences)
- [⚡ Quick Start](#-quick-start)
- [🛠️ Git Commands Cheat Sheet](#️-git-commands-cheat-sheet)
- [🔄 GitHub Workflow](#-github-workflow)
- [📊 Comparison Table](#-comparison-table)
- [❓ FAQ](#-faq)
- [📚 Resources](#-resources)

---

## 🎯 Introduction

Welcome! This guide explains the difference between **Git** (version control system) and **GitHub** (hosting platform) with practical examples.

### 📺 Watch Our Tutorial
[![YouTube Video](https://img.shields.io/badge/Watch_Video-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com/your-video-link)

---

## 🤔 What is Git?
# 🚀 Git vs GitHub — Beginner's Guide

<p align="center">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
  <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  <img src="https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge" alt="Version">
</p>

A concise, cleaned-up reference for Git (VCS) and GitHub (hosting) with practical commands.

---

## 📋 Quick Navigation
- [Introduction](#introduction)
- [What is Git?](#what-is-git)
- [What is GitHub?](#what-is-github)
- [Key Differences](#key-differences)
- [Quick Start](#quick-start)
- [Git Commands Cheat Sheet](#git-commands-cheat-sheet)
- [GitHub Workflow](#github-workflow)
- [Comparison Table](#comparison-table)
- [FAQ](#faq)
- [Resources](#resources)

---

## Introduction

This guide explains the core differences between **Git** (a distributed version control system) and **GitHub** (a cloud hosting and collaboration platform) and provides practical command examples.

## What is Git?

Git is a distributed version control system that tracks changes to files and enables collaboration locally and across teams.

Key features:

- Local operations (work offline)
- Branching and merging
- Data integrity via commit hashing
- Fast performance
- Open source

### Basic Git setup
```bash
# Configure identity
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Set default initial branch name
git config --global init.defaultBranch main
```

## What is GitHub?

GitHub is a cloud platform for hosting Git repositories with features for collaboration, code review, CI/CD, and project management.

Common GitHub features:

- Cloud hosting for repositories
- Pull requests and code review
- GitHub Actions for CI/CD
- GitHub Pages for static sites
- Issue tracking and project boards

## Key Differences

| Aspect | Git | GitHub |
|---|---:|:---|
| Type | Version control system | Hosting & collaboration platform
| Location | Local machine | Cloud / web
| Internet needed? | No (for local work) | Yes (to access hosted repo)
| Created by | Linus Torvalds | Tom Preston-Werner et al.
| Ownership | Open source | Microsoft (GitHub)
| Cost | Free | Free + paid plans for advanced features

Analogy: Git is like the word processor on your computer; GitHub is like Google Docs with sharing, reviews, and backups.

## Quick Start

### Install Git

Windows (Chocolatey):
```powershell
choco install git -y
```

macOS (Homebrew):
```bash
brew install git
```

Ubuntu/Debian:
```bash
sudo apt update
sudo apt install git -y
```

### GitHub setup (SSH)
```bash
# Generate SSH key (if you prefer SSH)
ssh-keygen -t ed25519 -C "your-email@example.com"
# Add the public key to GitHub > Settings > SSH and GPG keys
# Test connection
ssh -T git@github.com
```

## Git Commands Cheat Sheet

Repository operations
```bash
# Initialize repository
git init

# Clone remote repository (HTTPS)
git clone https://github.com/user/repo.git

# Clone via SSH
git clone git@github.com:user/repo.git

# Check status
git status
```

Basic workflow
```bash
# Stage changes
git add file.txt        # single file
git add .               # all changes

# Commit
git commit -m "Your message"

# Push
git push origin main
git push -u origin main  # set upstream

# Pull
git pull origin main
```

Branching
```bash
# List branches
git branch
git branch -a

# Create and switch to a branch
git switch -c feature-branch

# Switch branch
git switch main

# Merge
git switch main
git merge feature-branch

# Delete branch
git branch -d feature-branch
```

Undoing changes
```bash
# Unstage a file (keep changes)
git reset file.txt

# Discard changes in working directory (use carefully)
git restore file.txt

# Revert a commit (safe)
git revert <commit-hash>

# Reset to previous commit (dangerous)
git reset --soft HEAD~1   # keep changes staged
git reset --hard HEAD~1   # discard changes

# Stash
git stash
git stash pop
```

## GitHub Workflow

Typical feature branch workflow:

1. Create a branch locally
```bash
git switch -c new-feature
```
2. Work, stage, and commit
```bash
git add .
git commit -m "Add new feature"
```
3. Push branch
```bash
git push origin new-feature
```
4. Open a Pull Request on GitHub and follow review/merge steps.

Contributing to upstream projects (fork + sync):

```bash
# Clone your fork
git clone https://github.com/YOUR-USERNAME/repo.git
cd repo

# Add upstream remote
git remote add upstream https://github.com/ORIGINAL-USER/repo.git

# Fetch and merge upstream changes
git fetch upstream
git merge upstream/main
```

## Comparison Table

| Task | Git (local) | GitHub (hosted) |
|---|---:|:---|
| Start project | `git init` | Create repo on GitHub
| Get existing | `git clone` | Fork or clone via UI
| Save changes | `git commit` | Changes saved when you push
| Share | `git push` | Hosted on GitHub
| Code review | `git diff` | Pull Request review

## FAQ

Q: Do I need GitHub to use Git?

A: No — Git works locally. GitHub adds collaboration and cloud backup.

Q: HTTPS vs SSH?

- HTTPS: simpler, can use tokens for authentication.
- SSH: more convenient for repeated pushes once set up.

Q: What is `.gitignore`?

A `.gitignore` tells Git which files or patterns to ignore. Example:
```gitignore
node_modules/
.env
*.log
dist/
.DS_Store
```

Q: Common errors

- "Updates were rejected" → `git pull --rebase` or `git pull` then `git push`.
- Merge conflicts → resolve files, `git add`, then `git commit`.
- Permission denied → check SSH keys or use a personal access token for HTTPS.

## Resources

- Official Git docs: https://git-scm.com/doc
- GitHub Docs: https://docs.github.com
- Pro Git book: https://git-scm.com/book/en/v2
- Interactive: https://learngitbranching.js.org

---

If you want, I can now:

- Split this into multiple docs under a `docs/` folder and add `mkdocs.yml` for GitHub Pages (recommended).
- Create a smaller, pinned `README.md` with links to detailed pages.

Last updated: December 28, 2025
