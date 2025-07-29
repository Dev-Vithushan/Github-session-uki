# GitHub Merging and Pull Request (PR) Conflicts: Workshop Guide

Welcome to the workshop on **GitHub merging** and **PR conflict resolution**! This session is designed for students to learn the practical workflow of collaborating on projects, making pull requests, and resolving merge conflicts.

## Table of Contents
- Introduction
- Setting Up the Repository
- Forking and Cloning
- Creating a New Branch
- Making Changes
- Creating a Pull Request (PR)
- Simulating a Merge Conflict
- Resolving Merge Conflicts
- Best Practices
- Useful Commands Reference

## Introduction

Collaborative projects on GitHub often involve multiple contributors. Understanding how to merge branches and resolve conflicts is essential for smooth teamwork.

## 1. Setting Up the Repository

1. Create a new GitHub repository (or use an existing one).
2. Initialize with a `README.md` or any file.

## 2. Forking and Cloning

- **Fork** the repository to your GitHub account.
- **Clone** the fork to your local machine:

   ```sh
   git clone https://github.com/your-username/repository-name.git
   cd repository-name
   ```

## 3. Creating a New Branch

- Always create a feature branch before making changes:

   ```sh
   git checkout -b feature/your-feature-name
   ```

## 4. Making Changes

- Edit files or add new files to the repository.
- Stage and commit your changes:

   ```sh
   git add .
   git commit -m "Describe your feature or fix"
   ```

## 5. Creating a Pull Request (PR)

- Push your branch to your forked repository:

   ```sh
   git push origin feature/your-feature-name
   ```

- Go to GitHub, select your branch, and open a **Pull Request** (PR) to the main repository.

## 6. Simulating a Merge Conflict

To practice resolving conflicts:
1. One student modifies a specific line in a file on their branch and creates a PR.
2. Another student modifies the same line in the same file on a different branch and creates a PR.
3. When trying to merge the second PR, GitHub will show a **merge conflict**.

## 7. Resolving Merge Conflicts

When a conflict arises:

1. **Fetch** the latest changes:

    ```sh
    git fetch origin
    ```

2. **Checkout** to your branch and try to merge the latest code from the base branch (usually `main` or `master`):

    ```sh
    git checkout feature/your-feature-name
    git merge origin/main
    ```

3. Git will indicate which files have conflicts. Open those files; conflicted areas will be marked like:

    ```
    <<<<<<< HEAD
    your changes
    =======
    incoming changes
    >>>>>>> origin/main
    ```

4. Edit the file to keep the correct changes. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) after resolving.

5. **Add** and **commit** the resolved files:

    ```sh
    git add conflicted-file.txt
    git commit -m "Resolved merge conflict in conflicted-file.txt"
    ```

6. **Push** your changes and update the PR.

## 8. Best Practices

- Pull from upstream often to avoid big conflicts:

    ```sh
    git pull origin main
    ```

- Make small, focused changes per PR.
- Write clear commit messages.
- Communicate with your team on potentially conflicting areas.

## 9. Useful Commands Reference

| Command                                    | Description                                 |
|---------------------------------------------|---------------------------------------------|
| `git checkout -b branch-name`               | Create & switch to a new branch             |
| `git add .`                                | Add changes to staging area                 |
| `git commit -m "message"`                   | Commit staged changes with a message        |
| `git push origin branch-name`               | Push branch to remote                       |
| `git fetch origin`                          | Fetch latest changes from remote            |
| `git merge origin/main`                     | Merge upstream into current branch          |
| `git status`                                | See repo status and conflicted files        |
| `git log`                                   | View commit history                         |

Happy coding and collaborating! If you have questions, ask during the session or raise issues on GitHub.

Sources
