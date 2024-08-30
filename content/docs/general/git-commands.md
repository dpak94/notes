---
type: "docs"
title: Git
url: "/docs/general/git/"
---

# Git

**Git** is the free and open source distributed **version control system** that's responsible for everything **GitHub** related that happens locally on your computer.

## Installation

- [**Windows**](https://windows.github.com)
- [**Mac**](https://mac.github.com)
- [**All Platforms**](https://git-scm.com)

## Configuring User Information

Configuring User Information to be used across all repositories

| **Command**                                            | **Function**                                                           |
| ------------------------------------------------------ | ---------------------------------------------------------------------- |
| `git config --global user.name “[firstname lastname]”` | Set a name that is identifiable for credit when review version history |
| `git config --global user.email “[valid-email]”`       | Set an email address that will be associated with each history marker  |
| `git config --global color.ui auto`                    | Set automatic command line coloring for Git for easy reviewing         |

## Setup & Initializing

| **Command**       | **Function**                                                 |
| ----------------- | ------------------------------------------------------------ |
| `git init`        | Initialize an existing directory as a Git repository         |
| `git clone [url]` | Retrieve an entire repository from a hosted location via URL |

## Stage & Snapshot

Working with snapshots and the Git staging area

| **Command**                                | **Function**                                                          |
| ------------------------------------------ | --------------------------------------------------------------------- |
| `git status`                               | Show modified files in working directory, staged for your next commit |
| `git add fileName`                         | Add a file as it looks now to your next commit (stage)                |
| `git reset fileName`                       | Unstage a file while retaining the changes in working directory       |
| `git diff`                                 | Difference of what is changed but not staged                          |
| `git diff --staged`                        | Difference of what is staged but not yet commited                     |
| `git commit -m “[descriptive message]”`    | Commit your staged content as a new commit snapshot                   |
| `git commit -a -m “[descriptive message]”` | Commit your content without staging                                   |

## Branch & Merge

Isolating work in branches, changing context, and integrating changes

| **Command**             | **Function**                                                                 |
| ----------------------- | ---------------------------------------------------------------------------- |
| `git branch`            | List your branches. a **\*** will appear next to the currently active branch |
| `git branch branchName` | Create a new branch at the current commit                                    |
| `git checkout`          | Switch to another branch and check it out into your working directory        |
| `git merge branchName`  | Merge the specified branch’s history into the current one                    |
| `git log`               | Show all commits in the current branch’s history                             |
| `git log --online`      | Show all commits with only commit messages                                   |
| `git log -p`            | Show all commits along with changes                                          |

## Inspect & Compare

Examining logs, diffs and object information

| **Command**                  | **Function**                                               |
| ---------------------------- | ---------------------------------------------------------- |
| `git log`                    | Show the commit history for the currently active branch    |
| `git log branchB..branchA`   | Show the commits on branchA that are not on branchB        |
| `git log --follow [file]`    | Show the commits that changed file, even across renames    |
| `git diff branchB...branchA` | Show the diff of what is in branchA that is not in branchB |
| `git show [SHA]`             | Show any object in Git in human-readable format            |

## Share & Update

Retrieving updates from another repository and updating local repos

| **Command**                    | **Function**                                                          |
| ------------------------------ | --------------------------------------------------------------------- |
| `git remote add [alias] [url]` | Add a git URL as an alias                                             |
| `git fetch [alias]`            | Fetch down all the branches from that Git remote                      |
| `git merge [alias]/[branch]`   | Merge a remote branch into your current branch to bring it up to date |
| `git push [alias] [branch]`    | Transmit local branch commits to the remote repository branch         |
| `git pull`                     | Fetch and merge any commits from the tracking remote branch           |

## Tracking Path Changes

Versioning file removes and path changes

| **Command**                         | **Function**                                                  |
| ----------------------------------- | ------------------------------------------------------------- |
| `git rm [file]`                     | Delete the file from project and stage the removal for commit |
| `git mv [existing-path] [new-path]` | Change an existing file path and stage the move               |
| `git log --stat -M`                 | Show all commit logs with indication of any paths that moved  |

## Rewrite History

Rewriting branches, updating commits and clearing history

| **Command**                 | **Function**                                                   |
| --------------------------- | -------------------------------------------------------------- |
| `git rebase [branch]`       | Apply any commits of current branch ahead of specified one     |
| `git reset --hard [commit]` | Clear staging area, rewrite working tree from specified commit |

## Temporary Commits

Temporarily store modified, tracked files in order to change branches

| **Command**      | **Function**                                |
| ---------------- | ------------------------------------------- |
| `git stash`      | Save modified and staged changes            |
| `git stash list` | List stack-order of stashed file changes    |
| `git stash pop`  | Write working from top of stash stack       |
| `git stash drop` | Discard the changes from top of stash stack |

## Ignoring Patterns

Preventing unintentional staging or commiting of files

```sh
logs/
*.notes
pattern*/
```

Save a file with desired paterns as **.gitignore** with either direct string matches or wildcard globs

```sh
git config --global core.excludesfile [file]
```

System wide ignore patern for all local repositories

## SSH Key Generation

Generating SSH Key for local Git Bash to pull remote repos and adding the generated key to the remote repo account.

1. Open **Git Bash**

2. Paste the text below :

   `ssh-keygen -t rsa -b 4096 -C "dpak@tuta.io"`

3. This creates a new SSH key, using the provided email as a label

   > Generating public/private rsa key pair.

4. When you get the below prompt :

   > Enter a file in which to save the key (/c/Users/ranger/.ssh/id_rsa): [Press Enter]

5. The public key will be stored in `C:\Users\ranger\.ssh` as **id_rsa.pub** file. Opening this file with notepad or VSCode gives the **SSH key**. This key can be added to GitHub or GitBucket on their website.

---

## 7 Golden Rules for Git Commit

1. Separate the subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain _what_ and _why_ vs _how_
