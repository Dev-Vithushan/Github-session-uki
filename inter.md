# GitHub Merging and Pull Request (PR) Conflicts: Workshop Guide

Welcome to the workshop on **GitHub merging** and **PR conflict resolution**! This session is designed for students to learn the practical workflow of collaborating on projects, making pull requests, and resolving merge conflicts.

## Table of Contents
- Introduction
- Setting Up the Repository
- Forking and Cloning
- Creating a New Branchgit push 
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

Sure! Here's an additional section for your Markdown file that covers **how to revert changes** in Git and GitHub, useful for students learning about collaboration and version control:

## 10. Reverting Changes

Mistakes happen—and Git makes it easy to revert them safely. Let’s learn how to undo changes in different scenarios.

### 🧯 A. Undo a Local Commit (Before Push)

If you've made a commit but haven’t pushed it yet, and you want to undo it:

```sh
git reset --soft HEAD~1
```

- This keeps your changes in the staging area so you can recommit or modify.

To delete the commit **and** unstage changes:

```sh
git reset --mixed HEAD~1
```

To delete the commit and discard all changes:

```sh
git reset --hard HEAD~1
```

> ⚠ Use `--hard` with caution: It deletes all local changes without recovery.

### 🌀 B. Revert a Pushed Commit (Using `git revert`)

You can undo a pushed commit by creating a new commit that reverses the changes:

```sh
git revert <commit-hash>
```

- This is **safe** for shared branches like `main` because it doesn’t rewrite history.
- After reverting, push the changes:

```sh
git push origin branch-name
```

### 🔁 C. Using GitHub Revert (via UI)

GitHub lets you revert a merged PR directly:

1. Go to the original PR.
2. Click the **“Revert”** button (visible after merge).
3. GitHub creates a new PR with reversed changes.
4. Review and merge it.

### 📌 Extra: Revert a Merge Commit

If you want to revert a **merge commit**, add `-m 1` to specify the parent branch:

```sh
git revert -m 1 <merge-commit-hash>
```

> `-m` tells Git which side to keep base from (usually `1` = main branch).

## ✅ Best Practices for Reverting

- Communicate with your team before reverting shared changes.
- Always use `git revert` instead of `git reset` when working on shared/public branches.
- Avoid using `git push --force` unless you know exactly what you're doing.

Let me know if you'd like this added to the same `.md` file or presented differently!

Sources
