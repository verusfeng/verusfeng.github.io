---
layout: post
title: 软件安装SublimeText & Atom
tags: sublime,atom
category: 指引
date: 2018-05-16
modify_date: 2018-05-16
---

## 知道sublime
sublime text 是从群里获知的一款文本编辑器软件。 开始安装使用之后觉得很不错，软件包小，启动快，功能也很不错，比其他类型的编辑器要好用很多。

### 使用sublime编写markdown
同时，我也有用sublime text3 编写markdown文本，使用还可以。

### 一些问题

软件重复提示unregistered，还有在软件重复提示新版本安装。

## 获知ATOM

ATOM也是从群里知道的一款软件，开源免费。安装使用后，跟sublime差不多，用着也很好。 就是软件有100M左右。

- ATOM也可以编辑markdown

- 文件管理器

- 支持多种类型文件




## 安装使用

### sublime下载

- https://download.sublimetext.com/Sublime%20Text%20Build%203170%20Setup.exe

- %20是utf8编码中，表示空格。

- Bulid%203170表示版本的为3170，修改改版本号，可以下载历史版本的安装文件。版本号可以在官网查找。

### sublime安装

- 正常安装即可。

### sublime注册码

- for sublime version3.0 bulid 3143
- https://download.sublimetext.com/Sublime%20Text%20Build%203143%20Setup.exe

```text

—– BEGIN LICENSE —–
TwitterInc
200 User License
EA7E-890007
1D77F72E 390CDD93 4DCBA022 FAF60790
61AA12C0 A37081C5 D0316412 4584D136
94D7F7D4 95BC8C1C 527DA828 560BB037
D1EDDD8C AE7B379F 50C9D69D B35179EF
2FE898C4 8E4277A8 555CE714 E1FB0E43
D5D52613 C3D12E98 BC49967F 7652EED2
9D2D2E61 67610860 6D338B72 5CF95C69
E36B85CC 84991F19 7575D828 470A92AB
—— END LICENSE ——
```

### 修改hosts文件

- path：C:\Windows\System32\drivers\etc
- Add items list below
- 这个是把licnese验证服务器 重定向为本地localhost 127.0.0.1， 这样license不会频繁失效。

127.0.0.1 sublimetext.com

127.0.0.1 sublimehq.com

127.0.0.1 license.sublimehq.com


### 修改更新提醒

- 修改更新提示，和一些设置

Menu -> perferences -> settings -> settings for user


```markdown
{

    "font_size": 17,    // 字体大小
    "ignored_packages":
    [
    ],                  // 这里是忽视某些插件,每安装过的插件都会添加
    "update_check": false,  //取消软件更新提示

    "hot_exit": false,                  //
    "remember_open_files": false,       // 退出不记录 当前文件。
    "translate_tabs_to_spaces": true,   // tab转为空格
    "tab_size": 4,                      // tab size = 4

}
```


## markdown

- 快捷键，preview in browser

perference - key bindings - key bindings for user

```markdown

[
    { "keys": ["ctrl+shift+m"], "command": "markdown_preview", "args":   {"target": "browser", "parser":"markdown"} }
]

```




## ATOM正常安装即可

- 不需要lincense
