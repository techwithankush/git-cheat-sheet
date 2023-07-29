# Git Commands
## This Gist contains all the useful commands for Git prepared by Ankush Yadav


Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.

If you are a developer and want to keep every version of your code/project (which you would most certainly want to), a Version Control System (VCS) is a very wise thing to use.

- All the commands used for Git
- Compatibility with GitHub
- ✨Magic ✨

## Commands

---------------------------
1. Git Configuration:
---------------------------

```sh
Configure User Information:
---------------------------
# Set your username
git config --global user.name "Your Name"

# Set your email address
git config --global user.email "your.email@example.com"

# View configured user information
git config --global --list

Configure Default Editor:
-------------------------

# Set the default text editor (e.g., VSCode, Nano, Vim)
git config --global core.editor "code"

Git Aliases:
------------

# Create a short alias for a Git command (e.g., 'st' for 'status')
git config --global alias.<alias_name> <git_command>

# Example: Set 'st' as an alias for 'status'
git config --global alias.st status

# View all configured aliases
git config --global --get-regexp alias

Ignoring Files:
---------------

# Create or edit a global .gitignore file to ignore specific files or patterns
git config --global core.excludesfile ~/.gitignore_global

# Example: Ignore .DS_Store files and temporary files globally
# ~/.gitignore_global
*.DS_Store
*.tmp

Color Configuration:
--------------------

# Enable colored output in Git commands
git config --global color.ui true

# Disable colored output in Git commands
git config --global color.ui false

Default Branch Name:
--------------------

# Set the default branch name for new repositories (Git 2.28 and later)
git config --global init.defaultBranch main

Credential Caching:
-------------------

# Enable credential caching for a specified period (in seconds)
git config --global credential.helper 'cache --timeout=3600'

# Use system-level credential manager (e.g., macOS Keychain, Windows Credential Manager)
git config --global credential.helper osxkeychain  # macOS
git config --global credential.helper wincred      # Windows

# Disable credential caching
git config --global --unset credential.helper

Proxy Configuration (if using a proxy server):
----------------------------------------------

# Set HTTP proxy
git config --global http.proxy http://proxy.example.com:8080

# Set HTTPS proxy
git config --global https.proxy https://proxy.example.com:8080

# Unset proxy configuration
git config --global --unset http.proxy
git config --global --unset https.proxy

User Interface:
---------------

# Set the default Git UI to a graphical tool like Git GUI
git config --global gui.ui graphical

# Set the default Git UI to a text-based tool like TUI (text user interface)
git config --global gui.ui tcl/tk

# Reset Git UI configuration to the default (auto-detect)
git config --global --unset gui.ui
```

---------------------------
2. Starting A Project:
---------------------------
```sh
1. Initialize a Git Repository:

# Create a new directory for your project
mkdir my_project
cd my_project

# Initialize a new Git repository
git init

2. Set Up .gitignore:

# Create a .gitignore file to specify files and directories to ignore
touch .gitignore

# Open the .gitignore file in your text editor and add entries for files and directories to ignore, e.g.:
# - Build artifacts
# - Temporary files
# - Sensitive information (e.g., API keys, passwords)
# - IDE-specific files

3. Add and Commit Initial Files:

# Add all files in the current directory to the staging area
git add .

# Commit the initial files with a meaningful message
git commit -m "Initial commit"

4. Create a Remote Repository (Optional):

# Go to GitHub (https://github.com) or other Git hosting service
# Create a new repository with the same name as your local project (e.g., "my_project")

5. Connect Local and Remote Repositories (Optional):

# Add the remote repository URL as "origin"
git remote add origin <remote_repository_url>

# Push the local repository to the remote repository
git push -u origin master

6. Branching and Development:

# Create a new branch for a feature or bug fix
git checkout -b feature/new-feature

# Make changes, add and commit them
git add <file_name>
git commit -m "Implement new feature"

# Push the branch to the remote repository (if needed)
git push origin feature/new-feature

# Merge the branch into the main branch (e.g., "master") after code review and testing
git checkout master
git merge feature/new-feature

7. Tagging Releases (Optional):

# Create a new tag for a release
git tag v1.0.0

# Push tags to the remote repository
git push --tags

8. Collaborating with Others:

# Pull latest changes from the remote repository before making changes
git pull origin master

# Resolve any conflicts if they occur during the pull

# Create and switch to a new branch for your changes
git checkout -b feature/your-feature

# Make changes, add and commit them

# Push the branch to the remote repository
git push origin feature/your-feature

# Create a pull request on the Git hosting service to merge your changes into the main branch

9. Git Help:

# Get help on a specific Git command
git help <command>

# Get help on Git concepts and guides
git help -g
```

