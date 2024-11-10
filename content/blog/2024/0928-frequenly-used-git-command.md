---
title: Git command to remove branches without remote upstream   
description: Git command to remove branches without remote upstream
date: 2024-11-10
tags:
	- git
---

If you want to delete local branches that no longer have an upstream branch on the remote, you can use the following Git command 

```bash
#!/bin/bash

# Fetch the latest information about remote branches
git fetch --all --prune

# List all local branches
for branch in $(git branch --format='%(refname:short)'); do
    # Check if the branch has a corresponding remote branch
    if ! git show-ref --verify --quiet refs/remotes/origin/"$branch"; then
        echo "Deleting branch: $branch"
        git branch -d "$branch"
    fi
done
```