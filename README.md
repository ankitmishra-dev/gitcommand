# **Git Commands Cheat Sheet**

This README includes all the essential Git commands you might need while working on your project. These commands will help you set up, manage, and manipulate your repository with ease. The commands are divided into different sections based on their purpose for easy navigation.

## **Table of Contents**

1. [Repository Setup](#repository-setup)
2. [Configuration](#configuration)
3. [Core Basic Git Operations](#core-basic-git-operations)
4. [Branching](#branching)
5. [Remote Repositories](#remote-repositories)
6. [File Management](#file-management)
7. [Viewing Commit History](#viewing-commit-history)
8. [Working with Gitignore](#working-with-gitignore)
9. [Advanced Git Operations](#advanced-git-operations)
10. [Additional Resources](#additional-resources)
11. [Commands for New and Existing Repositories](#commands-for-new-and-existing-repositories)

---

## **Repository Setup**

```bash

git init                         # Initialize a new Git repository
git clone <repository-url>       # Clone an existing repository
git remote set-url origin <url>  # Change the URL of the remote repository

```

## **Configuration**

```bash

git config --list                               # All git global config
git config --list --global                      # View all global config settings
git config --global user.name "<Your Name>"     # Set global username
git config --global user.email "<your.email@domain.com>" # Set global email
git config user.name                            # Verify username
git config user.email                           # Verify email
git branch --list master main                   # Check default branch for git config
git config --get remote.origin.url              # set remote origin url
git config --global init.defaultBranch main     # Set default branch to 'main'

```

## **Core Basic Git Operations**

```bash

git status                   # Check the status of your files
git log                      # View commit history
git add .                    # Stage all changes in the working directory
git add <filename>           # Stage a specific file
git commit -m "message"      # Commit staged changes with a message
git commit -a -m "message"   # Commit all tracked files directly (skips git add .)


# Discard Local File (Unstaged)

git restore .                 # Discard all changes in the working directory
git restore <path/to/file.ext># Discard changes in a specific file

git checkout <path/to/file.ext> # Discard changes in a specific file
git checkout .                # Discard changes in all files


# Discard Local File (Staged)

git reset <filename>          # Unstage a specific file from the staging area
git reset .                   # Unstage all files from the staging area

git restore --staged <path/to/file.ext> # Unstage a specific file from the staging area
git restore --staged .        # Unstage all files from the staging area

git checkout -f               # Discard changes whether staged or unstaged


# Note:
# - Use 'restore' to discard changes in modern workflows.
# - 'checkout' can also be used for discarding changes, but 'restore' is clearer in this context.

```

## **Branching**

```bash

git branch                   # List all branches
git branch <branch-name>      # Create a new branch
git branch -d <branch-name>   # Delete a local branch
git branch -v                 # Show last commit on each branch
git checkout <branch-name>    # Switch to an existing branch
git checkout -b <branch-name> # Create and switch to a new branch
git checkout -d <branch-name> # Delete a branch (if merged)
git checkout -f               # Revert all changes in the working directory

```

## **Remote Repositories**

```bash

git remote add origin <url>   # Add a remote repository
git remote -v                 # View remote repository information
git push -u origin master     # Push to the remote repository (master branch)
git push -u origin <branch>   # Push a specific branch to the remote
git push origin <branch-name> # Push a specific branch to GitHub
git pull origin <branch>      # Pull changes from the remote repository
git fetch origin              # Fetch the latest changes without merging
git reset --hard origin/master # Reset local branch to match remote

git push --set-upstream origin {origin-branch-to-track} # no need to do this seprately if we are using -u identifier while pushing


```

## **File Management**

```bash

git rm <filename>             # Remove a file from the repository and stage the deletion
git mv <old-filename> <new-filename> # Rename a file and stage the changes
git rm --cached <filename>    # Stop tracking a file (while keeping it locally)

```

## **Viewing Commit History**

```bash

git log                       # View commit history
git log --oneline             # View commit history in a concise format
git log -p                    # View commit history with changes
git log -n <num>              # View the last n commits
git log --stat                # View commit history with file changes
git log --pretty=oneline      # View commit history in a single line format
git log --since="2 weeks ago" # View commits since a certain time

```

## **Working with Gitignore**

Create a `.gitignore` file in the root of your repository to specify which files and directories Git should ignore.

### Examples:

```txt

# Ignore all .log files
*.log

# Ignore a specific file
aman.log

# Ignore a directory
dir/

# Ignore only the outer dir folder but track inner ones
/dir/

```

## **Advanced Git Operations**

```bash

git revert <commit>          # Create a new commit that reverts a previous commit
git revert --no-commit <commit> # Revert a commit without automatically committing the changes
git reset --soft <commit>    # Reset to a specific commit but keep changes in the working directory
git reset --hard <commit>    # Reset to a specific commit but dont leaves changes in working directory
git diff                     # Compare changes in the working directory and the staging area
git diff --staged            # Compare the staging area with the last commit
git diff <base> <file>       # Compare specific changes between a file and the base
git log --since=2days        # View commits since 2 days ago

```

## **Commands For New And Existing Repositories**

```bash

# If the repo is created directly from GitHub (e.g., https://github.com/ankitmishra-dev/build-something.git):

git clone https://github.com/ankitmishra-dev/build-something.git  # Clone the repository to your local machine
git init  # Re-initialize the git repository (though this is not necessary if the repo is already initialized)
git add .  # Stage all local changes
git commit -m "Initial commit"  # Commit the changes with a message
git branch -M main  # Ensure the local branch is named 'main' (since GitHub default is now 'main')
git remote add origin https://github.com/ankitmishra-dev/build-something.git  # Add the remote repository URL

git push -u origin main  # Push changes to the 'main' branch; '-u' sets the upstream so future push/pull commands won't need to specify the branch name

# For pushing an existing repo:

git remote add origin https://github.com/ankitmishra-dev/something-is-cooking.git  # Add the remote repository URL
git branch -M main  # Ensure the local branch is named 'main'
git push -u origin main  # Push the changes to the 'main' branch   

```

## **Additional Resources**

* [Official Git Documentation](https://git-scm.com/doc)
* [Git Cheat Sheet by GitHub](https://education.github.com/git-cheat-sheet-education.pdf)

---

### **Tips:**

* **`.gitignore`**: Use this file to keep unwanted files (e.g., log files, IDE files, etc.) out of your repository. Make sure to keep this file updated.

* **Branching Strategy**: Use meaningful branch names like `feature/user-auth`, `bugfix/login-page`, etc. This helps you maintain a cleaner history and makes collaboration easier.

* **Commit Message Best Practices**: Write clear, concise commit messages. For example:

  * `feat: add user login functionality`
  * `fix: resolve issue with form validation`
  * `docs: update README for Git setup instructions`
  * `JIRATICKET-1234: update README for Git setup instructions`

---

### **Contributor:**

* Ankit Mishra - [LinkedIn](https://www.linkedin.com/in/ankit-mishra99)


