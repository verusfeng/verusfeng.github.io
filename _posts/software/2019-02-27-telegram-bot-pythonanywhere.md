---
layout: post
category: 软件
title: 在pythonanywhere部署Telegram机器人
---


### Telegram

- 这软件用着确实不错, 加上开放的机器人API, 让telegram存在多种多样的功能机器人. 非常方便. 

### 如何制作自己的机器人

#### 使用bot api

1. 从@botFather处新建一个机器人, 会有一个机器人token, 开发bot会用到.
2. 简单利用机器人api收发信息
    1. ```https://api.telegram.org/bot<token>/getupdates```
    2. ```https://api.telegram.org/bot<token>/sendmessage?chat_id=<user_id>&text=<message>```
    3. 把这些放在浏览器中, 向这些地址发送请求, 会实现简单的收发信息. 返回的是json数据.

3. 使用python模拟http请求api,来收发信息.
    1. python的requests库, 向指定url(GET,POST请求),可以获得返回数据
    2. python处理返回的json数据包.
    3. 如果是在本地电脑, 需要增加requests的代理参数porxies=dict({'https':'host:port'})

#### 使用webhook

1. 什么是webhook
    - 我在这里的理解是, 当有信息发送给bot, telegram服务器就把这些数据post到你设置好的webhook上, 让webhook的程序做处理. 
2. 设置weibhook,需要token
    - ```https://api.telegram.org/bot<token>/setwebhook?url=<webhoook_address>```

3. 制作机器人bot
    0. 使用flask, 安装flask , pip install flask
    1. 使用第三方库telebot, 安装pip install telebot pytelegrambotapi

```python

#!coding:utf8

from flask import *
import telebot

bot = telebot.TeleBot(<your_token>)
bot.remove_webhook()
bot.set_webhook(<your_webhook_url>)

app = Flask(__name__)  # flask app
@route('/')
def index():
    return ("index page")

@route("/"+webhook,methods=['POST'])
def webhook():
    # code here
    return 'ok',200

@bot.message_handler(content_types=['text'])
def echo(m): 
    bot.send_message(m.chat.id, m.text)

bot.polling()



```

### Pythonanywhere

1. 新建一个flask的应用

2. 删除原来的flask_app.py

3. 新建bot.py，拷贝进代码保存

4. 编辑wsgi.py文件
    - 更改应用名字为bot，原来为flask_app
    - 刷新网页应用

5. 查看error log 看有没有错误

```python
# This file contains the WSGI configuration required to serve up your
# web application at http://<your-username>.pythonanywhere.com/
# It works by setting the variable 'application' to a WSGI handler of some
# description.
#
# The below has been auto-generated for your Flask project

import sys

# add your project directory to the sys.path
project_home = u'/home/vonvin/mysite'
if project_home not in sys.path:
    sys.path = [project_home] + sys.path

# import flask app but need to call it "application" for WSGI to work
from bot import app as application  # noqa  # update app.name bot.py


```

#### 问题

1. 在pythonanywhere无法安装telebot
2. 创建虚拟环境virtualenv
3. 在web选项有一个virutalenv配置。配置就好
4. 需要安装pyTelegramBotAPI

5. bot.py在pythonanywhere发布
    1. 本地更改代码后,push到github 
    2. 在pythonanywhere控制台,pull下来
    3. 在web page refresh.

6. 为了缩短发布步骤, 想直接在pythonanywhere建立一个git remote 然后代码直接push到pythonanywhere上面.自动发布. 查找后,确实有这种做法, 不过需要pythonanywhere的付费账户才可以用ssh功能. (git push 需要ssh认证)

### 其他
0. 把token的数据放在config.ini
1. config.ini要放在正确的地方. 
2. 在web page配置正确的路径即可.

 

## 在botFather添加命令
- start - 开始
- help - 获取帮助
- encode64 - base64编码
- decode64 - base64解码