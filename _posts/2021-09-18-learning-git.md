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
1. Terminology:
    - **blob** - a file (which is a bunch of bytes) is called a blob 
    - **tree** - a directory is called a tree, it maps names to blobs or treees
        ![]({{ site.baseurl }}/images/learning_git/blob_tree.png "credit: ./missing-semester")
    - **commits** - snapshots are called commits.
2. DAG (directed acyclic graph):
    - Each snapshot in git refers to a set of 'parents' (snapshots that preceded it).
        ![]({{ site.baseurl }}/images/learning_git/dac_snapshots.png "credit: xkcd")
    - A snapshot might descend from multiple parents (due to merging)
        ![]({{ site.baseurl }}/images/learning_git/dac_snapshots_merging.png "credit: xkcd")
    - The arrow points to the parent of each commit
    - Commits are immutable

## Command line

### Basics
- ```git help <command>```: get help for a git command
- ```git init```: creates a new git repo, with data stored in the .git directory
- ```git status```: tells you what’s going on
- ```git add <filename>```: adds files to staging area
- ```git commit```: creates a new commit
    Write [good commit messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)!
    Even more reasons to write [good commit messages](https://chris.beams.io/posts/git-commit/)!
- ```git log```: shows a flattened log of history
- ```git log --all --graph --decorate```: visualizes history as a DAG
- ```git diff <filename>```: show changes you made relative to the staging area
- ```git diff <revision> <filename>```: shows differences in a file between snapshots
- ```git checkout <revision>```: updates HEAD and current branch