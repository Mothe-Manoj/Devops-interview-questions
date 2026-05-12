### What is the difference between git fork and git clone, and when would you use each?

**git fork** creates a copy of a repository on your GitHub (or GitLab, etc.) account, letting you propose changes without write access to the original repo.
**git clone** creates a local copy of any Git repository (your own or someone else’s) on your machine for development.

# Explanation

- When you fork a repository on GitHub, you're telling the platform: "I want a separate version of this repository in my own GitHub account."
This is especially useful for contributing to open-source and team projects where you don't have direct write access to the main repository. You fork the repo, make changes in your fork, and then create a pull request to propose those changes to the original project.

- On the other hand, **git clone** is used to download a repository (forked or original) to your local development machine. This is what actually gives you the codebase to work with.

```Fork = GitHub-level action, Clone = Local machine-level action.```
