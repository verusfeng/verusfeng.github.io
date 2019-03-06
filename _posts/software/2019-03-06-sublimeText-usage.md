---
layout: post
category: 软件
title: sublime的一些使用方法
---

## sublime Text3

### 添加环境
- 由于经常使用cmder命令行模式，所以需要用sublime打开某个文件时，直接用命令打开就可以。
- 添加sublimeText3的目录地址到环境变量path中。
- 文件目录有两个执行文件exe ， sublime_text.exe和subl.exe
    - sublime_text.exe是打开软件的。
    - subl.exe是命令行模式下使用，可以跟参数例如文件名，目录名。

- 使用
    - subl 1.txt用sublimeText3打开1.txt文件
    - subl folder_name 打开文件夹，在sublime中会添加该文件夹树。
    - subl . 点是代表当前文件。 功能同上。

### 快捷键

1. ctrl+D 
    - 选择一些文件按ctrl+D可以选择文件内相同的文本。 可以一起编辑。
    - ctrl + K 跳过
    - ctrl + U 回退

2. ctrl+F
    - 查找文本，支持正则表达式

3. ctrl+P
    - 快速查找文件，在把文件夹用sublimtext打开时， 子文件夹中的文件比较多， 可以用ctrl+P快速定位文件并打开。 前提是知道文件名字。

4. ctrl+shift+P
    - set syntax 切换文件语法。

5. Enter 回车，往下插入新行
    - ctrl+shift+Enter ， 往上插入新行

6. Alt+shift+numX 分屏, 分屏数由数字决定

7. Ctrl + ←/→    进行逐词移动

8. Ctrl + Shift + ←/→    进行逐词选择

9. Ctrl + Shift + ↑/↓    移动当前行 

10. Ctrl + J  把选择的区域合并为一行, 空格隔开, 


### 新建与关闭

1. Ctrl + N 新建
2. Ctrl + W 关闭
3. Ctrl + Shift + T 恢复刚关闭的标签

### 全屏切换

1. F11
2. shift + F11

### 多重选择

1. ctrl + D 选择下一个相同文本
    - ctrl + K 跳过当前相同文本
    - ctrl + U 回退当前相同文本哦

2. ctrl + shift + L , 把选择的一片区域打散, 分为多重选择, 光标在最后  


### 跳转
1. Ctrl+P
    - 输入文件跳转到文件
    - @开头 输入symbol 跳转到symbol位置
    - #开头 输入关键字, keyword, 跳转到keyword位置
    - :开头 输入行号,跳转到行



### 插件支持

0. 打开控制台ctrl+点 点在数字1隔壁
    - 现在ctrl+shift+P 可以直接package control模块了。

1. 快捷键ctrl+shift+P
    - package control插件包管理
    - package control：install package 会列出所有插件。 输入需要的插件，回车安装。


## 就这些了
- 自己普通使用, 插件也没装几个.



 
