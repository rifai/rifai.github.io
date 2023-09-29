---
title: "Git scenario 1 : Urgent bug report"
description: You're working on a software project and are in the middle of implementing a new feature in your branch.
date: 2023-09-28
tags:
	- git
---
You're working on a software project and are in the middle of implementing a new feature in your branch. However, you receive an urgent bug report that requires your immediate attention.  
You don't want to commit your incomplete work, so you decide to use git stash to temporarily save your changes and switch to a different branch to fix the bug.

## 1. Check your current branch:
```bash
git branch
```
Output:
```bash
* feature-branch
master
```
You are currently on the **feature-branch**.

## 2. Save your changes to a stash:

```bash
git stash save "Work in progress on new feature"
```
This command stashes the changes with a descriptive message.

## 3. Check the list of stashes:
```bash
git stash list
```
Output:
```bash
stash@{0}: On feature-branch: Work in progress on new feature
```

## 4. Switch to another branch:
```bash
git checkout bug-fix-branch
```
The developer is now on the **bug-fix-branch** to address the urgent bug.

## 5. Fix the bug:
```c
// Make necessary code changes to fix the bug
```

## 6. Commit the bug fix:

```bash
git commit -m "Fixed the critical bug"
```
The bug is fixed, and the changes are committed.

## 7. Switch back to the feature branch:
```bash
git checkout feature-branch
```

The developer returns to the **feature-branch**.

## 8. Apply the stashed changes:

```bash
git stash apply stash@{0}
```
The previously stashed changes are applied to the feature-branch. The developer can continue working on the new feature from where they left off.

## 9. Check the status:

```bash
git status
```
The developer sees the unstashed changes and can proceed with feature development.
