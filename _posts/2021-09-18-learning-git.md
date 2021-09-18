---
toc: true
layout: post
description: My attempt to get comfortable with Git.
categories: [markdown]
title: "Get good at Git!"
---

# Intro

I have been always felt tormented while using Git when working with teams or even alone. This below comic from xkcd aptly summarizes my experience with Git.

![]({{ site.baseurl }}/images/learning_git/git_xkcd.png "credit: xkcd")

To finally get comfortable, and efficiently use Git, I went through this lecture(link) from **Missing semester** course. Trying to summarize and demnstrate my learnings. Recommend this [video](https://missing.csail.mit.edu/2020/version-control/) and lecture notes for detailed walkthrough.

## Git data model
1. Terminology:
- blob - a file (which is a bunch of bytes) is called a blob 
- tree - a directory is called a tree, it maps names to blobs or treees
![]({{ site.baseurl }}/images/learning_git/blob_tree.png "credit: ./missing-semester")
2. DAC
- 