---
layout: post
title: Git常用命令说明
category: 文章
---

## 使用git

### 本地安装gogs

0. 所有git仓库都存放在本地git服务里。
	1. 地址为localhost:3000

1. 本地安装git软件.
	1. 可以用命令行操作git.
	2. 设置自己的用户名和邮箱作为识别的唯一地址.
		1. git config --global user.name ""
		2. git config --global user.email ""

2. 使用自己的git仓库
	1. 创建ssh key.  $ ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
	2. C:\Users\username\.ssh 路径下有id_rsa.pub, 复制内容到github-> add ssh key.
	3. 使用clone命令可以复制自己的git仓库.并推送.  $git clone git_address_

3. 有时候用ssh地址好像拉取不了
	1. 可以尝试用https地址拉取
	2. https再推送的时候，会要求登录。


### 使用服务器git仓库

0. 选择git服务提供商
    1. github
    2. bitbucket
    3. gitee
    4. 等等

1. 注册，创建仓库
    1. 在创建仓库时，会有.gitignore文件和readme.md文件可选生成，根据需要选择
    2. 开源协议选择，根据情况选择
    3. 仓库可以公开，也可以不公开

2. 本地使用git clone远端仓库,有两种地址克隆仓库
    1. git clone ssh_address, 需要有ssh-key 支持
    2. git clone https_address




