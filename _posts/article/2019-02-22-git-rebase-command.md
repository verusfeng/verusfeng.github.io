---
layout: post
title: Git命令rebase使用说明
category: 文章
---


# git命令rebase

- 变基命令
    - 理解不了变基的意思，就我看来，就是可以修改提交信息，让commit log可以比较工整
    - rebase可以让主分支的信息、结构清晰工整
    - 当然rebase命令，会丢弃历史记录，回溯问题会比较难。

# rebase命令的使用

- git rebase -i [start_commint] ([end_commit] 可选，没有就默认当前head

## rebase的指令

```text

# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.

```

- p or pick 使用当前的提交，即保持不变
- r or reword 更改提交的信息

- 开发过程，本地可能会有多次提交， 例如update modify 等多个commit信息
    - 可以使用rebase 中pick 和 fixup来丢弃重复的提交历史。保持log清晰。


## 使用fixed 或者 suqash 比delete好


# 在pythonanywhere发布的代码

- 是在github上建立的远端仓库

- 本地电脑关联origin remote

- 在pythonanywhere关联origin remote

- 代码都是在本地修改，推送到origin，然后在pythonanywhere拉去最新更新

- 当在本地使用rebase命令时， git push -f 强制推送覆盖
    - 在pythonanywhere使用git fetch --all 
    - 再执行git reset --hard origin/master