---
layout: post
category: 文章
title: Git安装与使用
---


# SVN and Git

- 工作上使用的编程语言主要是C语言，单片机嵌入式的编程。第一次接触代码管理软件是工作需要装的SVN。

- 后面了解到Git。

- 使用git的好处，可多人协助，可创建分支，流程清晰。

# 安装Git

### Linux 
- sudo apt-get install git

### Windows
- 下载安装包，安装
- configuration设置用户名和邮箱
    - $ git config --global user.name "Your Name"
    - $ git config --global user.email "email@example.com"

- Git是分布式版本控制系统，所以，每个机器都必须表明自己的身份：你的名字和Email地址。

- 如果系统有安装git了使用
    - git clone https://github.com/git/git 获取最新git版本

# Git and Github

- 本地已经安装git，可以创建仓库管理代码。
- 在服务器上建立远程仓库，分布式的特点。
- 本地仓库与远程仓库的通讯链接需要SSH key

## 创建SSH key

- 打开Shell（Windows下打开Git Bash），创建SSH Key

- $ ssh-keygen -t rsa -C "youremail@example.com"
- 找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
- 把公钥id_rsa.pub的内容复制到github的ssh中。
- GitHub需要识别出你推送的提交确实是你推送的，SSH就算是认证了。

## 本地git仓库与github服务器的git仓库关联

- 远程仓库建立空repository。
- $ git remote add origin git@github.com:username/gitLog.git

## 从远程仓库clone到本地

- 本地为空文件夹。
- git clone git@github.com:username/gitLog
 