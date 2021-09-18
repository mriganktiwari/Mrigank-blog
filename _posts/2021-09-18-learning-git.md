---
toc: true
layout: post
description: My attempt to get comfortable with Git.
categories: [markdown]
title: "Get good at Git!"
---

## Intro

I have been always felt tormented while using Git when working with teams or even alone. This below comic from xkcd aptly summarizes my experience with Git.

![]({{ site.baseurl }}/images/learning_git/git_xkcd.png "credit: xkcd")

To finally get comfortable, and efficiently use Git, I went through this lecture(link) from **Missing semester** course. Trying to summarize and demnstrate my learnings. Recommend this [video](https://missing.csail.mit.edu/2020/version-control/) and lecture notes for detailed walkthrough.

## Data model
    1. Terminology:
        - blob - a file (which is a bunch of bytes) is called a blob 
        - tree - a directory is called a tree, it maps names to blobs or treees
        ![]({{ site.baseurl }}/images/learning_git/blob_tree.png "credit: ./missing-semester")
    2. DAC:
        - Each snapshot in git refers to a set of 'parents' (snapshots that preceded it).
            ![]({{ site.baseurl }}/images/learning_git/dac_snapshots.png "credit: xkcd")
        - A snapshot might descend from multiple parents (due to merging)
            ![]({{ site.baseurl }}/images/learning_git/dac_snapshots_merging.png "credit: xkcd")
    