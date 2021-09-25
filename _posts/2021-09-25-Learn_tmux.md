---
toc: true
layout: post
categories: [tmux, linux]
title: "Wish I knew tmux earlier"
---

## Intro (```man tmux```)
- ```tmux``` is a terminal multiplexer
- it enables a number of terminals to be created, accessed, and controlled from a single screen.
- ```tmux``` may be detached from a screen and continue running in the background, then later reattached.

## Sessions

|Command | Description |
|--------|-------------|
|```tmux``` | Create new session |
|```tmux new -s <session name>``` | Create new session with "name"|

## Windows
- Equivalent to tabs in editors, visually seperate part of the same session

|Command | Description |
|--------|-------------|
|```<C-b>``` - ```c``` | Creates new window |
|```<C-d>``` | Close a window |
|```<C-b>``` - ```N``` | Go to Nth window |
|```<C-b>``` - ```p```| Go to previous window |
|```<C-b>``` - ```n```| Go to next window |
|```<C-b>``` - ```,```| Rename current window |
|```<C-b>``` - ```w```| List current windows |

## Panes
- Panes let you have multiple shells in the same display

|Command | Description |
|--------|-------------|
|```<C-b>``` - ```%``` | Open new pane on vertically |
|```<C-b>``` - ```"``` | Open new pane horizontally |
|```<C-b>``` - ```<arrow keys>``` | Jump to desired pane |
|```<C-b>``` - ```z``` | Toggle zoom for current pane |
|```<C-b>``` - ```[``` | Start scrollback. You can then press ```<space>``` to start a selection and ```<enter>``` to copy that selection |
|```<C-b>``` - ```<space>``` | Cycle through pane arrangements |


## Detach & attach sessions

|Command | Description |
|--------|-------------|
|```<C-b>``` - ```d```| Detaches the current session |
|```tmux ls``` | List the detached sessions |
|```tmux attach a``` | Attaches the last session |
|```tmux attach -t <session name>``` | Attach a session, it preserves state |
|```tmux rename-session -t <old name> <new name>``` | Rename a detached session |
|```tmux kill-session -t <session name>``` | 
