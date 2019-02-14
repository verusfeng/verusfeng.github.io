---
layout: post
title: 在github page更新
tags: blog
category: 指引
date: 2018-05-16 
descriptions: 使用的是其他jekyll主题
---


在钻完牛角尖，耗费一大段时间捏出了主站之后，自己仍然觉得不够好。还打算换其他主题，例如node.js等在本地编译好，再上传github的。

还是觉得太麻烦，又要装环境，又要装软件。再弄下去怕不是又要浪费很多时间在这里。

## Description

使用jekyll主题，fork别人的模版修改，图标什么的也不改了，不想在电脑装软件。


## Update log

- Use [TeXt Theme](https://github.com/kitian616/jekyll-TeXt-theme). Powered by [Jekyll](http://jekyllrb.com/) 

- 更改摘要显示模式为html

- 增加阅读数统计（好像不怎么奏效，没自增的样子）
    - 随便改了下，好像又有点作用了，搞不懂这东西。
    - google Chrom 和safari(手机)就没自增。360浏览器就有。

- 添加disqus，需要代理才能连接上，最后还是取消了。

### 背景

- 更改首页背景图，原先的背景为本地文件。想更改为网络图片。Unsplash上有很多可用的高清大图。
- 我想的是，每次打开首页，背景都是不同的图片，会改变。但是对于图片地址固定之后，不知道如何让图片每次都不一样.(undone)

- 通过修改CSS可以让图片以不同的方式显示。

> 链接图片文件太大导致页面加载过慢。

#### 原图


CSS属性为：



    #fullscreen {
        z-index: -999; 
        min-height: 100%;     /*    这个最小高度100%， 意思应该是拉伸*/  
        min-width: 1024px;    /*    最小宽度，1024个像素   */
        width: 100%;          
        height: auto;
        position: fixed;
        top: 0;
        left: 0;
    }




#### Unsplash图片


修改CSS属性为:

```
#setfull { 
    z-index: -999;
    min-height: 100%;
    min-width: 1024px;
    width: 100%;
    height: 100%;   /* 高度不自动，拉伸，Unsplash图片过大，拉伸为适合屏幕 -- 100% | auto | 1024px 数值可变 */
    position: fixed;
    top: 0;
    left: 0;
}

```

#### 一堆问题

为了更改背景，从Unsplash找了一张图片的源链接，大概有7M的大小，替换后发现图片太大，加载慢，又换了回来。
换为原图，岂不是白做了，改！就把新图传到仓库，从文件引用。提交，OK。
把这次替换写进blog里面，记录的时候，又想添加两张缩略图，就把原repository里的github里图片链接加一张，外链一张，提交后，发现图片没显示，不止如此，连post的md文件也没更新。
没更新哦，是不是哪里写错了？才出问题！
瞎猜想，想着是不是外链链接有问题？是不是必须要像\*.jpg带后缀的链接才行？
又搞了一阵，把图片添加进仓库文件夹，想着从文件路径显示会不会就没问题了，提交了，还是那样，不行。

看repository的时候，从github中repository的setting里，发现有文件报错，\_config.yml是我在之前修改的时候，看到yml文件有一个项目是exclude，就是不包含，想着不包含就是不需要，那就删除了，虽然有意识到删除了原文件，那yml的item也要删掉，但是还是粗心了，事情做了一半，文件删了，item没注释掉，导致报错。

#### 总结

不懂网页的知识，就靠瞎调，瞎蒙在做。还是不够高效。

既然要用jekyll，那基础必须仔细过一遍。 



