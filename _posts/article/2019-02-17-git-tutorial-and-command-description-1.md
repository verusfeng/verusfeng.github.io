---
layout: post
title: Git常用命令说明
category: 文章
---


0.所有git仓库都存放在本地git服务里。
0.1.地址为localhost:3000

1.本地安装git软件.

1.1.可以用命令行操作git.

1.2.设置自己的用户名和邮箱作为识别的唯一地址.

1.2.1. git config --global user.name ""
1.2.2. git config --global user.email ""

2.使用自己的git仓库
2.1.创建ssh key.  $ ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
2.2.C:\Users\username\.ssh 路径下有id_rsa.pub, 复制内容到github-> add ssh key.

2.3.使用clone命令可以复制自己的git仓库.并推送.  $git clone git_address_

3.有时候用ssh地址好像拉取不了
3.1.可以尝试用https地址拉取
3.2.https再推送的时候，会要求登录。