---------------------------
3. Day-To-Day-Work:
---------------------------
```sh

Basic Commands:
---------------

# Clone a repository
git clone <repository_url>

# Check repository status
git status

# Stage changes for commit
git add <file_name>          # Add specific file
git add .                    # Add all changes in the current directory

# Commit changes with a message
git commit -m "Your commit message"

# Push changes to a remote repository
git push <remote_name> <branch_name>

# Pull latest changes from the remote repository
git pull <remote_name> <branch_name>

Branching and Merging:
----------------------

# Create a new branch
git branch <branch_name>

# Switch to an existing branch
git checkout <branch_name>

# Create a new branch and switch to it (shortcut for git branch + git checkout)
git checkout -b <branch_name>

# Merge a branch into the current branch
git merge <branch_name>

# Delete a branch (only when changes are merged)
git branch -d <branch_name>

Working with Remote Repositories:
---------------------------------

# Add a remote repository
git remote add <remote_name> <repository_url>

# List remote repositories
git remote -v

# Rename a remote repository
git remote rename <old_remote_name> <new_remote_name>

# Remove a remote repository
git remote remove <remote_name>

Viewing History and Changes:
----------------------------

# Show commit history
git log

# Show commit history with abbreviated SHA and commit messages
git log --oneline

# Show changes in a file between commits
git diff <commit_hash1> <commit_hash2> <file_name>

# Show changes between working directory and last commit
git diff

Undoing Changes:
----------------

# Discard changes in the working directory for a specific file
git checkout -- <file_name>

# Undo the last commit and keep changes staged
git reset --soft HEAD^

# Undo the last commit and discard changes
git reset --hard HEAD^

Miscellaneous:
--------------

# Create and switch to a new branch with the changes from specific commit
git cherry-pick <commit_hash>

# Create a new tag
git tag <tag_name>

# List all tags
git tag

# Show detailed information about a specific tag
git show <tag_name>

# Rebase current branch onto another branch
git rebase <base_branch>

# Show branches and their commits in a graph
git log --graph --oneline --all
```
---------------------------
3. Git branching model:
---------------------------
```sh
Branching Model Overview:
-------------------------

- master: The main branch containing the production-ready code.
- develop: The branch for ongoing development and integration of features.
- feature/<feature_name>: Branches created for developing new features.
- release/<version>: Branches created for preparing a new release.
- hotfix/<issue_name>: Branches created for fixing critical issues in production.

Creating and Switching Branches:
--------------------------------

# Create a new feature branch
git checkout -b feature/new-feature develop

# Create a new release branch
git checkout -b release/v1.2.0 develop

# Create a new hotfix branch
git checkout -b hotfix/issue-123 master

Merging Changes:
----------------

# Merge a feature branch into develop
git checkout develop
git merge feature/new-feature

# Merge a release branch into master and develop
git checkout master
git merge release/v1.2.0
git checkout develop
git merge release/v1.2.0

# Merge a hotfix branch into master and develop
git checkout master
git merge hotfix/issue-123
git checkout develop
git merge hotfix/issue-123

Finish a Release:
-----------------

# Tag the release commit
git checkout master
git tag v1.2.0

# Push tags to remote repository
git push origin --tags

Finish a Feature:
-----------------

# Merge the feature branch into develop and remove the feature branch
git checkout develop
git merge --no-ff feature/new-feature
git branch -d feature/new-feature

Finish a Hotfix:
----------------

# Merge the hotfix branch into master and develop and remove the hotfix branch
git checkout master
git merge --no-ff hotfix/issue-123
git branch -d hotfix/issue-123
git checkout develop
git merge --no-ff hotfix/issue-123
git branch -d hotfix/issue-123

Pull Requests (Optional):
--------------------------

# Create a pull request for a feature or hotfix branch on the remote hosting service.
# Review and merge the pull request after code review and testing.

Viewing History and Changes:
----------------------------

# Show commit history with branches and merges in a graph
git log --graph --oneline --all

# Show changes between branches
git diff <branch1>..<branch2>
```

