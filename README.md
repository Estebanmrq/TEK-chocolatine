# 🍫 CHOCOLATINE - Improve Integration and Testing with GitHub Actions

Welcome to **Chocolatine**! 🥐🍫
Whatever your stance on the name (Chocolatine vs. Pain au Chocolat), this project is all about making workflow smoother and more efficient with **GitHub Actions**.

GitHub Actions is like the chocolatine of development – it makes everything easier. I automate CI/CD, enhance testing, enforce good practices, and focus on things that matter (not the eternal name debate 😉).

## 📜 Summary

1. [Introduction](#-introduction)
2. [Technical Details](#-technical-details)
3. [Features](#️-features)
4. [Environment Variables](#-environment-variables)
5. [Jobs](#️-jobs)
6. [Contributors](#-contributors)

## 🎯 Introduction

The **Chocolatine** project is designed to help automate and enforce good practices in a GitHub repository using **GitHub Actions**. I set up a **YAML workflow file** to run on events like pushes and pull requests, streamlining my development process.

## 🔧 Technical Details

- The workflow file is named `chocolatine.yml`.
- It is placed at the root of the repository, but to work in your repository it must be in the `.github/workflows` folder.
- The workflow is compatible with **Epitech projects** and their tools.
- Allowed external actions:
  - `actions/checkout`
  - `pixta-dev/repository-mirroring-action`
- **Important:** Sensitive data like secrets are not hardcoded!

## ⚙️ Features

The GitHub Actions workflow includes:

1. **Trigger events**:  
   - Runs on every `push` and `pull request` unless:
     - The branch name starts with `ga-ignore-`.
     - The repository is the same as the mirror repository.

2. **Job sequence**:
   - **Checks out** the repository.
   - Each job runs only if the previous one succeeds.

## 🌍 Environment Variables

I define these at the workflow level:

- `MIRROR_URL`: The URL of the repository mirror.
- `EXECUTABLES`: `:` separated list of expected executable paths.

## 🛠️ Jobs

1. **Check Coding Style**  
   - ID: `check_coding_style`
   - Runs in a `ghcr.io/epitech/coding-style-checker:latest` container.
   - Runs the command: `check.sh $(pwd) $(pwd)`
   - Displays errors as annotations.

2. **Check Program Compilation**  
   - ID: `check_program_compilation`
   - Runs `make` and verifies executables.
   - Timeout: 2 minutes.

3. **Run Tests**  
   - ID: `run_tests`
   - Executes `make tests_run`.
   - Timeout: 2 minutes.

4. **Push to Mirror**  
   - ID: `push_to_mirror`
   - Mirrors the repository using a secret SSH key (`GIT_SSH_PRIVATE_KEY`).


## 👥 Contributors

- Main Contributor: [MARQUES Esteban](https://github.com/Estebanmrq)
