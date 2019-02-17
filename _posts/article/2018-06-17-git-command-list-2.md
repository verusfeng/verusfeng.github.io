---
layout: post
title: 常用命令列表2-git
category: 文章
---

## 系统环境windows
1. 软件cmder
2. git



## git常用命令

> 当对一个命令参数不清楚时，使用 git [command] -help


### git基础操作

0. git clone address --depth=1
    - 克隆深度设置，克隆到最近一次提交

1. $git init
    - initial a git local repository 
    - 初始化一个本地仓库

2. $git add test.txt
    - add a file < test.txt > 
    - 把单个文件 < test.txt > 添加到index

3. git add -A . 
    - 添加所有更改到暂存区

4. $git commit -m "message log"
    - 提交所有修改到本地仓库，并添加log提交信息

5. $git diff
    - 比较当前所有文件与上一版本
    - $git diff HEAD -- readme.txt
        - 比较单个文件

6. $git status
    - 查看仓库文件状态

7. $git push -u origin master
    - 推送到服务器

8. git pull
    - 从服务器拉取最新到本地

9. git log
    - 查看提交日记

10. git reflog
    - 查看操作日记

### git回滚撤销修改

1. $git checkout -- readme.txt
    - 恢复某个修改文件，未存入暂存区的
    - 就是把状态恢复正常，删除的文件也能恢复
    
2. git rm --cached readme.txt
    - 文件已经添加入暂存区的
    - 清除暂存区，指定文件的缓存

> 当对一个命令参数不清楚时，使用 git [command] -help

3. $git reset --hard HEAD~2
    - 回滚两个版本，强制，不保留更改
    - git reset --mixed HEAD~2
    - 回滚两个版本，保留更改

4. $git reset HEAD file.txt
    - 恢复某个修改文件，已删除文件

### git分支
1. $git branch <name>
    - 创建分支<name>

2. $git checkout <name>
    - 切换分支

3. $git checkout -b <name>
    - 切换分支，不存在就创建

4. $git branch -d <name>
    - 删除分支

5. $git merge <name>
    - 合并分支，把分支<name> 合并到当前分支.
    - 分支<name>工作做完，切换到master，merge<name> 把工作分支合并到master

### git标签

- 版本发布可以打tag

$git tag v1.2

$git tag v1.0 version_ID

$git show v1.2

$git tag -a v1.0 -m "description for tag" version_ID

$git tag -d v1.1

$git push origin v1.1

$git push origin --tags

$git check-ignore

## git配置config

### git用户设置user

git config --global user.name  " "
git config --global user.email " "

### git别名设置alias

$git config --global alias.lg "log --pretty=oneline --graph --abbrev-commit"
    - git lg 一行显示

$git config --global alias.addall "add -A ."
    - git addall 添加所有文件.

### git代理设置proxy

git config --global https.proxy localhost:1080
git config --global http.proxy localhost:1080


