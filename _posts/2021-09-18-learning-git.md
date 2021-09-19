---
toc: true
layout: post
description: My attempt to get comfortable with Git.
categories: [git, github, linux]
title: "Get good at Git!"
---

## Intro

I have been always felt tormented while using Git when working with teams or even alone. This below comic from xkcd aptly summarizes my experience with Git.

![]({{ site.baseurl }}/images/learning_git/git_xkcd.png "credit: xkcd")

To finally get comfortable, and efficiently use Git, I went through this lecture(link) from **Missing semester** course. Trying to summarize and demnstrate my learnings. Recommend this [video](https://missing.csail.mit.edu/2020/version-control/) and lecture notes for detailed walkthrough.

## Data model

#### Terminology:
- **blob** - a file (which is a bunch of bytes) is called a blob 
- **tree** - a directory is called a tree, it maps names to blobs or treees
- **commits** - snapshots are called commits.
    ![]({{ site.baseurl }}/images/learning_git/blob_tree.png "credit: ./missing-semester")

#### DAG (directed acyclic graph):
- Each snapshot in git refers to a set of 'parents' (snapshots that preceded it).
    ![]({{ site.baseurl }}/images/learning_git/dac_snapshots.png "credit: xkcd")
- A snapshot might descend from multiple parents (due to merging)
    ![]({{ site.baseurl }}/images/learning_git/dac_snapshots_merging.png "credit: xkcd")
- The arrow points to the parent of each commit
- Commits are immutable

## Command line

#### Basics
- ```git help <command>```: get help for a git command
- ```git init```: creates a new git repo, with data stored in the .git directory
- ```git status```: tells you what’s going on
- ```git add <filename>```: adds files to staging area
- ```git commit```: creates a new commit
    - Write [good commit messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)!
    - Even more reasons to write [good commit messages](https://chris.beams.io/posts/git-commit/)!
    - ```git commit -a```: commits all already tracked files by git without explicitly adding
- ```git log```: shows a flattened log of history
- ```git log --all --graph --decorate```: visualizes history as a DAG
- ```git diff <filename>```: show changes you made relative to the staging area
- ```git diff <revision> <filename>```: shows differences in a file between snapshots
- ```git checkout <revision>```: updates HEAD and current branch
    - move around in your version history
    - it not just moves you different brach names, but can also move you with hash ids
    - essentially it moves **HEAD** around
    - ```
        (base) ~/code/Mrigank-blog/images/learning_git on master
        $ git log --all --graph --decorate
        * commit 37f4256ef34c48179683448a6ae7cccac42098cc (HEAD -> master, origin/master, origin/HEAD)
        | Author: mriganktiwari <tiwarimrigank2@gmail.com>
        | Date:   Sun Sep 19 07:01:30 2021 +0530
        |
        |     pushing a change for git commit -a to test the same feature
        |
        * commit 29cfcf12e1c78d4def94ffb752966b961176ac4a
        | Author: mriganktiwari <tiwarimrigank2@gmail.com>
        | Date:   Sat Sep 18 22:54:34 2021 +0530
        |
        |     more git commands added
        |
        * commit a82dba6861f89136758bbda480f030292e9543ae
        | Author: mriganktiwari <tiwarimrigank2@gmail.com>
        | Date:   Sat Sep 18 22:45:12 2021 +0530
        |
        |     Add basic git commands
        ```
    - Let's move our HEAD to <commit a82dba6861f89136758bbda480f030292e9543ae>
        ```
        (base) ~/code/Mrigank-blog/images/learning_git on master
        $ git checkout a82dba68
        Note: checking out 'a82dba68'.

        You are in 'detached HEAD' state. You can look around, make experimental
        changes and commit them, and you can discard any commits you make in this
        state without impacting any branches by performing another checkout.

        If you want to create a new branch to retain commits you create, you may
        do so (now or later) by using -b with the checkout command again. Example:

        git checkout -b <new-branch-name>

        HEAD is now at a82dba6 Add basic git commands
        ```
    - Now if we see git log (the decorated version) - HEAD is moved to the desired commit (snapshot) with hash key (that too not complete hash is required).
        ```
        (base) ~/code/Mrigank-blog/images/learning_git on (HEAD detached at a82dba6)
        $ git log --all --graph --decorate
        * commit 37f4256ef34c48179683448a6ae7cccac42098cc (origin/master, origin/HEAD, master)
        | Author: mriganktiwari <tiwarimrigank2@gmail.com>
        | Date:   Sun Sep 19 07:01:30 2021 +0530
        |
        |     pushing a change for git commit -a to test the same feature
        |
        * commit 29cfcf12e1c78d4def94ffb752966b961176ac4a
        | Author: mriganktiwari <tiwarimrigank2@gmail.com>
        | Date:   Sat Sep 18 22:54:34 2021 +0530
        |
        |     more git commands added
        |
        * commit a82dba6861f89136758bbda480f030292e9543ae (HEAD)
        | Author: mriganktiwari <tiwarimrigank2@gmail.com>
        | Date:   Sat Sep 18 22:45:12 2021 +0530
        |
        |     Add basic git commands
        ```
    
#### Branching & Merging
- ```git branch```: shows branches
- ```git branch <name>```: creates a branch
- ```git checkout -b <name>```: creates a branch and switches to it
    - same as ```git branch <name>; git checkout <name>```
- ```git merge <revision>```: merges into current branch
- ```git mergetool```: use a fancy tool to help resolve merge conflicts
- ```git rebase```: rebase set of patches onto a new base

#### Remotes
- ```git remote```: list remotes
- ```git remote add <name> <url>```: add a remote
- ```git push <remote> <local branch>:<remote branch>```: send objects to remote, and update remote reference
- ```git branch --set-upstream-to=<remote>/<remote branch>```: set up correspondence between local and remote branch
- ```git fetch```: retrieve objects/references from a remote
- ```git pull```: same as git fetch; git merge
- ```git clone```: download repository from remote

#### Advanced git
- ```git config```: Git is [highly customizable](https://git-scm.com/docs/git-config)
- ```git clone --depth=1```: shallow clone, without entire version history
- ```git add -p```: interactive staging
- ```git rebase -i```: interactive rebasing
- ```git blame```: show who last edited which line
- ```git stash```: temporarily remove modifications to working directory
- ```git bisect```: binary search history (e.g. for regressions)
- ```.gitignore```: [specify](https://git-scm.com/docs/gitignore) intentionally untracked files to ignore