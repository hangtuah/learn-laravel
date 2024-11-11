
# Version Control with Git

## Introduction
Git is a distributed version control system that allows developers to track changes in code, collaborate with others, and maintain a history of their project. In this session, we’ll explore Git basics, common commands, and how to use GitHub for Laravel projects.

---

## Setting Up Git
1. **Install Git**:
   - Download and install Git from [https://git-scm.com/](https://git-scm.com/).
   - Verify the installation:
     ```bash
     git --version
     ```

2. **Configure Git**:
   Set your username and email for Git commits:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "youremail@example.com"
   ```

---

## Basic Git Workflow
1. **Initialize a Git Repository**:
   Navigate to your Laravel project directory and initialize Git:
   ```bash
   git init
   ```

2. **Check Repository Status**:
   View changes in your repository:
   ```bash
   git status
   ```

3. **Add Files to Staging Area**:
   Add specific files or all files to the staging area:
   ```bash
   git add filename
   git add .
   ```

4. **Commit Changes**:
   Save changes to the repository with a message:
   ```bash
   git commit -m "Initial commit"
   ```

5. **View Commit History**:
   Check the log of commits:
   ```bash
   git log
   ```

---

## Working with Branches
1. **Create a New Branch**:
   ```bash
   git branch branch_name
   ```

2. **Switch to a Branch**:
   ```bash
   git checkout branch_name
   ```

3. **Merge Branches**:
   Merge a branch into the current branch:
   ```bash
   git merge branch_name
   ```

4. **Delete a Branch**:
   ```bash
   git branch -d branch_name
   ```

---

## Using GitHub
1. **Create a GitHub Repository**:
   - Go to [GitHub](https://github.com/) and create a new repository.

2. **Connect Local Repository to GitHub**:
   Add the remote repository URL:
   ```bash
   git remote add origin https://github.com/username/repository_name.git
   ```

3. **Push Changes to GitHub**:
   Push your local commits to GitHub:
   ```bash
   git push -u origin main
   ```

4. **Pull Changes from GitHub**:
   Update your local repository with the latest changes:
   ```bash
   git pull origin main
   ```

---

## Collaborating with Git
1. **Clone a Repository**:
   Clone an existing repository from GitHub:
   ```bash
   git clone https://github.com/username/repository_name.git
   ```

2. **Create Pull Requests**:
   - Make changes in a new branch.
   - Push the branch to GitHub.
   - Open a pull request on GitHub for review.

3. **Resolve Merge Conflicts**:
   If two changes conflict, Git will notify you. Resolve conflicts in the files and then:
   ```bash
   git add .
   git commit -m "Resolved merge conflicts"
   git push
   ```

---

## Hands-On Task
1. Initialize a Git repository in your Laravel project.
2. Make some changes to your project and commit them.
3. Push your project to a new GitHub repository.
4. Create a new branch for a feature (e.g., `feature/add-login`) and make changes.
5. Merge the feature branch back into the `main` branch.
6. Clone the repository onto another machine or directory.

---

## Summary
In this session, we learned the basics of version control using Git and how to collaborate using GitHub. Git helps track changes, collaborate with team members, and maintain a clean history of your project.

---