---------------------------
5. Review your work:
---------------------------
```sh


Viewing Changes:
----------------

# View changes in the working directory (unstaged changes)
git status

# View changes in a file
git diff <file_name>

# View changes between the working directory and the last commit
git diff

# View changes between the staging area (index) and the last commit
git diff --staged

Staging Changes:
----------------

# Stage changes for commit (add all changes)
git add .

# Stage specific changes in a file
git add <file_name>

# Unstage changes from the staging area (before committing)
git reset <file_name>

Committing Changes:
-------------------

# Commit staged changes with a message
git commit -m "Your commit message"

# Amend the last commit (combine with the staged changes)
git commit --amend

Viewing Commit History:
-----------------------

# Show commit history
git log

# Show commit history with abbreviated SHA and commit messages
git log --oneline

# Show changes introduced by each commit
git log -p

# Show commit history for a specific file
git log <file_name>

# Show commit history for a specific author
git log --author="Author Name"

# Show commit history between two commits
git log <commit_hash1>..<commit_hash2>

Undoing Changes:
----------------

# Discard changes in the working directory for a specific file
git checkout -- <file_name>

# Undo the last commit and keep changes staged
git reset --soft HEAD^

# Undo the last commit and discard changes
git reset --hard HEAD^

Branch Comparison:
------------------

# Show changes between two branches
git diff <branch1>..<branch2>

Reviewing Remote Changes:
-------------------------

# Fetch changes from the remote repository (without merging)
git fetch

# Show changes between your local branch and the remote branch (after fetching)
git diff <remote_name>/<branch_name>

# Review changes in the remote repository
git log <remote_name>/<branch_name>

Pulling Remote Changes:
-----------------------

# Pull and merge changes from the remote repository
git pull <remote_name> <branch_name>

# Pull and rebase changes from the remote repository (maintains a linear history)
git pull --rebase <remote_name> <branch_name>

```
---------------------------
6. Tagging known commits:
---------------------------
```sh

Tagging a Specific Commit:
--------------------------

# List all existing tags
git tag

# Create an annotated tag for a specific commit with a message
git tag -a <tag_name> <commit_hash> -m "Tag message"

# Create a lightweight tag for a specific commit (no message)
git tag <tag_name> <commit_hash>

# Example: Create an annotated tag for commit with hash "abcdef12345" with a message
git tag -a v1.0.0 abcdef12345 -m "Version 1.0.0 release"

Pushing Tags to Remote Repository:
----------------------------------

# Push a specific tag to the remote repository
git push <remote_name> <tag_name>

# Push all tags to the remote repository
git push <remote_name> --tags

Deleting Tags:
--------------

# Delete a local tag
git tag -d <tag_name>

# Delete a remote tag
git push <remote_name> --delete <tag_name>

# Example: Delete a local and remote tag named "v1.0.0"
git tag -d v1.0.0
git push origin --delete v1.0.0
```

---------------------------
7. Reverting changes:
---------------------------
```sh

Undoing Uncommitted Changes:
---------------------------

# Discard all changes in the working directory for a specific file
git checkout -- <file_name>

# Discard all changes in the working directory for all files (Caution: Use with care!)
git reset --hard HEAD

Undoing Committed Changes:
-------------------------

# Revert the last commit (creates a new commit that undoes the changes)
git revert HEAD

# Revert a specific commit (creates a new commit that undoes the changes introduced by the commit)
git revert <commit_hash>

# Revert a range of commits (creates new commits to undo changes in the specified range)
git revert <commit_hash1>..<commit_hash2>

Resetting Changes (Use with Caution!):
--------------------------------------

# Reset the staging area to match the most recent commit, but keep the changes in the working directory
git reset --soft HEAD^

# Reset the staging area and the working directory to match the most recent commit
git reset --hard HEAD^

# Reset the staging area and the working directory to match a specific commit
git reset --hard <commit_hash>

Recovering Lost Commits (Useful for accidentally deleted commits):
-----------------------------------------------------------------

# Find the hash of lost commit using git reflog
git reflog

# Reset to the lost commit using the hash found in the reflog
git reset --hard <lost_commit_hash>

Recovering Deleted Files:
-------------------------

# Restore a deleted file from the most recent commit
git checkout <file_name>

# Restore a deleted file from a specific commit
git checkout <commit_hash> -- <file_name>

# Find the commit that deleted the file using git log with -- <file_name>
git log -- <file_name>

```

---------------------------
8. Synchronizing Repository:
---------------------------

```sh

Pulling Remote Changes:
-----------------------

# Pull and merge changes from the remote repository (fetch + merge)
git pull <remote_name> <branch_name>

# Pull and rebase changes from the remote repository (fetch + rebase)
git pull --rebase <remote_name> <branch_name>

Pushing Local Changes:
----------------------

# Push changes from the local branch to the remote branch
git push <remote_name> <branch_name>

# Push changes to a new branch on the remote repository
git push -u <remote_name> <local_branch_name>:<remote_branch_name>

# Push changes to all remote branches (only if they already exist on the remote)
git push --all <remote_name>

Viewing Remote Repositories:
---------------------------

# List all remote repositories and their URLs
git remote -v

Adding and Removing Remotes:
----------------------------

# Add a remote repository with a name and URL
git remote add <remote_name> <repository_url>

# Remove a remote repository
git remote remove <remote_name>

# Rename a remote repository
git remote rename <old_remote_name> <new_remote_name>

Viewing Branch Tracking:
------------------------

# Show local branches and their tracking branches
git branch -vv

# Show the remote tracking branch of a local branch
git rev-parse --abbrev-ref <local_branch_name>@{upstream}

Fetching Changes:
-----------------

# Fetch changes from the remote repository (without merging)
git fetch <remote_name>

# Fetch all remote branches (including new branches)
git fetch --all

Merging Remote Branches (Advanced):
------------------------------------

# Merge changes from a remote branch into the current branch
git merge <remote_name>/<remote_branch_name>

# Merge changes from a specific commit in a remote branch into the current branch
git cherry-pick <remote_name>/<commit_hash>

# Merge changes from a specific pull request in a remote repository (GitHub)
git fetch <remote_name> pull/<pull_request_number>/head:<new_local_branch>
git checkout <new_local_branch>
git merge <remote_name>/<remote_branch_name>

```

