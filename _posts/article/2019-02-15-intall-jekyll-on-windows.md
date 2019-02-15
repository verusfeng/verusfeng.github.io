---
layout: post
title: windows安装jekyll
category: 文章
---

# 需求

- 在github page 上部署了静态blog，基于jekyll的

- 需要在本地上，调好网页页面。那么需要安装jekyll在本地上，使用的又是windows



## 下载软件

0. msys2下载安装(先下载安装这个)
    - 地址[link](http://repo.msys2.org/distrib/x86_64/)
    - 选择对应系统的版本

1. Ruby下载安装
    - 地址[link](https://rubyinstaller.org/downloads/)
    - 安装完成会弹出窗口
    - ![1]({{ site.baseurl }}/assets/img/article/ruby-install-1.jpg)
    - 如果安装失败，重新从命令行执行ridk install选择3
    - ![2]({{ site.baseurl }}/assets/img/article/ruby-install-2.jpg)

2. 再打开一个新的命令行窗口（cmd/powershell/bash/msys2 都行），输入以下命令安装 jekyll
    - gem install jekyll bundler
    - ![3]({{ site.baseurl }}/assets/img/article/ruby-install-3.jpg)


## 进入blog所在目录

1. bundle install 
2. jekyll serve
    - 如果出错， 需要更新依赖包，bundle update 执行一下

3. 出现一个错误，提示在命令前面加bundle exec jekyll serve 再执行，可以了。
    - 在本地4000端口运行


----
