+++
date = '2022-04-17T00:00:00Z'
draft = false
title = 'Useful Git Commands'
description = 'Git commands everyone should know'
tags = ['git', 'github', 'version-control', 'commands']
categories = ['development']
+++

# Useful Git Commands

Git is a free and open-source distributed version control system that's responsible for everything GitHub related that happens locally on your system. GitHub is a web-based platform where you can share your work with other developers and showcase your learnings.

## Git commands:
Think of it as a Marriage (our git repository) → guests (working files) → photoshoots on stage → (committing your repository)

## git config
Configures user information used across all local repositories.

Set a name that is identifiable for credit when review version history:
```bash
git config --global user.name "username"
```

Set an email address that will be associated with each history marker:
```bash
git config --global user.email "email"
```

## git init
Initializes an existing directory as Git repository (.git directory).
```bash
git init
```

## git clone
Retrieve an entire repository from a hosted location via URL:
```bash
git clone [url]
git clone --branch [url]
```

## git add
Add a file to your next commit (stage):
```bash
git add [file]
```

## git rm
Deletes the file from project and stages the removal for commit:
```bash
git rm [file]
```

## git mv
Changes an existing file path and stages the move:
```bash
git mv [existing-path] [new-path]
```

## git commit
Commits the staged contents as a new commit snapshot:
```bash
git commit -m "your commit message goes here"
```

## git branch
List, Create or Delete Branches (branches look like an acyclic graph)

List branches:
```bash
git branch
```

Create a new Branch at the current commit:
```bash
git branch [branch-name]
```

Delete a Branch:
```bash
git branch -d [branch-name]
```

## git status
Shows the paths of modified files in working directory:
```bash
git status
```

## git diff
Show changes between commits:

To see diff of what is changed, but not staged:
```bash
git diff
```

To see diff of what is staged, but not committed:
```bash
git diff --staged
```

To see diff between 2 branches:
```bash
git diff BranchA...BranchB
```

## git log
Shows the commit history for the currently active branch:
```bash
git log
```

Shows the commits on branch-A that are not on branch-B:
```bash
git log branchA..branchB
```

## git checkout
Switch Branches.

Switch to another branch and check it out into your working directory:
```bash
git checkout [branch-name]
```

Switch to another branch (create if does not exist):
```bash
git checkout -b [branch-name]
```

## git merge
For joining two or more development histories together:
```bash
git merge [branch]
```

## git fetch
Fetch branches and/or tags from one or more other repositories:
```bash
git fetch [alias]
```
You can use git fetch to know the changes done in the remote repo/branch since your last pull.

## git pull
Fetch and merge any commits from tracking remote branch:
```bash
git pull
```

## git push
For making changes in your repository:
```bash
git push origin [branch-name]
```

Transmit local branch commits to the remote repository branch:
```bash
git push [alias]
```

## git rebase
Applies any commits of current branch ahead of specified one. It is used if you need to rewrite the history of a project:
```bash
git rebase [branch-name]
```

## git revert
Reverts some existing commits:
```bash
git revert
```

## git reset
If you want to delete the commits:
```bash
git reset [hashcodeId]
```
You can get "hashcodeId" by running git log
*NOTE: the commits deleted will be in unstaged area*

Resets current HEAD to the specified state. Unstages a file while retaining the changes in working directory:
```bash
git reset [file]
```

Clears staging area, rewrite working tree from specified commit:
```bash
git reset --hard [commit]
```

## git stash
Temporarily stores modified, tracked files in order to change branches. It's used when you don't want to commit your working files but want to store temporarily.

Save modified and staged changes:
```bash
git stash
```

List StackOrder of stashed file changes:
```bash
git stash list
```

Write working from top of stash stack or to bring your temporarily stored files:
```bash
git stash pop
```

Discard the changes from top:
```bash
git stash drop
```

For deleting temporary stored, modified, tracked files:
```bash
git stash clear
```

## git remote
For adding the URL of your repository to your project:
```bash
git remote add origin [URL]
```
Remote means you're working with URLs and origin is the name of the url.

Shows all the URLs attached with your project:
```bash
git remote -v
```

## Things to keep in mind while working on other developer's open-source projects

Always make a separate branch when you working with a new feature or fixing a bug in someone's else repository:
```bash
git branch [branch-name]
```

**HEAD**: It's just a pointer that means all the commits that you've made will be added on the head (the new branch).

To check when someone else commits to main branch:
```bash
git checkout main
```

For merging your code with the main code:
```bash
git merge [branch-name]
```

For copying existing organization project:
- Use fork for that
- Clone that project in your repository:
```bash
git clone [URL]  # paste the URL of the forked project
```

**Upstream URL**: it is the URL from where you've forked the project:
```bash
git remote add upstream [URL]
```

To make changes in the upstream (original project):
- Make a new branch:
```bash
git branch [new-branch]
git checkout [new-branch]  # this will change the header to new-branch
```

For making changes in the original project of the organization we use **pull request**.

**NOTE**: 1 Branch → 1 pull request
We always make a new branch to make it easier to review our commit to the original project.

To force push the changes:
```bash
git push origin [branch-name] -f
```

To make changes that you've previously made in the original project to be shown in your forked project too:
```bash
git checkout main
git fetch --all --prune  # prune means the deleted commits will also be fetched
```

To reset the main branch of my origin to main branch of upstream:
```bash
git reset --hard upstream/main
git push origin main
```

**NOTE**: That's how you keep in sync with the main branch or you can directly fetch upstream in your GitHub.
