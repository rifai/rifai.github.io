---
title: Frequently used git command
description: Here's a list of Git commands I use frequently, as well as some less common ones
date: 2023-09-28
tags:
	- git
---
While using a GUI client for Git is helpful and user-friendly, the command-line interface, although more complex, offers greater power and speed.  

I've written this post to serve as a handy reference, eliminating the need to repeatedly search for specific commands on Google or Stack Overflow.  

Here's a list of Git commands I use frequently, as well as some less common ones

## Init
Initializes a new Git repository in current directory.
```bash
git init 
```

## Clone 
Clone a remote Git repository on local computer
```bash
git clone https://repo-url.com 
```

## Status
Displays the current status of the working directory
```bash
git status
```

## Add 
Stages changes in the working directory for the next commit
```bash
git add <file1> <file2> <file3>
git add .  
```

## Commit 
Records changes in a new commit along with a descriptive message
```bash
git commit –m "<message here>"
```

## Stash
Temporarily saves changes for later use.
```bash
git stash save -m "<message here>"
```
Applies the changes from a specific stash back to working directory. The stash index number (e.g., stash@{0}) identifies the stash to apply. If not specified, it applies the most recent one.
```bash
git stash apply [stash@{n}]
```
Applies and removes the changes from a specific stash. If not specified, it applies and removes the most recent stash.
```bash
git stash pop [stash@{n}]
```
Deletes a specific stash, permanently removing it.
```bash
git stash drop [stash@{n}]: 
```
## Fetch
Downloads changes from a remote repository without merging.
```bash
git fetch
```
## Pull
Fetches and merges changes from a remote repository into the current branch.
```bash
git pull
```
## Push
Sends local commits to a remote repository to share changes.
```bash
git push
```

To be continued ...