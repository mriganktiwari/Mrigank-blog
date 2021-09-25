---
toc: true
layout: post
categories: [tmux, linux]
title: "Wish I knew tmux earlier"
---

# Intro

# Navigating sessions and windows

|Command | Description |
|--------|-------------|
|```tmux``` | Create new session |
|```tmux new -s <session name>``` | Create new session with "name"|
|```C-b``` - ```%``` | Open new pane on vertically |
|```C-b``` - ```"``` | Open new pane horizontally |

# Detach & attach sessions

|Command | Description |
|--------|-------------|
|```C-b``` - ```d```| Detaches the active session |
|```tmux ls``` | List the detached sessions |
|```tmux attach -t <session name>``` | Attach a session, it preserves state |
|```tmux rename-session -t <old name> <new name>``` | Rename a detached session |
|```tmux kill-session -t <session name>``` | 

# 