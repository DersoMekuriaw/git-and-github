# Git vs GitHub — Documentation

This README is a documentation-style reference for Git (the version control system) and GitHub (a hosting and collaboration platform). It covers concepts, differences, common commands, workflows, best practices, and troubleshooting.

Table of contents

- Introduction
- Git — overview, install, basic usage
- GitHub — overview, setup, collaboration
- Key differences (concise table)
- Commands cheat sheet (commonly used commands)
- Workflows (feature branches, PRs, forks)
- Best practices
- Troubleshooting & common errors
- .gitignore example
- Resources

---

Introduction

This document is intended to be used as a reference for new and intermediate users who want a clear, practical guide to using Git locally and GitHub for hosted collaboration.

1) Git — Overview

What is Git?

Git is a distributed version control system (DVCS) for tracking changes in files and coordinating work among multiple people. It stores snapshots of a project and enables branching, merging, and history inspection.

Key concepts

- Repository: a directory tracked by Git (contains a .git folder).
- Commit: a recorded snapshot of the repository state.
- Branch: a movable pointer to a commit (used for parallel development).
- Working tree / index (staging area): where changes are prepared before committing.
- Remote: a hosted copy of the repo (e.g., on GitHub).

Installing Git

Windows (Chocolatey):
```powershell
choco install git -y
```

macOS (Homebrew):
```bash
brew install git
```

Ubuntu / Debian:
```bash
sudo apt update
sudo apt install git -y
```

Basic configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

2) Git — Basic usage & commands

Initialize a repository
```bash
git init                 # Create a new local repository
```

Clone a repository
```bash
git clone <url>          # e.g. https://github.com/user/repo.git
```

Staging and committing
```bash
git status               # See changed files
git add <file>           # Stage a single file
git add .                # Stage all changes
git commit -m "message" # Create a commit
```

Branching & merging
```bash
git branch               # List local branches
git switch -c feature    # Create and switch to branch
git switch main          # Switch to main
git merge feature        # Merge changes into current branch
git branch -d feature    # Delete local branch
```

Working with remotes
```bash
git remote -v                        # Show remotes
git remote add origin <url>          # Add remote
git push -u origin main              # Push and set upstream
git fetch origin                     # Fetch remote changes
git pull origin main                 # Fetch+merge from remote
```

Undoing and recovering
```bash
git restore <file>                   # Discard changes in working tree
git restore --staged <file>          # Unstage file
git reset --soft HEAD~1              # Move HEAD back, keep changes staged
git reset --hard HEAD~1              # Move HEAD back, discard changes
git revert <commit>                  # Create a new commit that undoes a commit
git stash                            # Save working changes temporarily
git stash pop                        # Restore saved changes
```

Inspecting history
```bash
git log --oneline --graph --decorate  # Compact visual history
git show <commit>                     # Show commit details
git diff                              # See unstaged changes
```

3) GitHub — Overview and setup

What is GitHub?

GitHub hosts Git repositories and adds collaboration features: pull requests, code review, issue tracking, actions (CI/CD), pages (static hosting), and more.

Creating an account and repo

- Create an account at https://github.com
- Click New repository to create a hosted repo (public or private)

Authentication methods

- HTTPS with personal access token (recommended for automation)
- SSH keys for passwordless push/pull from your machine

Generate and add SSH key (example)
```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
# copy the contents of ~/.ssh/id_ed25519.pub into GitHub Settings → SSH and GPG keys
```

4) GitHub collaboration features & common workflows

Fork & pull request (contribute to upstream)

- Fork the repository on GitHub
- Clone your fork
- Create a feature branch, commit, push
- Open a Pull Request (PR) from your fork's branch to upstream
- Address review comments, then merge

Feature-branch workflow (within a team)

- Create a branch for each change
- Open PR to main or develop branch
- Use CI to run tests and checks
- Have at least one reviewer approve before merging

Pull requests and code review

- Use meaningful PR titles and descriptions
- Link related issue numbers
- Address review comments in commits, or squash and push

Using GitHub Actions (CI)

- Add workflow YAML files in .github/workflows/ to run unit tests, linters, builds

5) Key differences (summary)

| Area | Git | GitHub |
|---|---|---|
| Primary purpose | Local version control | Hosted repository + collaboration features
| Requires Internet? | No (local) | Yes to access hosted features
| Examples of tasks | commit, branch, merge, revert | pull requests, issues, actions, pages
| Storage | Local and remote (when pushed) | Hosted and backed-up on GitHub servers

6) Commands cheat sheet (compact)

Repository setup
```bash
git init
git clone <url>
```

Daily workflow
```bash
git status
git add .
git commit -m "message"
git pull --rebase origin main
git push
```

Branching and PRs
```bash
git switch -c feature
# make changes
git add . && git commit -m "feat: ..."
git push -u origin feature
# open PR on GitHub
```

Rewriting history (advanced)
```bash
git rebase main             # Replay commits onto main
git rebase -i HEAD~3        # Interactive rebase (edit/squash)
git cherry-pick <commit>    # Apply a single commit onto current branch
```

7) Best practices

- Use small, focused commits with clear messages
- Use feature branches for changes
- Use PR templates and require reviews before merging
- Protect main branch with branch protection rules and required CI checks
- Do not commit secrets or large binaries; use .gitignore and Git LFS when needed
- Keep repository README and CONTRIBUTING files up to date

8) Troubleshooting & common errors

- "Updates were rejected (non-fast-forward)":
  - Run `git pull --rebase` or `git fetch` then `git merge` to integrate remote changes, resolve conflicts, then push.
- Merge conflict on merge/pull:
  - Edit conflicting files, `git add` the resolved files, then `git commit` (or continue rebase with `git rebase --continue`).
- Permission denied (publickey):
  - Ensure your SSH key is added to GitHub or use HTTPS with token.
- Detached HEAD:
  - Create a branch `git switch -c my-branch` to preserve work.

9) Example `.gitignore`
```gitignore
# Node
node_modules/
npm-debug.log

# Environment
.env

# Build
dist/

# OS
.DS_Store
```

10) Additional resources

- Git official docs: https://git-scm.com/doc
- Pro Git book: https://git-scm.com/book/en/v2
- GitHub docs: https://docs.github.com
- Learn Git Branching (interactive): https://learngitbranching.js.org

If you'd like I can now:

- Remove or add specific sections (cheat sheet, advanced topics).
- Split this into multiple markdown files under a `docs/` folder and scaffold a simple MkDocs or GitHub Pages setup.

Last updated: 2025-12-28

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
