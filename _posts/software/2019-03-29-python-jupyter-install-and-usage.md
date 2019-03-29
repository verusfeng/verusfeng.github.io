---
layout: post
category: 软件
title: Jupyter的使用
---


## python入门学习-现状
1. 使用cmder命令行工具
2. 使用sublime编写py代码
3. 命令行运行python mycode.py就这样.
4. 虽然有装了pycharm, 但对我来说, 这牛刀太大了.

### 遇到的问题
1. py入门学习, 对一些模块使用并不是很清楚.
2. 不太熟练的编写, 经常需要多次运行py代码.
3. 在sublime 和命令行需要多次切换.

## jupyter的使用
1. 在看视频时发现的, jupyter 可以在编写的时候保存运行的变量, 同时能够获取 代码段的执行结果, 很方便.
2. 安装
    - 选择工作目录, 创建虚拟环境
    - virtualenv -p python .
    - 进入环境中, 安装jupyter
    - .\scripts\activate (windows)
    - source ./bin/activate (linux)
    - pip install jupyter

3. 本地运行jupyter服务
    - jupyter notebook
    - 会自动打开一个页面, 进入jupyter的环境.
    - 可以在这里编写了.
    - 拓展格式为ipynb, 存放在当前目录中的.
    - 支持导出. 

4. 方向键选择代码块
    - 回车, 编辑当前代码块, 代码块中换行
    - Ctrl+回车, 运行当前代码块
    - Shift + 回车, 运行当前代码块, 并跳到下一个代码块, 若不存在, 则新建代码块
    - DD 删除代码块.

