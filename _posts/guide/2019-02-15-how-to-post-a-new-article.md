---
layout: post
title: 发布指引手册
category: 指引
keywords: tutorial,post,2019
---

## 如何发布新文章

1. 指定新文章存放的目录，例如：guide文件夹，在文件夹中新建md文件

2. md文件的格式
    1. 命名需要按照<年份-月份-日期-文件名称.md>的格式创建
        - 例如：2019-02-15-how-to-post-a-new-article.md
        - 注意：文件名称要用英文命名
    2. 文件内容
        - 开头需要有格式化说明
            1. layout，指定需要的模板
            2. title，页面的标题
            3. category，侧栏的目录名称
            4. keywords，关键字
            5. tags，标签
            6. description，添加描述
        - 一般layout，title，[category, tags]这些必填
        
        - 然后就是md文件的正文了

## 如何添加图片

1. 绝对地址, 添加图片的url
    - https://avatars3.githubusercontent.com/ml/55?s=62&v=4
    - ![zube](https://avatars3.githubusercontent.com/ml/55?s=62&v=4)


2. 现对地址, 本地图片资源

    - { { site.baseurl } }/assets/img/avatar.jpg

    - ![avatar]({{ site.baseurl }}/assets/img/avatar.jpg)